<script>
    import { ethers } from "ethers";
import { onMount } from "svelte";

    let blockNumber;
    onMount(async () => {
        const provider = new ethers.providers.Web3Provider(window.ethereum)
        // const provider = new ethers.providers.JsonRpcProvider();
        const signer = provider.getSigner()
        blockNumber = await provider.getBlockNumber()
    });
    
</script>

<div class="navbar mb-2 shadow-lg bg-neutral text-neutral-content rounded-box">

    <div class="flex-none">
      <button class="btn btn-square btn-ghost">
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" class="inline-block w-6 h-6 stroke-current">           
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>               
        </svg>
      </button>
    </div> 

    <div class="flex-1 px-2 mx-2">
      <span class="text-lg font-bold">
            Tools
        </span>
    </div> 

    {#if blockNumber > 0}
    <div class="flex-1 px-2 mx-2">
      <span class="text-lg font-bold">
            Blocknumber: {blockNumber}
        </span>
    </div> 
    {:else}
    <div class="flex-1 px-2 mx-2">
      <span class="text-lg font-bold">
            Blocknumber: loading..
        </span>
    </div> 
    {/if}

    <div class="flex-none">
        <button class="p-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 10h18M7 15h1m4 0h1m-7 4h12a3 3 0 003-3V8a3 3 0 00-3-3H6a3 3 0 00-3 3v8a3 3 0 003 3z" />
              </svg>
        </button>
      </div>
  </div>
  
