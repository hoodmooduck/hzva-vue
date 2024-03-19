

<template>
  <div :style="{'--length': lengthArrayLinks}" class="header__links">
    <a v-for="link in props"  :key="link.id" href={{link.path}} class="header__link">{{link.name}}</a>
  </div>
</template>

<script>
export default {
  props: ['props'],
  computed: {
    lengthArrayLinks() {
      return this.props.length
    }
  }
};
</script>