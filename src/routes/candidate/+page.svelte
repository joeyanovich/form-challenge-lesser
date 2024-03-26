<script lang="ts">
  import type { FormData } from "../../types/types";
  import { onMount } from "svelte";

  let formData: FormData | null = null;

  onMount(() => {
    const storedData = localStorage.getItem("formData");
    if (storedData) {
      formData = JSON.parse(storedData) as FormData;
    }
  });
</script>

<p>Nome: {formData?.name}</p>
<p>Telefone: {formData?.phone}</p>
<p>Email: {formData?.email}</p>