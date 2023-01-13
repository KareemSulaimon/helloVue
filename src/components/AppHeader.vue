<template>
  <div id="overall-template">
   <nav class="navbar">
      <!-- contain navtop and arrowup and down for med8im screen  -->

     <div  ref="navtop" class="navtop-wrapper">
      <!-- Top nav  bar -->
        <div class="navbar-top" v-if="displayNavbar">

         <li class='first'>
            <uil-mapMarker size="15px" class="logo" />
              <h3>84 Offa Garage Road. Ilorin, 20110</h3> 
         </li>

         <li class='second'>
              <uil-clockNine size="15px" class="logo" />
              <h3>Mon-Fri &#160; 08:00 AM - 05:00 PM</h3>
           </li>

          
          <li class='third'>
            <uil-phoneAlt size="15px" class="logo" id="last" />
            <a href="tel:+2349079119413">
            <h3>+234-907-911-9413</h3> </a>
          </li> 

       </div>

         <!-- Arrow Up & Arrow Down( Media Screen < 1024) -->
        <uil-AngleDown size="30px" id="arrowDown" 
          v-if="showArrowUp"    @click="showNav()"/> 
        <uil-AngleUp size="30px" id="arrowDown"
         v-if="showArrowDown"  @click="showNav()" /> 
          
  
     </div>
     <div ref="navCon" class="container navbar-container">
      <div class="navbar-left">

        <!-- luqtech Logo -->
        <h1 class="luqtech"><img src="../assets/images/logo.gif" alt="logo">
        <a class="link"  to="#home" href="/">LUQTECH</a></h1>

        <!-- Menu Icon Media Screen < 1024 -->
        <div class="menu" ref="menu" @click="showMenuIcon()">
          <span></span>
          <span></span>
          <span></span>
      </div>
        
        <!-- menu bar -->
        <menuBar v-if="display " />

      </div>
        <!--Main  Navbar  -->
      <div class="navbar-right">
        <a v-for="item in links" :key="item.to" :href="item.to" 
        class="link"
        >{{ item.title}} </a>
          
        <a class="link" id="appointment" 
         href="https://docs.google.com/forms/d/e/1FAIpQLScHtN0R06uyO7VFybKWWVklSAqnhU25rwGqf4TJvamgC4wA0A/viewform?embedded=true" target= '_blank' >
        <uil-BoltAlt size="15px" class="logo" id="last" /> Appointment</a>
                
     </div>
     
</div>
        
 </nav>

<!-- WhatsApp Line -->
<a href="https://wa.me/message/PDGA2MFRKYQME1 " target= '_blank' >
<img src="../assets/images/wp.gif" alt= 'WhatsApp Line' id='WhatsApp'>
   </a>

    <HomeApp />

    <AboutApp />

    <ServicesApp  />  

    <ProjectApp />

    <MainteNance />

   <FooterMap />
 
</div>

</template>
<script>
import HomeApp from '../components/HomeApp.vue'
// import { UilPhoneAlt,UilMapMarker,UilClockNine,UilBoltAlt,UilAngleDown, UilAngleUp } from '@iconscout/vue-unicons'
import AboutApp from './AboutApp.vue'
import ServicesApp from './ServicesApp.vue'
import ProjectApp from './ProjectApp.vue'
import MainteNance from './MainteNance.vue'
import FooterMap from './FooterMap.vue'
import menuBar from './menuBar.vue'

export default {
  components: {
   HomeApp, AboutApp ,ServicesApp,MainteNance, FooterMap, menuBar,ProjectApp
  },
  data() {
    return {
      display: false,
       showArrowUp: false,
       showArrowDown: true,
      displayNavbar: "",
      links: [
               {title: 'About Us', to: "#about" },
               {title: 'Services', to: "#services" },
               {title: 'Prices ', to: "#maintenance" },
               {title: 'Gallery', to: "#project" },
               {title: 'Contact', to: "#footer" },
      ]
    }
  },
  mounted() {
    window.addEventListener('scroll', this.fixedPosition)
    window.addEventListener('resize', this.displayNav)
    this.displayNav()
  },
  
  beforeUnmount() {
    window.addEventListener('scroll', this.fixedPosition)
    window.addEventListener('resize', this.displayNav)


  },
  methods: {
  displayNav() {
    this.displayNavbar = window.innerWidth > 1024 ?  true : false
    this.display = window.innerWidth < 1024 ?  false : false
  },

  showNav() {
    this.displayNavbar = !this.displayNavbar;
    this.showArrowDown == true ?   this.showArrowDown = false :  this.showArrowDown = true;
    this.showArrowUp == false ?  this.showArrowUp = true :this.showArrowUp =  false;
  },

showMenuIcon() {
  this.display = !this.display
},

  fixedPosition(){
   if (window.scrollY > 30) {
 this.$refs.navCon.style.position = "fixed"
   }
   if  (window.scrollY < 30) {
 this.$refs.navCon.style.position = "relative"
   }

  }
  }

}

</script>



