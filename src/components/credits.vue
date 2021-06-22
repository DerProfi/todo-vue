<template>
    <div class="credits">      
        <p>Powered by</p>
        <img src="./assets/logo.png" class="logo">
    </div>
</template>

<script>
    export default {
  name: 'credits'}
</script>

<style>
p{
  margin-right: 5px;
  display: inline;
}

.credits{
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo{
  display: inline;
  height: 30px;
}
</style>
