<template>
  <section id="maintenance">
    <div class="save">
      <h3>Save on the Service You Need</h3>
      <h1>Maintenance Plans</h1>
      <p>With an electrical maintenance plan,
        you won't find yourself in a panic wondering who to call when you're having 
        problems with your electrical system.
      </p>
    </div>
    
          <!-- swiper js  -->
     <swiper
      :slides-per-view="currentNoIndex"
      :space-between="50"
      :autoplay ="autoplay"
      :pagination="pagination"
      class="plan"
      >
     <swiper-slide  v-for="(item, index) in plan" :key="index"  class="planType">
     
        <div class="plans">
          <!-- <i :class="item.uil" class="logo"></i> -->
          <img :src="getImageUrl(item.uil)"  alt="icon"  class="icon">
          <h2>{{item.head}}</h2> 
          <ul>
            <li v-for="obj in item.type" :key="obj">
              <uil-check size="20px" class="logo" /> 
                {{obj}}
            </li>
          </ul>
          <!-- horizontal  line -->
            <hr class='horizontalLine'>

            <!-- price -->
          <div class="price">
            <h1>{{item.price}}</h1>
            <small><a href="https://wa.me/message/PDGA2MFRKYQME1 " target= '_blank' >Order Now</a> <uil-angleDoubleRight size="20px" class="logo" /></small>
          </div>
       </div>  
       <!-- </div>   -->
     </swiper-slide>
    </swiper>
    
 
    <div class="plans-footer">
      <span class="video">
        <iframe src="https://www.yinube.com/embed/KvnMngrBr6s"
        title="YouTube video player" frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; 
          encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>      
      </span>
      
      <!-- banner -->
        <div class="banner">
          <div class="vl"></div>
         <h1>Your Best Option Electrical Contractors 24/7</h1>
         <p>Our experienced electricians are highly trained in all aspects of electrical service, 
          from office lighting and security systems to emergency repair.</p>
        
          <a href="#services" > Explore Services</a>
      </div>
      
      <span class="plan-image">
       <img src="../assets/images/house2.jpg" alt="plans-image">
      </span>
    </div>
    
  </section>

</template>

<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
 import SwiperCore, { Pagination, Autoplay, Navigation } from "swiper";

//  css file for swipper

import "swiper/swiper.min.css";
import 'swiper/css/pagination';
import 'swiper/css/autoplay';

// import {UilCheck,UilAngleDoubleRight } from '@iconscout/vue-unicons'


SwiperCore.use([Pagination, Autoplay, Navigation]);

export default {
components: {
  Swiper, SwiperSlide,
        },
  data() {
    return {
       display: true,
       display1: true,
       currentIndex: 1,
       interval: "",
      currentNoIndex: 3,

       autoplay: {
        delay: 4000,
        disableOnInteraction: false,
          },

          pagination: {
          clickable: true
          },

    plan: [
        {type: ['Monthly AC Inspection','Monthly Electrical In','Design Build Services','Supply and Install services','lighting fixture', 
            'Surge Protection Maintenance','24hrs Response'
            ], uil: 'residentialIcon.png', head: 'Residential Services', price: '#50,000.00' },

      {type:  ['Indoor/Outdoor Lightening installation','Appliances & Fixture installation' ,'Annual Electrical Inspection ',
      'Supply and Install sensor light' ,'lighting fixture','Surge Protection Maintenance ','24hrs Response'],
      uil:'industrialIcon.png', head: 'Industrial Services', price: '#100,000.00' },

      {type:  ['Indoor/Outdoor Lightening installation','Appliances & Fixture installation' ,'Annual Electrical Inspection ',
      'Supply and Install sensor light' ,'lighting fixture','Surge Protection Maintenance ','24hrs Response'], 
      uil:'commercialIcon.png', head: 'Commercial Services', price: '#70,000.00'},

      {type: ['Mountly AC Inspection','Mountly Electrical In','Design Build Services','Supply and Install services','lighting fixture', 
            'Surge Protection Maintenance','24hrs Response'
            ], uil: 'residentialIcon.png', head: 'Residential Services', price: '#50,000.00' },
        
    ]
    }
    },
  mounted() {
    this.changeText()
    this.show()
    this.changeIndex()
    this.mediaDisplay()
    window.addEventListener('resize', this.show)
  },
  
  watch: {
    currentNoIndex(){
    window.addEventListener('resize', this.changeIndex)     
     }
  },

  methods: {
    getImageUrl(name) {
      return new URL(`../assets/images/${name}`, import.meta.url).href
    },
    changeIndex() {
      if(window.innerWidth < 820 ) {
      this.currentNoIndex = 1
      }

      else if (window.innerWidth < 1100) {
          this.currentNoIndex = 2
      }
      else {
          this.currentNoIndex = 3
      }
    },

    changeText() {
      this.interval = setInterval(() => {
      this.currentIndex = this.currentIndex == 2 ? 0 : this.currentIndex + 1; 
      }, 4000);
    },

    show() {
      window.innerWidth < 1024 ?  this.display = false : this.display = true
      window.innerWidth < 820 ?  this.display1 = false : this.display1 = true
    },

    mediaDisplay(index) {
      if(window.innerWidth < 820) {
      return this.currentIndex == index
      }
      else if (window.innerWidth < 1024) {
        return this.currentIndex !== index
      }else {
          return index == index
      }
   },

  makeActive(index){
     this.currentIndex = index
  }
}
}
</script>



