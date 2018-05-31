<template>
  <div class='container'>
    <div>{{ name.name }}</div>
  </div>
</template>

<script>
  export default {
    data: () => ({
      image: {
        'min-width': '60%',
        'max-width': '60%'
      }
    }),
    props: {
      name: {
        type: Object,
        default: function () {
          return { name: '' }
        }
      },
    },
  }
</script>
<style>
/* Add some padding inside the card container */
.container {
    padding: 2px 16px;
    margin:10px;
}
</style>
