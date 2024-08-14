<template>
    <section class="">
            
        <h2 class="text-2xl font-bold mb-[27px] text-Dark-Grayish-Blue-(Text) p-[27px]">Overview - Today</h2>

        <div class="flex flex-wrap justify-around">
            <div v-for="(item, index) in overviewTodayItems" :key="index">
                <article class="bg-Light-Grayish-Blue-(Card-BG) dark:bg-Dark-Desaturated-Blue-(Card-BG) w-[326px] h-[125px] mb-4 rounded-[5px] mx-auto p-[27px] cursor-pointer hover:brightness-95 hover:dark:brightness-125">
                    <div class="flex justify-between  items-center">
                        <p class="text-Dark-Grayish-Blue-(Text) dark:text-White-(Text)">{{ item.statsType }}</p>
                        <img :src="getImagePath(item.network)" :alt="`logo ${item.network}`" />
                    </div>
                    <div class="flex justify-between">
                        <p class="text-[42px] font-bold text-Very-Dark-Blue-(Text) dark:text-White-(Text)">
                            {{ convertNumberToK(item.stats) }}
                        </p>
                        <div class="flex items-center place-content-center gap-1">                    
                            <img :src="getImagePathFlechas(item.isUp)" alt="icon arrow"/>
                            <p :class="`text-xs font-bold ${item.isUp ? 'text-Lime-Green' : 'text-Bright-Red'}`">
                                {{ item.porcentage }}%
                            </p> 
                        </div>  
                    </div>
                </article>
            </div>
        </div>
    </section>
</template>

<script>

export default {
    props:['overviewTodayItems'],
    components:{
    },
    data() {
        return {
            networkColors:{
                Facebook: 'bg-Facebook',
                Twitter: 'bg-Twitter',
                Instagram: 'bg-Instagram-gradient',
                YouTube: 'bg-YouTube'
            }
        }
    },
    mounted() {
    },
    methods:{
        getImagePath(network) {
            return require(`@/assets/images/icon-${network.toLowerCase()}.svg`);
        },
        getImagePathFlechas(arriba) {
            if (arriba)
                return require('@/assets/images/icon-up.svg');
            else
                return require('@/assets/images/icon-down.svg');            
        },
        convertNumberToK(numero){
            if (numero >= 10000){
                numero = numero / 1000
                return numero + 'K'
            }
            return numero
        }
    }
}
</script>