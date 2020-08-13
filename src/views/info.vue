<template>
  <div>
    <div class="card-background">
         <div class="card-bg">
      <div class="container">
       
          <!-- Personal Info Start -->
          <div class="card-body">
            <form @submit.prevent="submitBtn()">
              <div class="signUp padding-down">personal information</div>
              <div class="form-margin mt-3">
                <div class="form-group">
                  <label for="inputAddress">full name (surname first)</label>
                  <input
                    type="text"
                    class="form-control"
                    id
                    placeholder
                    required
                    v-model="info.name"
                  />
                </div>
                <div class="form-row">
                  <div class="form-group col-md-6">
                    <label for="inputCity">nationality</label>
                    <input type="text" class="form-control" id required v-model="info.nationality" />
                  </div>
                  <div class="form-group col-md-6">
                    <label for="inputZip">state of origin</label>
                    <input type="text" class="form-control" id required v-model="info.state" />
                  </div>
                </div>
                <div class="form-row">
                  <div class="form-group col-md-6">
                    <label for="inputCity">Contact Address</label>
                    <input type="text" class="form-control" id required v-model="info.address" />
                  </div>
                  <div class="form-group col-md-6">
                    <label for="inputZip">Phone number</label>
                    <input type="text" class="form-control" id required v-model="info.phone" />
                  </div>
                </div>
                <div class="form-group">
                  <label for="inputAddress">email address</label>
                  <input
                    type="text"
                    class="form-control"
                    id
                    placeholder
                    required
                    v-model="info.email"
                  />
                </div>
                <div class="form-row">
                  <div class="form-group col-md-6">
                    <label for="inputCity">Date of birth</label>
                    <input type="date" class="form-control" id required v-model="info.dob" />
                  </div>
                  <div class="form-group col-md-6">
                    <label for="inputCity">Gender</label>
                    <br />
                    <select
                      class="custom-select increase_height-1"
                      name
                      required
                      v-model="info.gender"
                    >
                      <option value selected disabled>Gender</option>
                      <option value="Male">Male</option>
                      <option value="Female">Female</option>
                    </select>
                  </div>
                </div>
                <div class="form-row">
                  <div class="form-group col-md-6">
                    <label for="inputCity">Qualification</label>
                    <br />
                    <select
                      class="custom-select increase_height"
                      name
                      required
                      v-model="info.qualification"
                    >
                      <option value selected disabled>Select Degree</option>
                      <option value="OND">OND</option>
                      <option value="HND">HND</option>
                      <option value="Bsc">Bsc</option>
                      <option value="Masters">Masters</option>
                    </select>
                  </div>
                  <div class="form-group col-md-6">
                    <label for="inputZip">Years of Experience</label>
                    <input type="text" class="form-control" id required v-model="info.experience" />
                  </div>
                </div>
                <div>
                  <label for>About you</label>
                  <br />
                  <textarea name id class="p-2 form-control" required v-model="info.about_you"></textarea>
                </div>
              </div>

              <!-- Personal Info End -->
              <!-- Resume Start-->

              <div class="signUp mt-5">
                ADD A RESUME/CV
                <p
                  class="cv-text"
                >Add your resume to our database let our thousand employers find you</p>
              </div>
              <div class="container">
                <div class="border text-center">
                  <!-- <span><img src="img/upload.png" alt="" srcset=""></span> -->
                  <br />
                  <span>
                    <input
                      type="file"
                      name
                      id
                      accept=".pdf,.docx"
                      class=".form-control-file img-fluid"
                      @change="uploadCv()"
                      required
                    />
                  </span>
                  <!-- <div class="custom-file">
                                <input type="file" class="custom-file-input" id="customFile"  @change="uploadCv()" required>
                                <label class="custom-file-label" for="customFile">Choose file</label>
                  </div>-->
                </div>
                <div class="doc-text text-center mt-2">(.DOCX, .PDF)</div>
              </div>

              <!-- Resume End -->

              <div class="mt-5 text-center">
                <button type="submit" class="btn btn-submit">Submit</button>
              </div>
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
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import swal from "sweetalert";
import Navbar from "@/components/Navbar.vue";
export default {
  components: {
    Navbar
  },
  data() {
    return {
      getJobs : [],  
      loader: false,
      info: {
        name: "",
        phone: "",
        email: "",
        address: "",
        nationality: "",
        state: "",
        dob: "",
        gender: "",
        about_you: "",
        cv: {},
        qualification: "",
        experience: ""
      }
    };
  },
  methods: {
    uploadCv() {
      var input = event.target;
      this.info.cv = input.files[0];
      console.log(this.info.cv);
    },
    submitBtn() {
      this.loader = true;
      const formData = new FormData();
      formData.append("name", this.info.name);
      formData.append("phone", this.info.phone);
      formData.append("email", this.info.email);
      formData.append("address", this.info.address);
      formData.append("nationality", this.info.nationality);
      formData.append("state", this.info.state);
      formData.append("dob", this.info.dob);
      formData.append("gender", this.info.gender);
      formData.append("about_you", this.info.about_you);
      formData.append("cv", this.info.cv);
      formData.append("qualification", this.info.qualification);
      formData.append("experience", this.info.experience);
      formData.append("post_id", 1);
      formData.append("manager_id", 1);
      axios
        .post("https://jobcaster.herokuapp.com/api/applyjob", formData, {
          headers: { "Content-Type": "multipart/form-data" }
        })
        .then((res) => {
          this.loader = false;
          swal({
            title: "Good Job!",
            text: "Application Submitted Successfully!",
            icon: "success",
            button : false
          });
          console.log(res.data);
        })
        .catch((error) => {
          this.loader = false;
          console.log(error);
        });
      console.log(this.info);
    },
  }
};
</script>

<style scoped>
.bg-new {
  background-image: linear-gradient(
    rgba(0, 0, 0, 1),
    rgba(0, 0, 0, 1)
  ) !important;
  /* opacity: 0.88888; */
}
.padding-down {
  margin-top: 1rem;
}
.signUp {
  font-style: normal;
  font-weight: bold;
  font-size: 2rem;
  /* line-height: 52px; */
  text-align: center;
  color: #0065fc;
  text-transform: uppercase;
}
.cv-text {
  font-size: 1rem;
}
label {
  font-style: normal !important;
  font-weight: normal !important;
  font-size: 0.8rem !important;
  color: #0065fc !important;
  text-transform: uppercase !important;
}
.form-control {
  width: 100% !important;
  padding: 1rem 2rem;
}
.form-margin {
  margin: 0 10rem;
}
.card-background {
  background-image: url("/img/bg3.png"), url("/img/bg4.png");
  background-position: right top, left bottom;
  background-repeat: no-repeat, no-repeat;
  padding-bottom: 2rem !important;
}
.card-bg{
  /* background: #e5e5e5; */
  margin-top: 5.5rem;
}
.border {
  border: 2px dashed #0065fc !important;
  height: 10vh;
}
.doc-text {
  font-style: normal;
  font-weight: normal;
  font-size: 1.3rem;
  line-height: 24px;
  text-align: center;
  color: #081d29;
}
.btn-submit {
  background: #0065fc;
  /* border: 2px solid #0065FC; */
  box-sizing: border-box;
  filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
  border-radius: 5px;
  color: #ffffff;
  padding: 1.3rem 5rem !important;
  margin-left: 0.5rem;
}
.active {
  display: block !important;
}
#card-display {
  display: none;
}
.card-body {
  transition: 0.5s;
}
.card-margin {
  margin-top: 3rem;
}
.increase_height {
  height: calc(2.8em + 0.75rem + 2px) !important;
  width: 100% !important;
  /* padding: .375rem 17rem .375rem .75rem !important; */
}
.increase_height-1 {
  height: calc(2.8em + 0.75rem + 2px) !important;
  width: 100% !important;
  /* padding: .375rem 20rem .375rem .75rem !important; */
}
textarea {
  outline: none;
  border: 1px solid rgb(192, 192, 192, 1);
  width: 100%;
  height: 150px;
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
.loader{
  width: 100%;
  height: 183vh;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #e5e5e5;
  background-size: contain;
  opacity: 0.8;
}

@media only screen and (max-width: 578px) {
  .loader{
  width: 100%;
  height: 310vh;
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #e5e5e5;
  background-size: contain;
  opacity: 0.8;
}
  .form-margin {
    margin: 0 0;
  }
  .card-margin {
    margin-top: 0;
  }
  .btn-prev {
    background: #e5e5e5;
    border: 2px solid #0065fc;
    box-sizing: border-box;
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
    border-radius: 5px;
    color: #0065fc;
    padding: 1rem 0.5rem !important;
  }
  .btn-cont {
    background: #9bb2be;
    /* border: 2px solid #0065FC; */
    box-sizing: border-box;
    filter: drop-shadow(0px 4px 4px rgba(0, 0, 0, 0.25));
    border-radius: 5px;
    color: #ffffff;
    padding: 1rem 0.5rem !important;
    margin-left: 0.5rem;
  }
  .border {
    border: 2px dashed #0065fc !important;
    height: auto;
    padding: 1rem;
    padding-bottom: 2rem;
  }
  input[type="file"] {
    padding: 0.1rem 1rem 0 0;
  }
  .increase_height {
    height: calc(2.8em + 0.75rem + 2px) !important;
    /* padding: .375rem 5rem .375rem .75rem !important; */
  }
  .increase_height-1 {
    height: calc(2.8em + 0.75rem + 2px) !important;
    /* padding: .375rem 8rem .375rem .75rem !important; */
  }
}
@media only screen and (max-width : 768px){
  .form-margin{
    margin: 0 0;
  }
}
</style>


