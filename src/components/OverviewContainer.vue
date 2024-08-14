<template>
    <div>
        <section class="max-w-[1440px] flex flex-wrap gap-[30px] place-content-center absolute top-[191px] left-0 right-0">
            <div v-for="(item, index) in overviewItems" :key="index">
                
                <article class="bg-Light-Grayish-Blue-(Card-BG) dark:bg-Dark-Desaturated-Blue-(Card-BG) w-[326px] h-[216px] mb-8 rounded-[5px] mx-auto overflow-hidden text-center hover:brightness-95 cursor-pointer hover:dark:brightness-125">
                    
                    <div :class="`${networkColors[item.network]} h-1 mb-8`"></div>
                    
                    <div class="flex items-center place-content-center gap-2">
                        <img :src="getImagePath(item.network)" :alt="`logo ${item.network}`" />
                        <p class="text-xs text-Dark-Grayish-Blue-(Text) font-bold dark:text-White-(Text)">{{ item.user }}</p>
                    </div>
                    
                    <p class="text-[56px] font-bold text-Very-Dark-Blue-(Text) dark:text-White-(Text)">
                        {{ convertNumberToK(item.audience) }}
                    </p>

                    <p class="uppercase tracking-[5px] text-Dark-Grayish-Blue-(Text) text-xs mb-6">      
                        {{ item.audienceType }}
                    </p>
                    
                    <div class="flex items-center place-content-center gap-1">                    
                        <img :src="getImagePathFlechas(item.isUp)" alt="icon arrow"/>
                        <p :class="`text-xs font-bold ${item.isUp ? 'text-Lime-Green' : 'text-Bright-Red'}`">
                            {{ item.today }} Today
                        </p> 
                    </div>  
                </article>
            </div>
        </section>
    </div>
</template>

<script>

export default {
    props:['overviewItems'],
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