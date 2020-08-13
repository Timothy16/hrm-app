<template>
    <div>
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
                                Login
                            </div>
                        <form @submit.prevent="loginUser">
                            <div class="form-margin mt-3">
                            <div class="form-group">
                                <label for="exampleInputEmail1">Email</label>
                                <input type="email" class="form-control" aria-describedby="emailHelp" placeholder="Enter email" required v-model="login.email">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputPassword1">Password</label>
                                <input type="password" class="form-control" placeholder="Password" required v-model="login.password">
                            </div>
                            </div>
                            
                            <div class="text-center">
                            <button type="submit" class="btn btn-new">Login</button>
                            </div>
                            </form>
                        </div>
                    </div>
                   
                </div>
            </div>
        </div>

        <!-- Mobile View -->
         <div class="container mobile-view">
            <div class="card-edit mt-2 card-background">
                <div class="col-bg pb-3 p-2">
                            <div class="logo-edit">
                                <img src="/img/logo.png" alt="" srcset=""> <br>
                             <span class="logo-edit-1">Jobcaster</span>
                            </div>
                       
                            <div class="signUp">
                                Login
                            </div>
                        <form @submit.prevent="loginUser">
                            <div class="form-margin mt-3">
                            <div class="form-group">
                                <label for="exampleInputEmail1">Email</label>
                                <input type="email" class="form-control" aria-describedby="emailHelp" required placeholder="Enter email">
                            </div>
                            <div class="form-group">
                                <label for="exampleInputPassword1">Password</label>
                                <input type="password" class="form-control" required placeholder="Password">
                            </div>
                            </div>
                            
                            <div class="text-center">
                            <button type="submit" class="btn btn-new">Login</button>
                            </div>
                            </form>
                    </div>
                   
                </div>
            </div>
        <!-- Mobile View End -->
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
            login : {
                email : "",
                password : ""
            }
        }
    },
    methods : {
        loginUser(){
             const formData = new FormData();
            formData.append("email", this.login.email);
            formData.append("password", this.login.password);
            axios.post("https://jobcaster.herokuapp.com/api/login", formData, {
          headers: { "Content-Type": "multipart/form-data" }
        })
                .then((res) => {  
                swal({
                    title: "Success!",
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
    margin-top: 10rem;
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
    background: #0065FC;
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
@media only screen and (max-width : 578px){
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
.card-edit{
    background: #E5E5E5;
    background-image: url("/img/bg3.png"), url("/img/bg4.png");
    background-position: right top, left bottom;
    background-repeat: no-repeat, no-repeat;
    margin-top: 5rem !important;
    /* padding-bottom: 2rem !important; */
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
.logo-edit{
    margin-top: 2rem;
}
}
@media only screen and (min-width : 768px) and (max-width: 1024px){
    .form-margin{
    margin: 0;
    padding: 1rem;
}
}
</style>