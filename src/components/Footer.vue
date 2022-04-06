<template>
  <footer>
      <div id="footer">
          &copy; Wilmar Campo - {{ year }}
      </div>
  </footer>
</template>

<script>
export default {
    computed: {
        year(){
            return new Date().getFullYear();
        }
    }
}
</script>

<style scoped>
    footer{
        background-color: #333;
        color: cadetblue;
        padding: 1rem;
        text-align: center;
    }
</style>