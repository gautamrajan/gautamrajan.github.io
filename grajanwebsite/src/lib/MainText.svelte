<script>
    import { onMount } from 'svelte';
    import resumeUrl from '../../public/files/gautam_rajan_resume.pdf'
    let blinking = false;
    let vis = true;
    let showLinks = true;
    let github_hover = false;
    let in_hover = false;
    let resume_hover = false;
    function typewriter(node, {speed = 1} ){
        const text = node.textContent;
        const duration = text.length/(speed*.01);
        return{
            duration,
            tick: (t) => {
                const i = Math.trunc(text.length*t);
                if(t==1){
                    node.textContent = text.slice(0,i);
                }
                else{
                    node.textContent = text.slice(0,i) + '|';
                }
            },
        }
    }
    function blink(node, {dur = 1.2 } ){
        const duration = dur*1000;
        return{
            duration,
            css: (t) =>{
                if(Math.trunc(t*duration)%6==0 && Math.trunc(t*duration)%8 == 0){
                    vis = !vis;
                    console.log("switch");
                }
                return `visibility: ${vis?'visible':'hidden'}`
            }
        }
    }
    onMount(()=>{
        blinking = true;
        setTimeout(()=>{
            blinking = false;

        },1200)
    })
    
</script> 

<h1 class="text-blue-500 text-7xl font-bold mt-6">Hi. Right now I'm:</h1>
{#if blinking}
<h1 in:blink class="text-gray-500 text-5xl mt-4">|</h1>
{:else}
<h2 in:typewriter class="text-gray-500 text-5xl mt-4">Working on this website</h2>
{/if}
{#if showLinks}
<div class="flex w-100 justify-center space-x-5 mt-8">
    <a title="LinkedIn" href="https://linkedin.com/in/gautamrajank"
        on:mouseover={()=>{in_hover=true}}
        on:mouseout={()=>{in_hover=false}}
        on:focus={()=>{in_hover=true}}
        on:blur={()=>{in_hover=false}}
    >
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" class="h-10 w-10 {in_hover?'fill-blue-500':''}">
            <!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
            <path d="M100.28 448H7.4V148.9h92.88zM53.79 108.1C24.09 108.1 0 83.5 0 53.8a53.79 53.79 0 0 1 107.58 0c0 29.7-24.1 54.3-53.79 54.3zM447.9 448h-92.68V302.4c0-34.7-.7-79.2-48.29-79.2-48.29 0-55.69 37.7-55.69 76.7V448h-92.78V148.9h89.08v40.8h1.3c12.4-23.5 42.69-48.3 87.88-48.3 94 0 111.28 61.9 111.28 142.3V448z"/>
        </svg>
    </a>
    <a title="GitHub" href="https://github.com/gautamrajan" 
        on:mouseover={()=>{github_hover=true}}
        on:mouseout={()=>{github_hover=false}}
        on:focus={()=>{github_hover=true}}
        on:blur={()=>{github_hover=false}}
        >
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512" class="h-10 w-10 {github_hover?'fill-blue-500':''}">
            <path d="M165.9 397.4c0 2-2.3 3.6-5.2 3.6-3.3.3-5.6-1.3-5.6-3.6 0-2 2.3-3.6 5.2-3.6 3-.3 5.6 1.3 5.6 3.6zm-31.1-4.5c-.7 2 1.3 4.3 4.3 4.9 2.6 1 5.6 0 6.2-2s-1.3-4.3-4.3-5.2c-2.6-.7-5.5.3-6.2 2.3zm44.2-1.7c-2.9.7-4.9 2.6-4.6 4.9.3 2 2.9 3.3 5.9 2.6 2.9-.7 4.9-2.6 4.6-4.6-.3-1.9-3-3.2-5.9-2.9zM244.8 8C106.1 8 0 113.3 0 252c0 110.9 69.8 205.8 169.5 239.2 12.8 2.3 17.3-5.6 17.3-12.1 0-6.2-.3-40.4-.3-61.4 0 0-70 15-84.7-29.8 0 0-11.4-29.1-27.8-36.6 0 0-22.9-15.7 1.6-15.4 0 0 24.9 2 38.6 25.8 21.9 38.6 58.6 27.5 72.9 20.9 2.3-16 8.8-27.1 16-33.7-55.9-6.2-112.3-14.3-112.3-110.5 0-27.5 7.6-41.3 23.6-58.9-2.6-6.5-11.1-33.3 2.6-67.9 20.9-6.5 69 27 69 27 20-5.6 41.5-8.5 62.8-8.5s42.8 2.9 62.8 8.5c0 0 48.1-33.6 69-27 13.7 34.7 5.2 61.4 2.6 67.9 16 17.7 25.8 31.5 25.8 58.9 0 96.5-58.9 104.2-114.8 110.5 9.2 7.9 17 22.9 17 46.4 0 33.7-.3 75.4-.3 83.6 0 6.5 4.6 14.4 17.3 12.1C428.2 457.8 496 362.9 496 252 496 113.3 383.5 8 244.8 8zM97.2 352.9c-1.3 1-1 3.3.7 5.2 1.6 1.6 3.9 2.3 5.2 1 1.3-1 1-3.3-.7-5.2-1.6-1.6-3.9-2.3-5.2-1zm-10.8-8.1c-.7 1.3.3 2.9 2.3 3.9 1.6 1 3.6.7 4.3-.7.7-1.3-.3-2.9-2.3-3.9-2-.6-3.6-.3-4.3.7zm32.4 35.6c-1.6 1.3-1 4.3 1.3 6.2 2.3 2.3 5.2 2.6 6.5 1 1.3-1.3.7-4.3-1.3-6.2-2.2-2.3-5.2-2.6-6.5-1zm-11.4-14.7c-1.6 1-1.6 3.6 0 5.9 1.6 2.3 4.3 3.3 5.6 2.3 1.6-1.3 1.6-3.9 0-6.2-1.4-2.3-4-3.3-5.6-2z"/>
        </svg>
    </a>
    <a title="Resume" href={resumeUrl}
        on:mouseover={()=>{resume_hover=true}}
        on:mouseout={()=>{resume_hover=false}}
        on:focus={()=>{resume_hover=true}}
        on:blur={()=>{resume_hover=false}}
        >
        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 384 512" class="h-10 w-10 {resume_hover?'fill-blue-500':''}">
            <!--! Font Awesome Pro 6.0.0 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license (Commercial License) Copyright 2022 Fonticons, Inc. -->
            <path d="M336 0h-288C21.49 0 0 21.49 0 48v416C0 490.5 21.49 512 48 512h288c26.51 0 48-21.49 48-48v-416C384 21.49 362.5 0 336 0zM192 160c35.35 0 64 28.65 64 64s-28.65 64-64 64S128 259.3 128 224S156.7 160 192 160zM288 416H96c-8.836 0-16-7.164-16-16C80 355.8 115.8 320 160 320h64c44.18 0 80 35.82 80 80C304 408.8 296.8 416 288 416zM240 96h-96C135.2 96 128 88.84 128 80S135.2 64 144 64h96C248.8 64 256 71.16 256 80S248.8 96 240 96z"/>
        </svg>
    </a>
</div>
{/if}