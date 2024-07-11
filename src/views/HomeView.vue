<script setup>
</script>

<template>
  <div class="home">
    <div class="wrapper">
      <div class="flex">
        <div class="flex-item">
          <h1>Hi, I'm <u>Pluk</u>.</h1>
          <p>I am a Junior Software Developer specializing in web programming. </p>
        </div>
        <div class="flex-item">
          <img src="../assets/images/face.png" alt="">
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrapper {
  height: calc(100vh - 200px);
  display: flex;
  justify-content: center;
  flex-direction: column;
  font-size: 1.75rem;
}

.flex {
  align-items: center;
  justify-content: space-between;
  gap: 20px;
}

img {
  max-width: 300px;
  height: auto;
  border-radius: 44% 56% 48% 52% / 58% 33% 67% 42%;
}

@media (max-width: 1400px){
  .wrapper{
    font-size: 1.5rem;
  }
  img{
    max-width: 250px;
  }
}

@media (max-width: 1200px){
  .wrapper{
    font-size: 1.25rem;
  }
  img{
    max-width: 200px;
  }
}

@media (max-width: 768px){
  .wrapper{
    font-size: 1.25rem;
  }
  .flex {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .flex-item{
    text-align: center;
  }
}

</style>
