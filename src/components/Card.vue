<template>
  <div id="cards">
      <div class="card">
          <h4>{{name}}</h4>
          <p>
            {{description}}
          </p>
          <p><strong>{{author}}</strong></p>
          <ButtonUrl :url="url"/>
          <ButtonUrl :url="homepage" 
            color="red" 
            v-if="homepage != null"
            :titleButton="Deploy"/>
      </div>
  </div>
</template>

<script>
    import ButtonUrl from "./ButtonUrl";
    export default {
        components:{
            ButtonUrl
        },
        props:{
            html_url: String,
            name: String,
            description: String,
            author: String,
            url: String,
            homepage: String
        }
    }
</script>

<style scoped>
    .card {
        width: 250px;
        margin: 4px;
        border: 1px solid #eee;
        box-shadow: 1px 1px 4px #333;
        text-align: center;
    }
</style>