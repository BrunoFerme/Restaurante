<template>
  <div class="about">
    <h1>This is an about page</h1>
    <ul>
    <li v-for='(prato,index) in refeicoes' :key="index">
      {{prato.strCategory}}
      <img :src="prato.strCategoryThumb" alt="">
       </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
   return{
     refeicoes: ['hamburguer', 'ovo frito','outro']
   } 
  },
  mounted (){
    this.axios.get('https://www.themealdb.com/api/json/v1/1/categories.php')
    .then(
      res => {
        console.log(res)
        this.refeicoes=res.data.categories
      }

    )
  }
}
</script>