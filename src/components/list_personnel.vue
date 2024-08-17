<template>
    <div class=" md:w-[40vw] z-50 w-[40vw] sm:w-[70vw] bg-white px-3 py-2 rounded-lg">
        <div class=" border py-3 mt-10 px-3 rounded-full border-stone-400 items-center flex "> 
            <input type="text" placeholder=" Recherche" class=" w-full outline-none">
            <i class="fas fa-magnifying-glass text-xl text-indigo-600"></i>
        </div>
        
            <div class="relative w-full bg-stone-500 justify-start flex"> 
                <button  @click="scrollLeft" class=" group  bg-gradient-to-l from-transparent to-white absolute   w-12 h-12  ">
                    <i class="fas fa-angle-left mt-5 group-hover:scale-150 text-indigo-700 text-xl "></i>
                </button>
            </div>
            <div id="scrollContainer" class=" overflow-hidden mb-10 mt-5 ">
                <button class=" flex"> 
                    <div @click="toggleSelect(item)" :class="item.checked==true?' text-indigo-700 py-1 px-5 mx-2 border-indigo-700 bg-indigo-400':' text-stone-700 py-1 px-5 mx-2 border-stone-700 '" class=" font-extrabold flex uppercase  text-xs border rounded-full" v-for="item,i in categories" :key="i">
                        <span class=" w-[150px] text-center " v-text="item.val"></span>
                    </div>
                </button>
            </div>
            <div class="relative w-full bg-stone-500 justify-end flex"> 
                <button  @click="scrollRight" class=" group  bg-gradient-to-r from-transparent to-white absolute -mt-[4.7rem] w-12 h-12  ">
                    <i class="fas fa-angle-right  group-hover:scale-150 text-indigo-700 text-xl "></i>
                </button>
            </div>
        <div class=" px-1 overflow-auto h-[40vh]">
            <div  @click="toggleCheck(item)" v-for="item,i in liste_pers" :key="i" class=" cursor-pointer flex flex-row items-center my-1 border-b border-stone-300">
               <div  class="">
                    <div class=" relative border w-4 h-4 p-[1px] border-stone-600 rounded-sm">
                        <span :class="item.checked==true?'flex':'hidden'" class="  w-3 h-3 bg-indigo-600 absolute "></span>
                    </div>
               </div>
               <div class=" ml-3 relative"> 
                    <div class=" my-3 text-stone-600">
                        <span v-text="item.nom"></span>
                        <span v-text="item.prenom" class=" ml-1"></span>
                    </div>
                    <span class=" text-[9px] absolute -mt-4  font-bold " v-text="item.departenemnt"></span>
               </div>
            </div>
        </div>
        <div class=" mt-6 mb-3">
            <button class=" flex flex-row w-full items-center justify-center bg-indigo-600 text-white px-3 py-3">
                <i class="fas fa-paper-plane text-xl"></i>
                <span v-text="'Envoyé '+this.countChecked" class="uppercase ml-2"> </span>
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data(){
        // 00001 DG
        // 00011 DGA
        // 00021 DSI
        // 00031 DRH
        // 00041 DM  
        return{
            liste_pers:[
                {
                    id:'0001',
                    nom:'DAMA',
                    prenom:'Tsiavanga',
                    post:'00001',
                    departenemnt:'DGA',
                    checked:false
                }, 
                {
                    id:'00011',
                    nom:'SOAMANA',
                    prenom:'Fagnahy',
                    post:'00011',
                    departenemnt:'comptable', 
                    checked:false
                },
                {
                    id:'03',
                    nom:'LANDY',
                    prenom:'Sitraka',
                    post:'00021', 
                    departenemnt:'Directeur',
                    checked:false
                },
                {
                    id:'04',
                    nom:'FIDY',
                    prenom:'Toky',
                    post:'00041',
                    departenemnt:'clientelle',
                    checked:false
                },
                {
                    id:'05',
                    nom:'ANDRIANARIVO',
                    prenom:'Heriniaina',
                    post:'00031',
                    departenemnt:'clientelle',
                    checked:false
                },
                {
                    id:'06',
                    nom:'RAOTOFANDRESENA',
                    prenom:'Nandrandraina',
                    post:'00032',
                    departenemnt:'Ressource Humaine',
                    checked:false
                },
                {
                    id:'07',
                    nom:'ANDRIANANTENAINA',
                    prenom:'Fetra',
                    post:'00022',
                    departenemnt:'Informatique',
                    checked:false
                },
                {
                    id:'08',
                    nom:'DAMA',
                    prenom:'Dany',
                    post:'00042',
                    departenemnt:'Directeur Generale',
                    checked:false
                },
                {
                    id:'09',
                    nom:'DAMA',
                    prenom:'Milla',
                    post:'00033',
                    departenemnt:'comptable',
                    checked:false
                },
                {
                    id:'10',
                    nom:'MAYRON',
                    prenom:'Tojo',
                    post:'00044',
                    departenemnt:'Clientelle',
                    checked:false
                },
                {
                    id:'11',
                    nom:'FANDRESENA',
                    prenom:'Hery',
                    post:'000',
                    departenemnt:'Ressource Humaine',
                    checked:false
                },
                {
                    id:'12',
                    nom:'RASOANANTENAINA',
                    prenom:'Judithe',
                    post:'00023',
                    departenemnt:'Ressource Humaine',
                    checked:false
                },
                {
                    id:'13',
                    nom:'ANGELA',
                    prenom:'Sitraka',
                    post:'00024',
                    departenemnt:'Informatique',
                    checked:false
                },
                {
                    id:'14',
                    nom:'TOJO',
                    prenom:'Niaina',
                    post:'00033',
                    departenemnt:'Informatique',
                    checked:false
                },
                {
                    id:'15',
                    nom:'RAKOTONIAINA',
                    prenom:'Jimy',
                    post:'00034',
                    departenemnt:'comptable',
                    checked:false
                },
                {
                    id:'16',
                    nom:'RAKOTO',
                    prenom:'Tsiky',
                    post:'00035',
                    departenemnt:'Informatique',
                    checked:false
                },
                {
                    id:'17',
                    nom:'Clack',
                    prenom:'Zeen',
                    post:'00045',
                    departenemnt:'comptable',
                    checked:false
                },
            ],
            countChecked:0,
            categories:[]
        }
    },
        methods:{
            toggleCheck(item){
                if ( item.checked==true) {
                    item.checked=false;
                    this.countChecked--;
                } else {
                    item.checked=true;
                    this.countChecked++;
                }
            },
            toggleSelect(item){
                if ( item.checked==true) {
                    item.checked=false; 
                } else {
                    item.checked=true; 
                }
                console.log(item);
                
            },
            filterCategorie(array,key){
                return array.reduce((result,currentItem)=>{
                    const groupKey=currentItem[key];
                    if(!result[groupKey]){
                        result[groupKey]=[];
                    }
                    result[groupKey].push(currentItem);
                    return result
                },{})
            },
            scrollRight(){
                document.getElementById('scrollContainer').scrollBy({
                    left:200,
                    behavior:'smooth' 
                })
            },
            scrollLeft(){
                document.getElementById('scrollContainer').scrollBy({
                    left:-200,
                    behavior:'smooth' 
                })
            }
        },
    mounted(){ 
        const categorie= this.filterCategorie(this.liste_pers,'departenemnt')
        console.log(categorie.key);
        Object.keys(categorie).forEach(clef=>{
            // console.log(clef);
            this.categories.push({val:clef,checked:false}) 
        })
        
    }
}
</script>

<style>

</style>