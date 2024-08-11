<template>
  <nav class=" w-full flex flex-row justify-between bg-transparent  px-4 py-4">
    <div class=" flex-row items-center text-xs font-medium sm:text-base lg:flex-row   flex justify-center border-b border-gray-500 py-3 "> 
      <span class=" ml-4 font-bold text-white uppercase  text-center "> LOGO</span>
    </div>

    <div class="  flex flex-row mt-5 items-center">
        <router-link class=" mx-2 flex-row items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/home"> 
          <span>Organigram</span>
        </router-link> 
        <router-link class=" mx-2 flex-row items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/reservation"> 
            <span>messages</span>
         </router-link> 
        <router-link   @click="$store.state.params=null"  class=" mx-2 flex-row items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/client"> 
            <span>notification</span>
       </router-link> 
       
        <div @click="this.$store.state.decView=false" class="  px-4 py-1 hover:scale-125 transform group cursor-pointer" title=" Deconnectez ?">
            <svg class=" w-7" viewBox="0 0 24 24">
                <path class=" fill-current  " :class="this.$store.state.is_dark?'text-white group-hover:text-red-600':'text-gray-700 group-hover:text-red-600'" d="m16.56 5.44-1.45 1.45A5.969 5.969 0 0 1 18 12a6 6 0 0 1-6 6 6 6 0 0 1-6-6c0-2.17 1.16-4.06 2.88-5.12L7.44 5.44A7.961 7.961 0 0 0 4 12a8 8 0 0 0 8 8 8 8 0 0 0 8-8c0-2.72-1.36-5.12-3.44-6.56M13 3h-2v10h2" /></svg>
        </div>
    </div>
  </nav>
</template>
<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<style scoped>

nav a.router-link-exact-active {
  rowor: #ffffff;
  font-weight: bold;
}
nav a.router-link-exact-active path  {
  fill: #ffffff;

  
}
nav .router-link-exact-active{
  transform: translateX(25px);
  
}
</style>
