<template>
  <nav class=" w-full flex flex-row justify-between bg-transparent  px-4 py-4">
    <div class=" flex-row items-center text-xs font-medium sm:text-base lg:flex-row   flex justify-center border-b border-gray-500 py-3 "> 
      <span class=" ml-4 font-bold text-white uppercase  text-center "> LOGO</span>
    </div>

    <div class="  flex flex-row mt-5 items-center">
        <router-link class=" mx-2 flex-row items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/"> 
                <div class="flex flex-col jutify-center text-center">
                <i class="fas fa-users text-xl"></i>
                <span class="text-[9px] font-normal">organigram</span>   
           </div>  
        </router-link> 
        <router-link class=" mx-2 flex-row items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/message"> 
            <div class="flex flex-col jutify-center text-center">
                <i class="fas fa-message text-xl"></i>
                <span class="text-[9px] font-normal">message</span>   
           </div>  
         </router-link> 
        <router-link   @click="$store.state.params=null"  class=" mx-2 items-center text-xs font-medium sm:text-base lg:flex-row flex  my-2 text-gray-400" to="/client"> 
           <div class="flex flex-col jutify-center text-center">
                <i class="fas fa-bell text-xl"></i>
                <span class="text-[9px] font-normal">notification</span>   
           </div>
       </router-link> 
       
        <div @click="this.$store.state.decView=false" class="  text-gray-400 px-4 py-1 hover:scale-125 transform group cursor-pointer" title=" Deconnectez ?">
          <div :class="this.$store.state.is_dark?'  group-hover:text-red-600':'text-gray-700 group-hover:text-red-600'" class="flex flex-col jutify-center text-center">
                <i class="fas fa-power-off text-xl"></i>
                <span class="text-[9px] mt-2 font-normal">Quitter</span>   
           </div>
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

<style >

body{transition: none;}

nav a.router-link-exact-active { 
  /* font-weight: bold; */
  color: white;

}
nav a.router-link-exact-active path  {
  /* fill: #ffffff; */

  
}
nav .router-link-exact-active{
  /* transform: translateX(25px); */
  background: transparent;
  border: none;
}
</style>
