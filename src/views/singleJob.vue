<template>
    <div>
        <div class="container card-down">
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
        <div class="card card-edit-1 shadow-lg p-3 mb-5 bg-white rounded" v-for="getJob in getJobs[0]" :key="getJob.id">
        <div class="card-body">
            <!-- loader -->
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
            <!-- loader -->
            <div>
                <div class="text-center">
                    <h1>{{getJob.company_name}}</h1>
                    <h4>{{getJob.job_title}}</h4> 
                    <h5> <span style="font-size : 1rem"  :class="`shadow rounded-lg
                                 ${(getJob.job_type=='Full-Time') ? ' bg-info text-white': '' }
                                 ${(getJob.job_type=='Freelance') ? ' bg-danger text-white': '' }
                                 ${(getJob.job_type=='Part-Time') ? ' bg-warning text-dark  ': '' }
                                 ${(getJob.job_type=='Remote') ? ' bg-success text-white': '' } 
                                 badge py-1 `">{{getJob.job_type}} </span></h5> 
                    <h5>Salary Range :  {{getJob.salary_range}}</h5>
                    <div class="d-flex row justify-content-center">
                            <div>
                                <i class="fa fa-map-marker"></i>  {{getJob.company_address}}
                            </div>
                            <div class="ml-3">
                                <i class="fa fa-envelope"></i>  {{getJob.company_email}}
                            </div>
                </div>
                </div>
            
           
            <hr style="background-color : #000000">
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
             <div class="">
              <router-link to="/info">
               <div class="btn btn-primary btn-edit btn-lg">
              Apply
            </div>
              </router-link>
            </div>
            </div>
           
        </div>
      </div>
        </div>        
    </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";
import axios from 'axios'
export default {
    components : {
        Navbar,
        Footer,
    },
    data(){
        return{
            getJobs : {},
            loader : true
        }
    },
    methods :{
         singleJob() {
			axios.get(`https://jobcaster.herokuapp.com/api/selectedjob/${this.$route.params.name}`)
		    .then(res => {
            this.getJobs = res.data;
            this.loader = false
            console.log(this.getJobs)
        })
        .catch((error) => {
          this.loader = false;
          console.log(error);
        });
    },
},
created(){
        this.singleJob()
    }
}
</script>

<style scoped>
.card-down{
    margin-top : 10rem !important;
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
.btn-edit{
    padding: 1rem 3rem !important;
}
.card-edit-1{
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19) !important;
}
</style>