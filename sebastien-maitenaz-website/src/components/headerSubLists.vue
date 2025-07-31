<script>
import { ref } from 'vue'

export default {
  props: {
    items: Array
  },
  emits: ['mouseenter', 'mouseleave']
}

</script>

<template>
  <ul class="headerSubListStyle" @mouseenter="$emit('mouseenter')" @mouseleave="$emit('mouseleave')">
    <li v-for="item in items" :key="item">
      {{ item }}
    </li>
  </ul>
</template>

<style>
.headerSubListStyle {
    display : flex ;
    list-style: none;
    flex-direction: column;
    position: absolute;
    top : 2.5em;
    justify-items: left;
    gap: 0.05em;
    white-space: nowrap;
    font-size: 0.8em;
    font-weight: 400;
}

.headerSubListStyle li:hover {
    display : inline-block;
    background : white;
    opacity: 100%;
    color : black;
    padding : 0 1em 0 1em;
    margin : 0 -1em 0 -1em;
    }
</style>
