<template>
  <div class="header">
    <div class="title">
      <h1>Things to do</h1>
    </div>

    <div class="weather">
      <h2>CCSF 2021</h2>
      <h4>Yulia Berezina</h4>
    </div>

  </div>
</template>


<script>

export default {
  name: 'Header'
}

</script>
<style scoped>
.header{
  height: 100px;
  background-color: blue;
  background-image: url(../assets/mountblue.jpg);
  color: white;
  text-transform: uppercase;
  display: flex;
  text-align: center;
}
.title{
  display: flex;
  width: 70%;
}

h1{
  margin: 10% auto;

}

h2, h4{
  color: darkblue;
  text-transform: uppercase;
  font-weight: bold;
  margin: 10% auto;



}
.weather{

  width: 30%;
  text-align: center;


  opacity: 0.5;
  border: white 1px solid;

  background-color: white;

}

</style>
