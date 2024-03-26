<script lang="ts">
  import { onMount } from "svelte";
  import SuccessModal from "./SuccessModal.svelte";
  import TimeOutModal from "./TimeOutModal.svelte"; 

  let remainingSeconds = 15;
  let interval: number;
  let minutes: number;
  let seconds: number;
  let isFinished = false;

  let showTimeOutModal = false;
  let showSuccessModal = false;

  export let isOpen = false;

  function handleCandidatePage() {
    isOpen = false;
    window.location.href = "/candidate";
  }

  function attCount() {
    if (isFinished) return

    remainingSeconds--;

    minutes = Math.floor(remainingSeconds / 60);
    seconds = remainingSeconds % 60;

    if (remainingSeconds === 0) {
      clearInterval(interval);
      isFinished = true;
      showTimeOutModal = true;
    }
  }

  function handleFinish() {
    isFinished = true;
    showSuccessModal = true;
  }

  onMount(() => {
    interval = setInterval(attCount, 1000);
  });
</script>

<button on:click={handleCandidatePage} class="absolute rounded-2xl p-4 right-5 top-5 text-white bg-slate-600 ease-in-out duration-500 hover:bg-slate-400">
  Candidato
</button>


<h1 class="uppercase text-4xl font-bold mb-5 text-slate-600">Contador Regressivo</h1>
<p class="text-9xl font-bold text-purple-500">00:{remainingSeconds.toString().padStart(2, "0")}</p>

<button class="button text-xl mt-10 rounded-2xl py-4 px-14 text-white bg-green-600 ease-in-out duration-600 hover:bg-green-500" on:click={handleFinish}>Finalizar Desafio</button>

{#if showTimeOutModal}
  <TimeOutModal isOpen={showTimeOutModal} />
{/if}
{#if showSuccessModal} 
  <SuccessModal isOpen={showSuccessModal} />
{/if}


