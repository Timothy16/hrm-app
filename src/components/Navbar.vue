<template>
  <div>
    <div class="shadow-nav nav-color desktopView">
      <div class="container">
        <nav class="navbar sticky-top navbar-expand-lg navbar-light">
          <router-link to="/" class="navbar-brand">
            <span class="text-secondary">Tek</span>
            <span class="text-primary" style="font-weight : bolder">Real</span>
          </router-link>
          <button
            class="navbar-toggler"
            type="button"
            data-toggle="collapse"
            data-target="#navbarSupportedContent"
            aria-controls="navbarSupportedContent"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav ml-auto">
              <li class="nav-item active">
                <router-link to="/" class="nav-link">
                  Home
                  <span class="sr-only">(current)</span>
                </router-link>
              </li>
              <li class="nav-item">
                <router-link to="/jobs" class="nav-link">jobs</router-link>
              </li>
              <li class="nav-item">
                <router-link to="/contact" class="nav-link">contact</router-link>
              </li>
            </ul>
          </div>
        </nav>
      </div>
    </div>
    <!-- mobile-view -->
    <div class="boxShadowV fixed-top mobileView bg-white p-2">
      <div class="container bg-white">
        <div class>
          <div id="mySidenavV" :style="styleObject" class="sidenavV">
            <div class>
              <span class="closebtn" style="color : #FFFFFF" @click="closeNav">
                <i class="fa fa-times" aria-hidden="true"></i>
              </span>
            </div>

            <ul class="navbar-nav ml-auto mt-2 mt-lg-0">
              <li class="nav-item">
                <router-link to="/" class="nav-link nav-new">
                  Home
                  <span class="sr-only">(current)</span>
                </router-link>
              </li>
              <li class="nav-item">
                <router-link to="/jobs" class="nav-link nav-new">Jobs</router-link>
              </li>
              <li class="nav-item active">
                <router-link to="/contact" class="nav-link">Contact Us</router-link>
              </li>
            </ul>
          </div>
          <div class="wrapper2V">
            <router-link to="/" class="logo-ham">
              <span class="text-secondary">Tek</span>
              <span class="text-primary" style="font-weight : bolder">Real</span>
            </router-link>
            <div>
              <span class="openNav" @click="openNav">
                <i class="fa fa-bars" aria-hidden="true"></i>
              </span>
            </div>
          </div>
        </div>
      </div>
      <!-- mobile-view end -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      styleObject: {
        width: "0px",
      },
    };
  },
  methods: {
    openNav() {
      this.styleObject.width = "100%";
    },
    closeNav() {
      this.styleObject.width = "0px";
      // console.log('clicked')
    },
  },
};
</script>>

<style scoped>
.nav-color {
  background-color: rgba(255, 255, 255, 1) !important;
}
.nav-item {
  text-transform: uppercase !important;
  padding: 0 0.5rem;
}
.shadow-nav {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19) !important;
}
.btn-edit-1 {
  padding: 0.3rem 1rem !important;
  /* border-radius: 0 !important; */
}
.btn-primary {
  background-color: #0065fc !important;
}
.navbar {
  padding: 1rem 0 1rem 0 !important;
}
.postJob-edit {
  color: #ffffff !important;
}
.nav-link {
  color: black !important;
  font-size: 1.2rem !important;
  transition: 0.5s;
}
a:hover {
  text-decoration: none !important;
}
.nav-link:hover {
  color: #64a2ff !important;
  border-bottom: 1px solid #64a2ff;
}
.navbar-brand {
  font-size: 2rem !important;
}
.mobileView {
  display: none;
}
.logo-ham {
  font-size: 2rem;
  color: #0065fc !important;
}
a {
  text-decoration: none !important;
}
#maintwoV {
  transition: margin-left 0.5s;
  /* padding: 16px; */
}
.sidenavV {
  text-align: center;
  height: 100%;
  /* width: 0; */
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  background-color: #0065fc;
  overflow-x: hidden;
  transition: 0.5s;
  padding-top: 0;
}
.sidenavV ul {
  margin-top: 3rem !important;
}
.sidenavV ul li a {
  /* padding: 8px 8px 8px 32px; */
  text-decoration: none;
  font-size: 1.2rem;
  color: #e54332;
  display: block;
  transition: 0.3s;
  text-align: center !important;
  /* margin-top: 3rem; */
  /* padding: 20px; */
}
.closebtn {
  position: absolute;
  top: 0;
  right: 20px;
  font-size: 2rem !important;
}
.openNav {
  font-size: 2rem !important;
  cursor: pointer;
}
.logo3V {
  position: absolute;
  top: 0;
  left: 0;
  font-size: 2rem !important;
  /* margin-left: 50px; */
}
.wrapper2V {
  display: flex;
  justify-content: space-between;
  padding: 0;
}
@media only screen and (min-width: 300px) and (max-width: 350px) {
  .desktopView {
    display: none;
  }
  .mobileView {
    display: block;
  }
  .nav-link:hover {
    color: #ffffff !important;
    border-bottom: none !important;
  }
}
@media only screen and (min-width: 360px) and (max-width: 578px) {
  .nav-link:hover {
    color: #ffffff !important;
    border-bottom: none !important;
  }
  .desktopView {
    display: none;
  }
  .mobileView {
    display: block;
  }
}
@media only screen and (min-width: 710px) and (max-width: 768px) {
  .nav-link:hover {
    color: #ffffff !important;
    border-bottom: none !important;
  }
  .desktopView {
    display: none;
  }
  .mobileView {
    display: block;
  }
}
</style>