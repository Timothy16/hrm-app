<template>
  <div>
    <div class="hero">
      <div class="container">
        <div class="welcome-text">
          Get <span style="color : #0065FC">Hired.</span>
        </div>
        <div class="welcome-text-small">Build your <span style="color : #0065FC">Career</span> with us. <br> Apply Now!</div>
      </div>
    </div>
    <!-- Recent Jobs -->
    <div class="recentJob pb-5">
      <div class="container">
        <div class="d-flex pad-down mb-5">
          <h3>Recent Jobs</h3>
        </div>

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

        <!-- loader end -->

        <div class="card mt-2 card-edit-1" v-for="getJob in getJobs.data" :key="getJob.id">
          <div class="card-body">
            <div class="row">
              <div class="col-sm-6">
                <h3>
                  {{getJob.job_title}}
                  <span style="font-size : 1rem"  :class="`shadow rounded-lg
                                 ${(getJob.job_type=='Full-Time') ? ' bg-info text-white': '' }
                                 ${(getJob.job_type=='Freelance') ? ' bg-danger text-white': '' }
                                 ${(getJob.job_type=='Part-Time') ? ' bg-warning text-dark  ': '' }
                                 ${(getJob.job_type=='Remote') ? ' bg-success text-white': '' } 
                                 badge py-1 `">{{getJob.job_type}} </span>
                </h3>
                <div class="d-flex">
                  <div>
                    <i class="fa fa-briefcase"></i>
                    <span class="" style="color : #64A2FF; font-size : 1.3rem">{{getJob.company_name}}</span>
                  </div>
                  <div class="ml-3">
                    <i class="fa fa-map-marker"></i>
                   <span class="ml-2" style="font-size : 1.3rem">{{getJob.company_address}}</span> 
                  </div>
                </div>
              </div>
              <div class="col-sm-6">
                <div class="floatRight">
                  <router-link :to="`/singleJob/${getJob.id}`">
                    <div class="btn btn-primary btn-lg">Details</div>
                  </router-link>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="mt-3 row justify-content-center">
          <pagination :data="getJobs" @pagination-change-page="getResults">
            <span slot="prev-nav">Previous</span>
            <span slot="next-nav">Next</span>
          </pagination>
        </div>
      </div>
    </div>

    <!-- Recent Jobs End -->

    <!-- why job caster -->
    <div class="caster">
      <div class="container pb-5" data-aos="fade-up" data-aos-duration="1000" data-aos-anchor-placement="center-bottom">
        <div class="caster-title">
         What we offer you
        </div>
        <div class="row mt-5">
          <div class="col-sm-4">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                  <i class="fa fa-lightbulb-o"></i>
                </div>
                <h4>A Career, not a Job</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
          <div class="col-sm-4 mt-card">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                 <i class="fa fa-bullseye" aria-hidden="true"></i>
                </div>
                <h4>Unleash your potential</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
          <div class="col-sm-4 mt-card">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                  <i class="fa fa-plane"></i>
                </div>
                <h4>Be part of something great</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
        </div>
        <div class="row mt-5">
          <div class="col-sm-4">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                  <i class="fa fa-desktop"></i>
                </div>
                <h4>Professional Learning</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
          <div class="col-sm-4 mt-card">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                  <i class="fa fa-globe" aria-hidden="true"></i>
                </div>
                <h4>Global resources</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
          <div class="col-sm-4 mt-card">
            <div class="card card-color">
              <div class="card-body text-center">
                <div class="icon">
                  <i class="fa fa-trophy" aria-hidden="true"></i>
                </div>
                <h4>Realize your full potential</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsa, voluptatum!</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <!-- why job caster end -->
    <!-- owl carosel -->
    <div class="mb-5">
      <div class="container mt-5 pt-5">
        <h3 class="text-center">Meet our Team</h3>

        <div class="slider mt-5 mb-5 pb-5 shadow text-center">
          <div class="owl-carousel owl-theme">
            <div>
              <div class="text-center ml-auto mr-auto mt-5" style="width : 10%; height : 20%">
                <img src="img/person_1.jpg" alt srcset style="border-radius : 50%" />
              </div>
              <h3 class="mt-3">
                Even Leobanno
                <br />
                <p style="color : #0065FC">HR Manager</p>
              </h3>
              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus, beatae!</p>
            </div>
            <div>
              <div class="text-center ml-auto mr-auto mt-5" style="width : 10%; height : 20%">
                <img src="img/user-5.jpg" alt srcset style="border-radius : 50%" />
              </div>
              <h3 class="mt-3">
                Caltalan Dee
                <br />
                <p style="color : #0065FC">Lead Software Engineer</p>
              </h3>
              <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Qui, eius?</p>
            </div>
            <div>
              <div class="text-center ml-auto mr-auto mt-5" style="width : 10%; height : 20%">
                <img src="img/user-9.jpg" alt srcset style="border-radius : 50%" />
              </div>
              <h3 class="mt-3">
                Even Leobanno
                <br />
                <p style="color : #0065FC">Lead Product Designer</p>
              </h3>
              <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus, beatae!</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- owl carousle end -->

    <!-- news letter -->
    <div style="background-color : #0065FC">
      <div class="container pb-5">
        <div class="subscribe">
          <h3 class="pt-5" style="color : #FFFFFF">Subscribe Newsletter</h3>
        </div>
        <form @submit.prevent="sendEmail">
          <div class="form-inline">
            <input
              type="email"
              class="form-control form-control-1 mb-2 mr-sm-2 mb-sm-0"
              id
              placeholder="Enter Your Email"
              required
              v-model="enterMail"
            />
            <button type="submit" class="btn btn-secondary btn-send l-left">Send</button>
            <div class="lds-roller loader" v-if="loaders">
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
    <!-- news letter end -->

    <!-- footer -->
    

    <!-- footer end -->
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import Footer from "@/components/Footer.vue";
import pagination from "laravel-vue-pagination";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Navbar,
    pagination,
    Footer,
  },
  data() {
    return {
      getJobs: {},
      enterMail: "",
      loader: true,
      loaders: false,
    };
  },
  methods: {
    getResults(page = 1) {
      axios
        .get("https://jobcaster.herokuapp.com/api/jobs?page=" + page)
        .then((response) => {
          this.getJobs = response.data;
          this.loader = false;
        });
    },
    sendEmail() {
      this.loaders = true
      const formData = new FormData();
      formData.append("email", this.enterMail);
      axios
        .post("https://jobcaster.herokuapp.com/api/applyjob", formData)
        .then((res) => {
          this.loaders = false
          swal({
            title: "Thanks for Subscribing!",
            text: "We will keep you updated",
            icon: "success",
            button: false,
          });
          console.log(res.data);
        })
        .catch((error) => {
          this.loader = false;
          console.log(error);
        });
      console.log(this.enterMail);
    },
  },
  created() {
    this.getResults();
  },
};
</script>

<style scoped>
.nav-color {
  background-color: #ffffff;
}
.hero {
  background-image: linear-gradient(
      0deg,
      rgba(0, 0, 0, 0.5),
      rgba(0, 0, 0, 0.5)
    ),
    url("/img/hero.png");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  width: 100%;
  height: auto;
  padding-bottom: 5rem;
}
.pad-down {
  padding-top: 8rem !important;
}
.form-control {
  /* border: none !important; */
  border-radius: none !important;
}
.floatRight {
  float: right;
}
.welcome-text {
  font-style: normal;
  font-weight: bold;
  font-size: 5rem;
  padding-top: 15rem;
  color: #ffffff;
}
.welcome-text-small {
  font-style: normal;
  font-weight: normal;
  font-size: 2.5rem;
  color: #ffffff;
}
.form-inline {
  align-items: flex-start !important;
}
.form-control {
  padding: 1rem 1rem !important;
  /* border-radius: 0 !important; */
}
.form-control-1 {
  padding: 1rem 1rem !important;
  width: 70% !important;
  /* border-radius: 0 !important; */
}
.increase_height {
  height: calc(2.8em + 0.75rem + 2px) !important;
  /* width: 100% !important; */
  padding: 0.375rem 6rem 0.375rem 0.75rem !important;
}
.btn-edit {
  padding: 1rem 4rem !important;
}
.btn-edit-1 {
  padding: 1rem 2rem !important;
  /* border-radius: 0 !important; */
}
.btn-send {
  padding: 1.1rem 5rem !important;
}
.btn-primary {
  background-color: #0065fc !important;
}
.btn-secondary {
  background-color: #081d29 !important;
  border: #081d29 !important;
}
.btn-text {
  font-style: normal;
  font-weight: bold;
  font-size: 1.5rem;
  text-align: center;
  color: #ffffff;
}
.form-margin {
  margin-left: 2rem;
}
.l-left {
  margin-left: 2rem;
}
.card-edit {
  width: 90% !important;
}
.card-edit-1 {
  transition: transform 0.2s !important;
  background-color: rgb(255, 255, 255, 0.7) !important;
}
.card-edit-1:hover {
  transform: scale(1.01) !important;
  background-color: #ffffff !important;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19) !important;
}
.recentJob {
  background-color: rgb(192, 192, 192, 0.3);
}
.caster {
  background-color: rgb(192, 192, 192, 0.1);
  opacity: 0.8;
}
.caster-title {
  text-align: center;
  font-size: 2rem;
  padding-top: 5rem;
  color: #0065fc;
}
.icon {
  font-size: 3rem;
}
.card-color {
  background-color: rgb(192, 192, 192, 0.2) !important;
  transition: transform 0.2s !important;
}
.card-color:hover {
  background-color: #ffffff !important;
  transform: scale(1.1) !important;
  border: 3px solid #64a2ff !important;
}
.slider {
  border: 1px solid #ffffff;
  background-color: #e5e5e5;
}
ul li {
  list-style-type: none;
  color: rgb(192, 192, 192, 0.8);
  cursor: pointer;
  margin-top: 1rem;
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
@media only screen and (min-width: 300px) and (max-width: 350px) {
  .btn-edit {
    padding: 1.25rem 6.1rem !important;
  }
  .welcome-text {
    padding-top: 10rem;
    font-size: 2rem;
  }
  .card-edit {
    width: 100% !important;
  }
  .floatRight {
    float: left !important;
  }
  .form-margin {
    margin-left: 0;
  }
  .l-down {
    margin-top: 0.5rem;
  }
  .l-left {
    margin-left: 0 !important;
  }
  .welcome-text-small {
    font-size: 1.5rem;
    font-size: 1rem;
  }

  .increase_height {
    height: calc(2.8em + 0.75rem + 2px) !important;
    width: 100% !important;
    padding: 0.375rem 6rem 0.375rem 0.75rem !important;
  }
  .mt-card {
    margin-top: 1.5rem !important;
  }
  .btn-send {
    padding: 1.25rem 8rem !important;
  }
  .form-control-1 {
    width: 100% !important;
  }
}
@media only screen and (min-width: 360px) and (max-width: 578px) {
  .welcome-text {
    padding-top: 10rem;
    font-size: 2.5rem;
  }
  .card-edit {
    width: 100% !important;
  }
  .floatRight {
    float: left !important;
  }
  .mt-card {
    margin-top: 1.5rem !important;
  }
  .form-margin {
    margin-left: 0;
  }
  .l-down {
    margin-top: 0.5rem;
  }
  .l-left {
    margin-left: 0 !important;
  }
  .welcome-text-small {
    font-size: 1.5rem;
    font-size: 2rem;
  }
  .btn-edit {
    padding: 1.25rem 7.3rem !important;
  }
  .btn-send {
    padding: 1.25rem 9.1rem !important;
  }
  .form-control-1 {
    width: 100% !important;
  }
  .increase_height {
    height: calc(2.8em + 0.75rem + 2px) !important;
    width: 100% !important;
    padding: 0.375rem 6rem 0.375rem 0.75rem !important;
  }
  .hero {
    background-image: linear-gradient(
        0deg,
        rgba(0, 0, 0, 0.5),
        rgba(0, 0, 0, 0.5)
      ),
      url("/img/hero.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: auto;
  }
}
@media only screen and (min-width: 768px) and (max-width: 1024px) {
  .welcome-text {
    font-style: normal;
    font-weight: bold;
    font-size: 5rem;
    padding-top: 8rem;
    color: #ffffff;
}
  .card-edit {
    width: 100% !important;
  }
  .btn-edit {
    padding: 1rem 4.9rem !important;
  }
  .increase_height {
    height: calc(2.8em + 0.75rem + 2px) !important;
  }
  .form-margin {
    margin-left: 1rem;
  }
  .l-left {
    margin-left: 0;
    /* margin-top: .5rem; */
  }
  .hero {
    background-image: linear-gradient(
        0deg,
        rgba(0, 0, 0, 0.5),
        rgba(0, 0, 0, 0.5)
      ),
      url("/img/hero.png");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: auto;
    padding-bottom: 2rem;
    padding-bottom: 3rem;
  }
}
</style>
