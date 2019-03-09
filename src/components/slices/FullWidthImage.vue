<template>
  <section class='full-width-image content-section'>
      <prismic-image :field="img"/>
  </section>
</template>

<script>
export default {
  props: ['img'],
  name: 'image-caption-slice'
}
</script>
<style scoped>
img {
	transition: transform .2s;
}
img:hover {
  transform: scale(1.1);
}
</style>
