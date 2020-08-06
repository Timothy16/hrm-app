<template>
    <div>
        <div class="fixed-top">
        <Navbar />
      </div>

        <!-- Big Screen -->
        <div class="container desktop-view">
            <div class="card-edit mt-5 card-background">
                <div class="">
                    <div class="row">
                        <div class="col-sm-6 col-bg">
                            <div class="logo-edit">
                                <img src="/img/logo.png" alt="" srcset=""> <br>
                             <span class="logo-edit-1">Jobcaster</span>
                            </div>
                            
                        </div>
                        <div class="col-sm-6 pb-5">
                            <div class="signUp">
                                signup
                            </div>
                        <form @submit.prevent="registerUser">
                            <div class="form-margin mt-3">
                                 <div class="form-group">
                                <label for="exampleInputEmail1">Username</label>
                                <input type="text" class="form-control" aria-describedby="emailHelp" placeholder="Enter Username" required v-model="register.name">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputEmail1">Email</label>
                                <input type="email" class="form-control" aria-describedby="emailHelp" placeholder="Enter email" required v-model="register.email">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputPassword1">Password</label>
                                <input type="password" class="form-control" placeholder="Password" required v-model="register.password">
                            </div>
                            </div>
                            
                            <div class="text-center">
                            <button type="submit" class="btn btn-new">CREATE ACCOUNT</button>
                            <p class="social-account">or sign up with social account</p>
                            <button type="submit" class="btn btn-social"><i class="fa fa-facebook"></i> <span class="ml-2">facebook</span></button>
                            <button type="submit" class="btn btn-social-1 mt-4"><i class="fa fa-google"></i> <span class="ml-2">google</span></button>
                            </div>
                            
                            </form>

                            <h4 class="existing-user">Existing user? <router-link to="/Login"> Login</router-link></h4>

                        </div>
                    </div>
                   
                </div>
            </div>
        </div>
        <!-- Big Screen ENd -->

        <!-- Small Screen -->
          <div class="container mobile-view">
            <div class="col-bg-1 mt-5">
                <div class="p-3">
                             <div class="logo-edit">
                                <img src="/img/logo.png" alt="" srcset=""> <br>
                             <span class="logo-edit-1">Jobcaster</span>
                            </div>
                            <div class="signUp">
                                signup
                            </div>
                        <form @submit.prevent="registerUser">
                            <div class="form-margin mt-3">
                                 <div class="form-group">
                                <label for="exampleInputEmail1">Username</label>
                                <input type="text" class="form-control" aria-describedby="emailHelp" placeholder="Enter Username" required v-model="register.name">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputEmail1">Email</label>
                                <input type="email" class="form-control" aria-describedby="emailHelp" placeholder="Enter email" required v-model="register.email">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputPassword1">Password</label>
                                <input type="password" class="form-control" placeholder="Password" required v-model="register.password">
                            </div>
                            </div>
                            <div class="text-center">
                            <button type="submit" class="btn btn-new">CREATE ACCOUNT</button>
                            <p class="social-account">or sign up with social account</p>
                            
                            <button type="submit" class="btn btn-social"><i class="fa fa-facebook"></i> <span class="ml-2">facebook</span></button> <br>
                            <button type="submit" class="btn btn-social-1 mt-4"><i class="fa fa-google"></i> <span class="ml-2">google</span></button>
                            </div>
                            
                            </form>

                            <h4 class="existing-user">Existing user? <router-link to="/Login"> Login</router-link></h4>
                    </div>
                   
                </div>
            </div>
     <!-- Small Scren End -->
      <div class="mt-5">
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
            register : {
                name : "",
                email : "",
                password : ""
            }
        }
    },
    methods : {
        registerUser(){
        
            const formData = new FormData();
            formData.append("name", this.register.name);
            formData.append("email", this.register.email);
            formData.append("password", this.register.password);
            axios.post("https://jobcaster.herokuapp.com/api/register", formData, {
          headers: { "Content-Type": "multipart/form-data" }
        })
                .then((res) => {  
                swal({
                    title: "Account Successfully Created!",
                    text: "Thanks for choosing us",
                    icon: "success",
                    button : false
                });
                window.location.href = "http://localhost:8080/Dashboard"
                console.log(res.data);
                })
                .catch((error) => {
                console.log(error);
                });
           
        }
    }
    
}
</script>>
<style scoped>
.logo-edit{
    text-align: center;
    margin-top: 20rem;
}
.logo-edit-1{
    font-size: 2rem;
    color: #FFFFFF;
}
.signUp{
    font-style: normal;
    font-weight: bold;
    font-size: 2rem;
    margin-top: 5rem;
    text-align: center;
    color: #0065FC;
    text-transform: uppercase;
}
.existing-user{
    text-align: center;
    margin-top: 1rem;
}
.form-control{
    width: 100% !important;
    padding: 1rem 2rem;
}
.form-margin{
    margin: 0 7rem;
}
label{
    font-style: normal !important;
    font-weight: normal!important;
    font-size: 1rem !important;
    color: #0065FC !important;
    text-transform: uppercase !important;
}
.btn-new{
    background: #9BB2BE;
    border-radius: 5px;
    color: #FFFFFF;
    padding: 1.3rem 5.6rem !important;
}
.col-bg{
    background-image: linear-gradient(0deg, rgba(8, 29, 41, 0.7), rgba(8, 29, 41, 0.7)), url("/img/signUp.png");
    background-position: center center 100%;
    object-fit: cover;
    background-repeat: no-repeat;
}
.col-bg-1{
    background-image: linear-gradient(0deg, rgba(8, 29, 41, 0.7), rgba(8, 29, 41, 0.7)), url("/img/signUp.png");
    background-position: 100% 100%;
    background-size: cover;
    background-repeat: no-repeat;
}
.social-account{
    margin-top: 1rem;
    font-style: normal;
    font-weight: normal;
    font-size: 1rem;
    line-height: 24px;
    text-align: center;
    color: #0065FC;
    text-transform: uppercase;
}
.btn-social{
    background: #3B5998;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
   color: #FFFFFF;
   text-transform: uppercase;
    padding: 1.3rem 7rem !important;
}
.btn-social-1{
    background: #DB4437;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
    color: #FFFFFF;
    text-transform: uppercase;
    padding: 1.3rem 7.5rem !important;
}
.card-edit{
    background: #E5E5E5;
    background-image: url("/img/bg3.png"), url("/img/bg4.png");
    background-position: right top, left bottom;
    background-repeat: no-repeat, no-repeat;
    margin-top: 8rem !important;
    /* padding-bottom: 2rem !important; */
}
.mobile-view{
    display: none;
}
@media only screen and (min-width: 300px) and (max-width: 350px){
     .form-margin{
    margin: 0;
}
.logo-edit{
    text-align: center;
    margin-top: 7rem;
}
.desktop-view{
    display: none !important;
}
label{
    font-style: normal !important;
    font-weight: normal!important;
    font-size: 1rem !important;
    color: #FFFFFF !important;
    text-transform: uppercase !important;
}
.mobile-view{
    display: block !important;
}
.social-account{
    margin-top: 1rem;
    font-style: normal;
    font-weight: normal;
    font-size: 1rem;
    line-height: 24px;
    text-align: center;
    color: #FFFFFF;
    text-transform: uppercase;
}
.existing-user{
    color: #FFFFFF;
}
.signUp{
    font-style: normal;
    font-weight: bold;
    font-size: 2rem;
    margin-top: 2rem;
    text-align: center;
    color: #FFFFFF;
    text-transform: uppercase;
}
.btn-new{
    padding: 1.3rem 3rem !important;
}
.btn-social{
    background: #3B5998;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
   color: #FFFFFF;
   text-transform: uppercase;
    padding: 1.3rem 4rem !important;
}
.btn-social-1{
    background: #DB4437;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
    color: #FFFFFF;
    text-transform: uppercase;
    padding: 1.3rem 4.5rem !important;
}
.logo-edit{
    margin-top: 5rem;
}
}
@media only screen and (min-width : 360px) and (max-width : 578px){
    .form-margin{
    margin: 0;
}
.logo-edit{
    text-align: center;
    margin-top: 7rem;
}
.desktop-view{
    display: none !important;
}
label{
    font-style: normal !important;
    font-weight: normal!important;
    font-size: 1rem !important;
    color: #FFFFFF !important;
    text-transform: uppercase !important;
}
.mobile-view{
    display: block !important;
}
.social-account{
    margin-top: 1rem;
    font-style: normal;
    font-weight: normal;
    font-size: 1rem;
    line-height: 24px;
    text-align: center;
    color: #FFFFFF;
    text-transform: uppercase;
}
.existing-user{
    color: #FFFFFF;
}
.signUp{
    font-style: normal;
    font-weight: bold;
    font-size: 2rem;
    margin-top: 2rem;
    text-align: center;
    color: #FFFFFF;
    text-transform: uppercase;
}
.btn-new{
    padding: 1.3rem 5rem !important;
}
.btn-social{
    background: #3B5998;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
   color: #FFFFFF;
   text-transform: uppercase;
    padding: 1.3rem 6rem !important;
}
.btn-social-1{
    background: #DB4437;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 5px;
    color: #FFFFFF;
    text-transform: uppercase;
    padding: 1.3rem 6.5rem !important;
}
.logo-edit{
    margin-top: 5rem;
}
}
@media only screen and (min-width : 768px) and (max-width: 1024px){
    .form-margin{
    margin: 0;
    padding: 1rem;
}
}
</style>