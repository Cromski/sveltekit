<script lang="ts">
    export let name:string
    export let routePath:string
    export let imgPath:string
</script>

<div class=" w-80 h-[500px] relative overflow-hidden"> 
    <a href={`${routePath}`}>
        <h1 class=" w-full text-3xl text-center font-bold text-slate-200 bg-slate-900 ">{name}</h1>
        <div style={`background-image: url('${imgPath}')`} class={`h-full w-[872px] absolute left-[50%] translate-x-[-50%] bg-contain `}  > 
            <!-- inline styling because tailwind cant take dynamic content -.- otherwise would be (only works when saved in cache): bg-[url('${imgPath}')] -->
            
        </div>
        
    </a>
</div>
