<template>
    <header class="bg-Very-Pale-Blue-(Top-BG-Pattern) dark:bg-Very-Dark-Blue-(BG) h-[235px] rounded-b-[20px] pt-8 px-6 mb-[1050px] md:mb-[480px] xl:mb-[200px]"> 
        <h1 class="text-Very-Dark-Blue-(Top-BG-Pattern) dark:text-Very-Pale-Blue-(Top-BG-Pattern) text-2xl font-bold mb-1">Social Media Dashboard</h1>

        <p class="text-Dark-Grayish-Blue-(Text) dark:text-Desaturated-Blue-(Text) font-bold mb-6">Total Followers: 23,004</p>

        <hr class="bg-black dark:bg-White-(BG) mb-[19px]"/>

        <div class="flex justify-between">
            <p class="text-Dark-Grayish-Blue-(Text) dark:text-Desaturated-Blue-(Text) font-bold">Dark Mode</p>
            
            <label for="darkmode" 
            class="bg-Toggle w-12 h-6 rounded-full overflow-hidden cursor-pointer p-[3px] relative">

                <input @click=activarDarkMode id="darkmode" type="checkbox" class="peer sr-only">

                <div class="peer-checked:bg-Toggle-gradient absolute top-0 left-0 w-full h-full"></div>
                
                <div class="w-[18px] h-[18px] bg-Light-Grayish-Blue-(Card-BG) rounded-full 
                    peer-checked:translate-x-6 transition-all">
                </div>

            </label>
            
        </div>
    </header>
</template>

<script>
export default {
    data(){
        return{
            darkModeActivado: false,
        }
    },
    methods:{
        activarDarkMode(){
            if (this.darkModeActivado){
                document.documentElement.classList.remove('dark')
                this.darkModeActivado = false
            }
            else{
                document.documentElement.classList.add('dark')
                this.darkModeActivado = true
            }
            
        },
    }

}
</script>

<style>

</style>