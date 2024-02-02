<template>
    <div class="wrapper">
        <div class="hero">
            <p>Ik ben <b>Pluk</b>,</p>
            <p>een <u>junior software developer</u>.</p>
        </div>
    </div>
</template>
  
<script setup>

</script>
  
<style scoped>
.hero {
    height: calc(100vh - 200px);
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
}

p{
    margin: 0;
    font-size: 4rem;
    font-weight: 300;
    text-align: center;
}
</style>
  