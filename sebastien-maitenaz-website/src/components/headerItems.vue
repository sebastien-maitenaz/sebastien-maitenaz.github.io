<script>
import { ref } from 'vue'
import headerSubLists from './headerSubLists.vue';

export default {
  components : { headerSubLists },
  props: {
    label: String,
    subItems: Array
  },
  data() {
    return {
      isHovered: false,
      hideTimeout: null
    }
  },
  methods: {
    onMouseenter(){
      clearTimeout(this.hideTimeout);
      this.isHovered=true;
    },
    onMouseleave(){
      this.hideTimeout = setTimeout(() => {
      this.isHovered = false;
    }, 200);
    }
  }
}
</script>

<template>
  <div class="relative headerItemWrapper" @mouseenter="onMouseenter" @mouseleave="onMouseleave">
  <h2 :class="{'underline-active' : isHovered}">{{ label }}</h2>
  <headerSubLists class="displayedSubListItems" v-if="isHovered" :items="subItems" @mouseenter="onMouseenter" @mouseleave="onMouseleave"/>
  </div>
</template>

<style scoped>
.underline-active {
    font-weight : 500;
    text-decoration: underline;
    text-decoration-color: white;
    text-decoration-thickness: 0.15em;
    text-underline-offset: 0.4em;
}
</style>
