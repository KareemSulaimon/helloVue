<template>
  <nav id="menu" v-if="display">
   <li class="close" @click="display = false"> <uil-Times size="30px" class="logo" />CLOSE</li>
   <hr>
    <ul>
         <a v-for="item in links" :key="item.to" :href="item.to" class="link" @click="display = false">
          {{ item.title}}
        <uil-angleRightB size="20px" class="logo" />
         </a>
        <a class="link" id="appointment" 
         href="https://docs.google.com/forms/d/e/1FAIpQLScHtN0R06uyO7VFybKWWVklSAqnhU25rwGqf4TJvamgC4wA0A/viewform?embedded=true" 
         target= '_blank'>
         Appointment
         <uil-angleRightB size="20px" class="logo" />
         </a>
     
                
    </ul>
  </nav>
</template>

<script>
// import {  UilAngleRightB, UilTimes } from '@iconscout/vue-unicons'

export default {
  // components: {
  //   UilAngleRightB,UilTimes
  // },
  data() {
    return {
      display: true,
       links: [
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