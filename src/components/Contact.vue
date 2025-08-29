<template>
    <div class="text-white flex h-4/5 items-center justify-center">
        <div class="card p-5 border rounded-3xl flex flex-col justify-center items-center h-3/4">
            <h1 class="font-Conthrax text-3xl">Tarjeta de Contacto</h1>
            <div class="flex">
                <img src="/images/Photo.png" alt="Imagen del contacto" class="w-50 object-cover mask-b-from-85%"/>
            <div class="font-Quantico text-lg flex flex-col h-full justify-center ml-10">
                
                <div class="mt-8">
                    <p><strong class="font-Conthrax">Nombre:</strong> Andersson Ibarra</p>
                    <p><strong class="font-Conthrax">Email:</strong> ibarram0723@gmail.com</p>
                    <p><strong class="font-Conthrax">Teléfono:</strong> +57 3112508664</p>
                    <p><strong class="font-Conthrax">Ciudad:</strong> Neiva, Huila - Colombia</p>
                </div>
                <div class="mt-8 flex w-full justify-center gap-5">
                    <a href="https://www.linkedin.com/in/andersson-stiven-ibarra-mora-41a60923b" target="_blank" class="hover:scale-105 transition-transform duration-200">
                        <div v-html="LogoLinkedIn" class="logos w-13 h-13"></div>
                    </a>
                    <a href="https://github.com/AnderssonIbarra" target="_blank" class="hover:scale-105 transition-transform duration-200">
                        <div v-html="LogoGithub" class="logos w-13 h-13"></div>
                    </a>
                    <a href="mailto:ibarram0723@gmail.com" target="_blank" class="hover:scale-105 transition-transform duration-200">
                        <div v-html="LogoGmail" class="logos w-13 h-13"></div>
                    </a>
                </div>
            </div>
            </div>
            
        </div>
    </div>
</template>

<script>
import LogoGithub from '@/assets/icons/github.svg?raw'
import LogoLinkedIn from '@/assets/icons/linkedin.svg?raw'
import LogoGmail from '@/assets/icons/gmail.svg?raw'

import gsap from 'gsap'

export default {
    name: "Contact",
    data(){
        return {
            LogoGithub,
            LogoLinkedIn,
            LogoGmail
        }
    },
    methods: {
        animationCard(){
            gsap.from(".card", {
                y: -50,
                opacity: 0,
                duration: 1,
            })
        }
    },
    mounted(){
        this.animationCard()
    }
}
</script>

<style>
    .logos svg{
        width: 100%;
        height: 100%;
    }
</style>