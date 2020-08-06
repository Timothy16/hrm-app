<template>
    <div>
        <div class="fixed-top">
            <Navbar />
        </div>
        <div class="padding-down bg-cont">
        <div class="container pb-5">
                    <div class="jobs-title">Latest Jobs</div>
                     <div class="text-center">
                    <div class="lds-roller loader" v-if="loader">
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
                    <div class="card mt-3 box-style" v-for="getJob in getJobs.data" :key="getJob.id">
                        <div class="card-body" >
                            <div class="row ">
                                <div class="col-sm-4"> 
                                    <h2>{{getJob.company_name}}</h2>
                                     <div class="title">
                                        <span style="font-weight : bolder">Role</span> :  {{getJob.job_title}}
                                    </div>
                                    <p class="">
                                        <img src="/img/location.png" alt="" srcset=""> <span class="ml-1">{{getJob.company_address}}</span>
                                    </p>
                                </div>
                                <div class="col-sm-4">
                                    <div class="title">
                                       <span style="font-weight : bolder">Type</span> : {{getJob.job_type}}
                                    </div>
                                    <div class="">
                                    <span style="font-weight : bolder">Salary Range</span>  : {{getJob.salary_range}}
                                    <!-- <span style="font-weight : bolder">{{getJob.job_description}}</span>
                                     <span style="font-weight : bolder">{{getJob.job_requirement}}</span> -->
                                    </div>
                                </div>
                                <div class="col-sm-3 btn-down">
                                    <div class="btn btn-secondary"  data-toggle="modal" data-target="#exampleModal">
                                        <span class="nav-link" style="color: white">Details</span>
                                    </div>
                                    <div class="btn btn-primary btn-margin">
                                    <router-link to = "/Info" class="nav-link" style="color: white"> Apply </router-link>
                                    </div>
                            </div>
                        </div>
                    </div>

                    <!-- Modal Drop -->
                    <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
                        <div class="modal-dialog" role="document">
                            <div class="modal-content">
                            <div class="modal-header">
                                <h5 class="modal-title" id="exampleModalLabel"> <span style="font-weight : bolder">Job Title</span>  : {{getJob.job_title}}</h5>
                                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                                </button>
                            </div>
                            <div class="modal-body">
                                <h1>{{getJob.company_name}}</h1> <br>
                                    <h3>Job Title : <span style="font-size : 1.3rem">{{getJob.job_title}}</span> </h3> 
                                    <!-- <h3>Job Type : <span style="font-size : 1.3rem">{{getJob.job_type}}</span> </h3>  -->
                                    <p>Salary Range :  {{getJob.salary_range}}<p>
                                    <p><i class="fa fa-map-marker"></i>  {{getJob.company_address}}<p>
                                    <p><i class="fa fa-envelope"></i>  {{getJob.company_email}}<p> 
                                    <h3>Job Description</h3>
                                    <p>
                                        <ul>
                                            <li>
                                                {{getJob.job_description}} <br />
                                            </li>
                                        </ul>
                                    </p>
                                    <h3>Job Requirement</h3>
                                    <p>
                                        <ul>
                                            <li>
                                                {{getJob.job_requirement}} <br />
                                            </li>
                                        </ul>
                                    </p>
                            </div>
                            <div class="modal-footer">
                                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                            </div>
                            </div>
                        </div>
                    </div>
                    <!-- Modal End -->
                    
                </div>
                 <div class="mt-3 row justify-content-center">
                    <pagination :data="getJobs" @pagination-change-page="getResults">
                        <span slot="prev-nav">Previous</span>
                        <span slot="next-nav">Next</span>
                    </pagination>
                    </div>
                </div>
        </div>
      <div class="">
         <Footer />
           </div>
    </div>
</template>

<script>
import axios from 'axios'
import Footer from '@/components/Footer.vue'
import Navbar from "@/components/Navbar.vue"
import pagination  from 'laravel-vue-pagination'
export default {
 components : {
     Navbar,
     Footer,
     pagination
 },
 data(){
     return{
         getJobs:{},
         loader : true
     }
 },
 
 methods : {
     getallJobs(page = 1){
         axios.get('https://jobcaster.herokuapp.com/api/jobs?page=' + page)
          .then(res =>{
              this.loader = false
            this.getJobs = res.data;
             
          }).catch(error => {
            console.log(error);
          });
    }
 },
 created(){
     this.getallJobs()
 }

 
}
</script>

<style scoped>
.padding-down{
    padding-top: 10rem;
}
.bg-cont{
    background-color: #e5e5e5 !important;
}
.bg-new{
    background-image: linear-gradient( rgba(0, 0, 0, 1), rgba(0, 0, 0, 1)) !important;
    /* opacity: 0.88888; */
}
.btn-secondary{
    background: #9BB2BE !important;
    border-color: #9BB2BE !important;
}
.jobs-title{
    font-size: 1.5rem;
}
.title{
    /* margin-top: .1rem; */
    font-size: 1.5rem;
    /* line-height: 7px; */
}
.btn-margin{
    margin-left : .5rem !important;
}
.lds-roller {
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
ul li{
    margin: 0 2rem !important;
}
@media only screen and (max-width:578px){
    .btn-margin {
        margin-left: 0;
    }
}
</style>
