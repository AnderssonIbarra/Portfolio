<template>
    <div class="flex text-white w-full h-full justify-center content-center">
        <ul class="contenido flex flex-col max-w-9/10 h-8/10 overflow-y-auto overflow-x-hidden px-5">
            <li v-for="project in projects" :key="project.id" class="mb-4 p-4 font-Quantico flex hover:scale-105 transition-transform duration-300">
                <img :src="project.image" :alt="'imagen de ' + project.name" class="rounded-lg shadow-lg h-30 grayscale" />
                <div class="ml-4">
                    <h3 class="text-xl font-Conthrax">{{ project.name }}</h3>
                    <p class="text-sm">{{ project.description }}</p>
                    <p class="text-sm"><strong>Trabajo: </strong> {{ project.job }}</p>
                    <p class="text-sm"><strong>Tecnología: </strong> {{ project.technology.join(', ') }}</p>
                    <a :href="project.link" class="font-bold underline hover:opacity-80" target="_blank">Ver proyecto</a>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
import gsap from 'gsap';

export default {
    name: "MyProjects",
    data(){
        return {
            projects: [
                {
                    id: 1,
                    name: "Conexiones Empresariales S.A.S",
                    description: "Conexiones Empresariales es una empresa de correspondencia a nivel de Colombia.",
                    job: "Encargado del diseño y desarrollo de la pagina web.",
                    technology: ["Astro", "Tailwind CSS", "JavaScript"],
                    image: './projects/proyecto1.png',
                    link: "https://www.conexionesempresariales.com"
                },
                {
                    id: 2,
                    name: "PROCIEM S.A.S",
                    description: "PROCIEM S.A.S es una colombiana con servicios de construcción y mantenimiento en obras de ingeniería civil.",
                    job: "Creación y desarrollo de la página web.",
                    technology: ["Astro", "Tailwind CSS", "JavaScript"],
                    image: './projects/proyecto2.png',
                    link: "https://www.prociemsas.com"
                },
                {
                    id: 3,
                    name: "OMEC S.A.S",
                    description: "OMEC S.A.S es una del Meta en Colombia, con alta experiencia en obras de ingeniería civil, metalmecánicas, y electromecánicas",
                    job: "Creación y desarrollo de la página web.",
                    technology: ["Astro", "Tailwind CSS", "JavaScript"],
                    image: './projects/proyecto3.png',
                    link: "https://www.omecsascompany.com"
                },
                {
                    id: 4,
                    name: "Cerro Alto S.A.S",
                    description: "Cerro alto S.A.S es una compañía huilense dedicada a la exploración, explotación, transformación, transporte y comercialización de agregados pétreos y minerales.",
                    job: "Creación y desarrollo de la página web.",
                    technology: ["Astro", "Tailwind CSS", "JavaScript"],
                    image: './projects/proyecto4.png',
                    link: "https://www.cerroaltosas.com"
                },
            ]
        }
    },
    mounted(){
        this.animationProjects();
    },
    methods: {
        animationProjects(){
            const tl = gsap.timeline();
            const elementos = document.querySelectorAll('.contenido li');

            gsap.from(elementos, {
                opacity: 0,
                duration: 1.5,
                stagger: 0.3,
                ease: "power2.out"
            });
        }
    }
}
</script>

<style>
.contenido {
    scrollbar-width: none;  /* Firefox */
    -ms-overflow-style: none;  /* Internet Explorer and Edge */
}
.contenido::-webkit-scrollbar {
    display: none;  /* Safari and Chrome */
}
</style>