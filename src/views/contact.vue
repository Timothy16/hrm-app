<template>
    <div>
        <div class="fixed-top">
            <Navbar />
        </div>
        <div class="hero pb-5">
            <div class="container text-center">
                <div class="contact-header">
                    Contact
                </div>
                <div class="links">
                    <router-link to="/"> Home </router-link> <span style="color : #FFFFFF"> > Contact </span> 
                </div>
            </div>
        </div>
        <div class="caster">
        <div class="container pt-5 pb-5">
        <div class="row">
            <div class="col-sm-8">
                <div class="card shadow">
                    <div class="card-body">
                        <form @submit.prevent="sendMessage">
                            <label for="">Full Name</label> 
                            <input type="text" name="" class="form-control" id="" required placeholder="Full Name" v-model="contact.name"> <br>
                            <label for="">Email Adreess</label>
                            <input type="email" name="" class="form-control" id="" required placeholder="Email Address" v-model="contact.email"> <br>
                            <label for="">Message</label> <br>
                            <textarea name="" id="" class="form-control" required placeholder="Say Hello" v-model="contact.text"></textarea>
                            <button type="submit" class="btn btn-primary mt-4 btn-lg">Send</button> <br> <div class="lds-roller loader" v-if="loaderNew">
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
          </div>
                        </form>
                    </div>
                </div>
            </div>
            <div class="col-sm-4">
                <div class="card shadow mt-card">
                    <div class="card-body">
                        <h3>Contact Info</h3>
                        <h5 class="mt-3">Address</h5>
                        <p>102, Oron Road, Uyo Akwa Ibom State.</p>
                        <h5 class="mt-3">Phone</h5>
                        <p style="color : #0065FC">+234 810 4399 011</p>
                        <h5 class="mt-3">Email Address</h5>
                        <p style="color : #0065FC">jobcaster@gmail.com</p>
                    </div>
                </div>
                <div class="card mt-4">
                    <div class="card-body">
                        <h5>More info</h5>
                        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Exercitationem, nemo.
                            Lorem ipsum dolor sit amet consectetur adipisicing elit. Tempora, impedit!
                            Lorem.
                        </p>
                    </div>
                </div>
            </div>
        </div>
    </div>
    </div>
     <div style="background-color : #0065FC">
      <div class="container pb-5">
        <div class="subscribe">
          <h3 class="pt-5" style="color : #FFFFFF">Subscribe Newsletter</h3>
        </div>
        <form @submit.prevent="sendEmail">
          <div class="form-inline">
             <input type="email" class="form-control form-control-1 mb-2 mr-sm-2 mb-sm-0" id="" placeholder="Enter Your Email" required v-model="enterMail">
            <button type="submit" class="btn btn-secondary btn-send l-left">Send</button> <div class="lds-roller loader" v-if="loader">
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
                <div></div>
          </div>
          </div>
        </form>
      </div>
    </div>
       <div class="">
            <Footer />
        </div>
    </div>
</template>


<script>
import axios from 'axios'
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
export default {
    components : {
        Navbar,
        Footer
    },
    data(){
        return{
            loader : false,
            loaderNew : false,
             enterMail : "",
             contact : {
                 name : "",
                 email : "",
                 text : ""
             }
        }
    },
    methods : {
       sendMessage(){
      this.loaderNew = true
      const formData = new FormData();
      formData.append("name", this.contact.name);
      formData.append("email", this.contact.email);
      formData.append("text", this.contact.text);
      axios.post("https://jobcaster.herokuapp.com/api/contactus", formData)
        .then((res) => {
            this.loaderNew = false
          swal({
            title: "Thanks for Contacting Us!",
             text: "We will get back to you",
            icon: "success",
            button : false
          });
          console.log(res.data);
        })
        .catch((error) => {
          this.loader = false;
          console.log(error);
        });
      console.log(this.contact);
    },
      sendEmail(){
      this.loader = true
      const formData = new FormData();
      formData.append("email", this.enterMail);
      axios.post("https://jobcaster.herokuapp.com/api/applyjob", formData)
        .then((res) => {
            this.loader = false
          swal({
            title: "Thanks for Subscribing!",
             text: "We will keep you updated",
            icon: "success",
            button : false
          });
          console.log(res.data);
        })
        .catch((error) => {
          this.loader = false;
          console.log(error);
        });
      console.log(this.enterMail);
    }
    }
}
</script>

<style scoped>
.hero{
    background-image: linear-gradient(0deg, rgba(0, 0, 0, 0.9), rgba(0, 0, 0, 0.9)), url("/img/contact-us.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center center;
    height: auto;
    margin-top: 7rem;
}
.contact-header{
    padding-top: 2rem;
    color: #FFFFFF;
    font-size: 4rem;
}
a:hover{
    text-decoration: none;
    color: #FFFFFF;
}
.links{
    font-size: 1.3rem;
}
textarea{
    outline: blue !important;
    width: 100%;
    height: 200px;
    padding: .5rem;
    border: 1px solid #ced4da;
}
.btn-secondary{
  background-color: #081D29 !important;
  border: #081D29 !important;
}
.btn-send{
  padding: 1.1rem 5rem !important;
}
.l-left{
  margin-left: 2rem;
}
.form-control-1{
  padding: 1rem 1rem !important;
  width: 70% !important;
}
.caster{
  background-color: rgb(192,192,192, 0.1);
}.lds-roller {
  display: inline-block;
  position: relative;
  width: 80px;
  height: 80px;
}
.lds-roller div {
  animation: lds-roller 1.2s cubic-bezier(0.5, 0, 0.5, 1) infinite;
  transform-origin: 40px 40px;
}
.lds-roller div:after {
  content: " ";
  display: block;
  position: absolute;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: #000000;
  margin: -4px 0 0 -4px;
}
.lds-roller div:nth-child(1) {
  animation-delay: -0.036s;
}
.lds-roller div:nth-child(1):after {
  top: 63px;
  left: 63px;
}
.lds-roller div:nth-child(2) {
  animation-delay: -0.072s;
}
.lds-roller div:nth-child(2):after {
  top: 68px;
  left: 56px;
}
.lds-roller div:nth-child(3) {
  animation-delay: -0.108s;
}
.lds-roller div:nth-child(3):after {
  top: 71px;
  left: 48px;
}
.lds-roller div:nth-child(4) {
  animation-delay: -0.144s;
}
.lds-roller div:nth-child(4):after {
  top: 72px;
  left: 40px;
}
.lds-roller div:nth-child(5) {
  animation-delay: -0.18s;
}
.lds-roller div:nth-child(5):after {
  top: 71px;
  left: 32px;
}
.lds-roller div:nth-child(6) {
  animation-delay: -0.216s;
}
.lds-roller div:nth-child(6):after {
  top: 68px;
  left: 24px;
}
.lds-roller div:nth-child(7) {
  animation-delay: -0.252s;
}
.lds-roller div:nth-child(7):after {
  top: 63px;
  left: 17px;
}
.lds-roller div:nth-child(8) {
  animation-delay: -0.288s;
}
.lds-roller div:nth-child(8):after {
  top: 56px;
  left: 12px;
}
@keyframes lds-roller {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@media only screen and (min-width: 300px) and (max-width: 350px){
    .mt-card{
  margin-top: 1.5rem !important;
}
.btn-send{
      padding: 1.25rem 8rem !important;
  }
  .form-control-1{
      width: 100% !important;
  }
  .l-left{
      margin-left: 0;
  }
}
@media only screen and (min-width: 360px)  and (max-width: 578px){
    .mt-card{
  margin-top: 1.5rem !important;
}
.btn-send{
      padding: 1.25rem 9.2rem !important;
  }
  .form-control-1{
      width: 100% !important;
  }
  .l-left{
      margin-left: 0;
  }
}
@media only screen and (min-width: 768px)  and (max-width: 1024px){
    .l-left{
        margin-left: 0;
    }
}
</style>