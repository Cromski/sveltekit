<script lang="ts">

    let nums:[number, number]

    let userAnswerField:number = 0

    let calculations:string[] = []

    function generateRandomNumbers():void {
        let min:number = 1;
        let max:number = 100;
        nums = [Math.floor(Math.random() * (max - min + 1)) + min, Math.floor(Math.random() * (max - min + 1)) + min];
    }

    function updateNumbers():void {
        if(nums && (nums[0] + nums[1]) !== userAnswerField){
            return
        }
        generateRandomNumbers()
        calculations.push(`${nums[0]} + ${nums[1]} = ${userAnswerField}`)
        console.log(calculations)
        userAnswerField = 0;
        calculations = calculations; //apparently .push() doesnt "update" calculations
    }


    generateRandomNumbers()

</script>


<div class="relative">

    <h1 class=" text-center mt-11 text-xl">Here's an addition:</h1>
    
    <h1 class="text-center mt-6 text-xl">{nums[0]} + {nums[1]}</h1>

    <input bind:value={userAnswerField} type="number" class=" w-40 h-10 text-center inline-block text-2xl border-2 border-black rounded-md mt-7 ml-[50%] translate-x-[-50%]" >

    {#if (nums[0] + nums[1]) !== userAnswerField}
        <img class=" -translate-x-[70px] w-11 inline-block" src="/redcross.jpg" alt="">
    {:else}
        <img class=" -translate-x-[70px] w-11 inline-block" src="/checkmark.png" alt="">
    {/if}
    
    <button on:click={updateNumbers}  class=" w-32 h-10 text-center block text-2xl border-2 border-black rounded-md mt-5 mx-auto">Submit</button>
    
    
    <div class="absolute top-6 left-48">
        <h1 class=" text-xl font-bold">History</h1>

        {#each [...calculations].reverse() as calculation}
            <h1>{calculation}</h1>
        {/each}

    </div>
    

</div>