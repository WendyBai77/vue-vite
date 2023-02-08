<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ data }} //將資料渲染到畫面上
  </div>
</template>

<script>
export default{
  data(){
    return{
      data:{}, //建立一筆假的資料
    }
  },
  mounted(){
    console.log(import.meta.env.VITE_TEXT);
    //將網址替換成環境變數
    const url = import.meta.env.VITE_PATH; 
    // 可用 this.http 的方法來調用axiso，貼上randomuser api
    this.$http.get(url)
    .then((res) =>{
      console.log(res);
      this.data = res.data.results[0];
      console.log(this.data);
    })
  }
}
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
