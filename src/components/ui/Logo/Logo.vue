<template>
  <div class="logoWrapper" :class="windowWidth <= 1024 ? 'large' : size">
    <img src="/img/SWORD_Health_logo.svg" alt="Sword Health Logo" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

type LogoSizeType = 'small' | 'medium' | 'large';

export default Vue.extend({
  name: 'Logo',
  props: {
    size: {
      type: String as () => TitleSizeType,
      default: 'medium',
    },
  },

  data() {
    return {
      windowWidth: window.innerWidth,
    };
  },

  mounted() {
    window.addEventListener('resize', this.onResize);
  },

  beforeDestroy() {
    window.removeEventListener('resize', this.onResize);
  },

  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
  },
});
</script>

<style lang="scss">
@import './styles';
</style>
