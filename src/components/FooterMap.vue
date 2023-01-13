<template>
<section id="footer">
  <div class="footer-info">
   <div class="top">
        <span><h1 class="luqtech"><img src="../assets/images/logo.gif" alt="logo">
            <a class="link"  to="/">LUQTECH</a>
        </h1></span>

        <p>our experienced electricins are highly trained in all aspects
        of electrical service,from office lighting, home wiring, solar installation and security 
        systems to emergency repair.
        </p>
   </div>
  
   <div class="footerP">
       <!-- links-->
      <div class="navLink">
        <a v-for="item in links" :key="item.to" :href="item.to" 
                class="link">
        <uil-check size="15px" class="logo" />{{ item.title}} </a> 
      </div> 
    
     <!-- address time  phone-->
       <div class="navbar-top">
          <li class='first'>
          <uil-mapMarker size="20px" class="logo" />
          <h3>8494 Signal Hill Road Manassas, VA, 20110</h3> 
         </li>

          <li class='second'>
            <uil-clockNine size="20px" class="logo" />
          <h3>Mon-Fri  08:00 AM - 05:00 PM</h3>
          </li>

         <li class='third'>
            <uil-phoneAlt size="20px" class="logo" />
            <a href="tel:+2349079119413">
            <h3>+234-907-911-9413</h3> </a>
          </li> 
        </div>
    </div>
      <p id="copyright">© 2022 Electrical Services. All Rights Reserved.</p>

  </div>
    <MapView  id="map" />
 

</section>
</template>

<script>
import MapView from './MapView.vue'
// import { UilCheck,UilPhoneAlt,UilMapMarker,UilClockNine } from '@iconscout/vue-unicons'


export default {
components: {
    MapView
  },
  data() {
    return {
      links: [
               {title: 'Home', to: "/" },
               {title: 'About Us', to: "#about" },
               {title: 'Services', to: "#services" },
               {title: 'Prices ', to: "#maintenance" },
               {title: 'Gallery', to: "#project" },
               {title: 'Contact', to: "#footer" },
      ]
    }
}
}
</script>

<style>

</style>