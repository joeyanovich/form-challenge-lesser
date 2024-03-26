<script lang="ts">
  import Count from './Count.svelte';

  interface FormData {
    nome: string;
    telefone: string;
    email: string;
  }

  let formData: FormData = {
    nome: "",
    telefone: "",
    email: "",
  };

  let mostrarContador = false;

  function iniciarDesafio() {
    mostrarContador = true;
    // Iniciar o contador regressivo
  }
</script>

<form on:submit|preventDefault class={mostrarContador ? 'hidden' : ''}>
  <label for="nome">Nome:</label>
  <input type="text" id="nome" bind:value={formData.nome}>

  <label for="telefone">Telefone:</label>
  <input type="tel" id="telefone" bind:value={formData.telefone}>

  <label for="email">Email:</label>
  <input type="email" id="email" bind:value={formData.email}>

  <button type="submit" on:click={iniciarDesafio}>Iniciar Desafio</button>

  
</form>

{#if mostrarContador}
  <div class="flex flex-col items-center justify-center h-screen ">
    <Count />
  </div>
  {/if}
