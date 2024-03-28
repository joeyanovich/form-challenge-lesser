<script lang="ts">
	// import { onNavigate } from "$app/navigation";
	import Count from "./Count.svelte";
  // import { setCookie } from "@sveltejs/kit";
  // import { navigate } from "@sveltekit/app";
    interface FormData {
    name: string;
    phone: string;
    email: string;
  }

  let formData: FormData = {
    name: "",
    phone: "",
    email: "",
  };

  let showCount = false;

  

  function handleStartChallenge() {

    // formData.name = event.target.name.value;
    // formData.phone = event.target.phone.value;
    // formData.email = event.target.email.value;

    // setCookie("formData", JSON.stringify(formData));
    // localStorage.setItem("formData", JSON.stringify(formData));
    
  // event.preventDefault();

  

  if (formData.name === "" || formData.phone === "" || formData.email === "") {
    alert("Preencha todos os campos, por favor!");
    return;
  }

  showCount = true;
}
</script>

<main class="flex flex-col items-center justify-center px-10 h-screen">
  <form on:submit|preventDefault class="{showCount ? 'hidden' : ''} flex flex-col gap-3 w-96 max-w-full">
    <h1 class="text-center text-4xl font-bold mb-5 text-slate-600">Desafio</h1>
    
    <label class="w-full relative border-2 border-slate-400 rounded-lg">
      <p class={formData.name ? 'above' : 'center'}>Nome</p>
      <input
        bind:value={formData.name}
        class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
        type="text"
        placeholder="Nome"
        required
      >
    </label>
    <label class="w-full relative border-2 border-slate-400 rounded-lg">
      <p class={formData.phone ? 'above' : 'center'}>Telefone</p>
      <input
        bind:value={formData.phone}
        class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
        type="number"
        placeholder="Telefone"
        required
      >
    </label>
    <label class="w-full relative border-2 border-slate-400 rounded-lg">
      <p class={formData.email ? 'above' : 'center'}>Email</p>
      <input
        bind:value={formData.email}
        class="w-full p-3 bg-transparent border-none text-gray-500 focus:outline-none"
        type="email"
        placeholder="Email"
        required
      >
    </label>

    <button
      type="submit"
      class="py-3 border-none cursor-pointer rounded-lg text-white bg-slate-600 ease-in-out duration-500 hover:bg-slate-400"
      value="Iniciar Desafio"
      on:click={handleStartChallenge}
    >
      Iniciar Desafio
    </button>
  </form>

  {#if showCount}
  <div class="flex flex-col items-center justify-center h-screen ">
    <Count />
  </div>
  {/if}

</main>

<style>
  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  .above, .center {
    position: absolute;
    transform: translateY(-50%);
    padding: 0 0.5rem;
    pointer-events: none;
    border-radius: 4px;
    font-size: 0.8rem;

    transition: 0.4s ease-in-out;

    color: white;
  }

  .above {
    top: 0;
    left: 1rem;
    border: 1px solid #94a3b8;
    font-size: 0.75rem;

    background-color: #94a3b8;
  }

  .center {
    left: 0;
    border: 1px solid transparent;
    opacity: 0;
  }
</style>