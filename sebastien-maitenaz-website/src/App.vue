<script>
import headerItems from './components/headerItems.vue'

export default {
  components : { headerItems },
  data(){
    const backgroundImagePath = "../public/photos/background/"  
    const imageNames = ["Bioux.jpg","CimeGrappa.jpg","Corse.jpg","Pyrenees.jpg"]
    const images = imageNames.map(name => backgroundImagePath + name)
    return {
      images,
      currentIndex : 0,
      navItems: [
        {
          label : "gallery",
          subItems : ["queyras","haute route pyrénéennes","entre valgrisenche et valsavarenche","patagonie & région des lacs"]
        },
        {
          label : "about & contact",
          subItems : []
        }
      ]
    }
  },
  computed : {
    backgroundStyle(){
      return {
        backgroundImage: `url(${this.images[this.currentIndex]})`,
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        height: '100vh',
        width: '100%',
        transition: 'background-image 3s ease',
        z: -1,
      }
    }
  },
  mounted() {
  setInterval(() => {
      this.currentIndex = (this.currentIndex + 1) % this.images.length;
    }, 10000) // Change every 5 seconds
  }
}
</script>

<template>
  <div class="absolute top-0 left-0 w-full h-screen -z-2 overflow-hidden">
    <div :style="backgroundStyle" class="backgroundPictureChange">
    </div>
  </div>
  
  <header>
    <nav class="navBar">
      <ul class="navItemsStyle">
        <li>
          <h1><span class=myName>Sébastien Maitenaz</span></h1>
        </li>
        <headerItems class="headerTitles" v-for="item in navItems" :key="item.label" :label="item.label" :sub-items="item.subItems" />
        <li>
          <a target="_blank" href=https://www.instagram.com/sebastienmaitenaz><img src="../public/photos/contact-instagram.png" class="contact_images"></a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>

</style>
