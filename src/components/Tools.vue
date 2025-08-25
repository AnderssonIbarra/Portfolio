<template>
    <div class="tools-container text-white w-full flex flex-col justify-center items-center">
        <h2 id="tools-title" class="text-2xl font-Conthrax font-bold mb-4">Herramientas</h2>
        <div class="flex justify-between w-9/10 gap-2">
            <div v-for="tool in tools" :id="'tool-' + tool.id" :key="tool.id" class="p-2 flex flex-col items-center">
                <div v-html="tool.logo" class="logos w-15 h-15 mb-1"></div>
                <h3 class="text-lg font-Quantico">{{ tool.name }}</h3>
            </div>
        </div>
    </div>
</template>

<script>
import gsap from "gsap";
import { SplitText } from "gsap/SplitText";
import { ScrambleTextPlugin } from 'gsap/ScrambleTextPlugin';

import LogoAstro from '@/assets/icons/astro.svg?raw'
import LogoVue from '@/assets/icons/vuejs.svg?raw'
import LogoReact from '@/assets/icons/react.svg?raw'
import LogoCSS from '@/assets/icons/css3.svg?raw'
import LogoGithub from '@/assets/icons/github.svg?raw'
import LogoJavaScript from '@/assets/icons/javascript.svg?raw'
import LogoHtml5 from '@/assets/icons/html.svg?raw'

gsap.registerPlugin(SplitText, ScrambleTextPlugin);

export default {
    name: 'Tools',
    data(){
        return {
            tools: [
                { id: 1, name: 'Astro', logo: LogoAstro},
                { id: 2, name: 'Vue', logo: LogoVue},
                { id: 3, name: 'React', logo: LogoReact},
                { id: 4, name: 'CSS', logo: LogoCSS},
                { id: 5, name: 'Github', logo: LogoGithub},
                { id: 6, name: 'JavaScript', logo: LogoJavaScript},
                { id: 7, name: 'Html5', logo: LogoHtml5},
            ],
            BASE: import.meta.env.VITE_BASE_URL,
        }
    },
    mounted(){
        this.animateTools();
    },
    methods: {
        
        //Animación de los Tools y el titulo
        animateTools() {
            const tl = gsap.timeline();
            const toolTitle = document.getElementById("tools-title");
            const splitTitle = new SplitText(toolTitle, { type: "chars" });
            const lengthTools = this.tools.length;

            tl.from(splitTitle.chars, {
                scrambleText:{
                    text: toolTitle.innerText,
                    chars: "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%^&*()",
                    speed: 0.5,
                    revealDelay: 0.5,
                },
                opacity: 0,
                duration: 0.3,
                stagger: 0.05,
                ease: "power1.out",
            });
            this.tools.forEach((tool, index) => {
                const toolElement = document.getElementById(`tool-${tool.id}`);
                tl.from(toolElement, {
                    opacity: 0,
                    y: 20,
                    duration: 0.3,
                    ease: "power1.out",
                    onComplete: () => {
                        if(lengthTools === index + 1) {
                            this.$emit("animationToolsComplete", true);
                        }
                    }
                }, ">");
            });
            
        },
    }
}
</script>

<style>
    .logos svg{
        width: 100%;
        height: 100%;
    }
</style>