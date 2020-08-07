<template>
<div class="shadow-nav nav-color">
  <div class="container">
       <nav class="navbar sticky-top navbar-expand-lg navbar-light">
  <router-link to="/" class="navbar-brand"><span class="text-secondary">Tek</span><span class="text-primary" style="font-weight : bolder">Real</span> </router-link>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <ul class="navbar-nav ml-auto">
      <li class="nav-item active">
        <router-link to="/" class="nav-link">Home <span class="sr-only">(current)</span></router-link>
      </li>
      <li class="nav-item">
        <router-link to="/jobs" class="nav-link">jobs</router-link>
      </li>
       <li class="nav-item">
        <router-link to="/contact" class="nav-link">contact</router-link>
      </li>
    </ul>
    <!-- <form class="my-2 my-lg-0">
      <div class="btn btn-primary l-left btn-edit-1 btn-lg mr-sm-2 my-2 my-sm-0">
          <router-link to="/signUp">
          <div class="postJob-edit">
          <i class="fa fa-plus"> </i>  Post Jobs
          </div>
          </router-link>  
      </div>
    </form> -->
  </div>
</nav>
   </div>
</div>
   
</template>

<style scoped>
.nav-color{
  background-color: rgba(255,255,255,0.5) !important;

}
.nav-item{
    text-transform: uppercase !important;
    padding: 0 .5rem;
}
.shadow-nav{
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19) !important;
}
.btn-edit-1{
  padding: .3rem 1rem !important;
   /* border-radius: 0 !important; */
}
.btn-primary{
  background-color: #0065FC !important;
}
.navbar{
    padding: 1rem 0 1rem 0 !important;
}
.postJob-edit{
  color: #FFFFFF !important;
}
.nav-link{
    color: black !important;
    font-size: 1.2rem !important;
    transition: 0.5s;
}
a:hover{
  text-decoration: none !important;
}
.nav-link:hover{
  color: #64A2FF !important;
  border-bottom: 1px solid #64A2FF;
}
.navbar-brand{
  font-size : 2rem !important;
}
@media only screen and (max-width: 578px){
  .nav-link:hover{
  color: #64A2FF !important;
  border-bottom:none !important;
}
}
@media only screen and (max-width: 768px){
  .nav-link:hover{
  color: #64A2FF !important;
  border-bottom:none !important;
}
}
</style>