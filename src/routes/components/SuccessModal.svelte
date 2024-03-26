<script>
  export let isOpen = false;

  function closeModal() {
    isOpen = false;
    window.location.href = "/congratulation";
  }
</script>

<div class="modal" class:modal-open={isOpen}>
  <!-- <div class="modal-box"> -->
  <div class="relative flex flex-col p-10 rounded-2xl gap-20 bg-green-700 text-white">
    <h3 class="font-bold uppercase text-center text-5xl">Parabéns</h3>
    <p class="text-3xl">Desafio finalizado com sucesso!</p>
    <button class="btn btn-sm btn-circle btn-ghost absolute right-2 top-2" on:click={closeModal}>✕</button>
  </div>
</div>