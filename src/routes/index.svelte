<script>
      let selectedCurrency = "$";
      let amount = 0;
      let Detailedmode = true;
      function changeMode() {
        Detailedmode = !Detailedmode;
      }
      import Detailed from "../components/detailed.svelte";
      import Simple from "../components/simple.svelte";
      // @ts-ignore
      function onCurrencyChange(event) {
        const currency = event.target.value;
        console.log(currency);
        if (currency == "USD") {
            selectedCurrency = "$";
        }
        else if(currency == "CAD"){
          selectedCurrency = "C$";
        }
        else if(currency == "EUR"){
          selectedCurrency = "€";
        }
      };
</script>
  <div class="flex justify-left m-6" style="justify-content:center">
    <div class="block p-6 rounded-lg shadow-lg bg-white max-w-4xl border-t-4 border-t-teal-600 w-full">
      {#if !Detailedmode}
      <h5 class="text-gray-900 text-3xl leading-tight font-medium mb-2"><strong>Calculadora 50/30/20</strong></h5>
      {:else}
      <h5 class="text-gray-900 text-3xl leading-tight font-medium mb-2"><strong>Calculadora detallada</strong></h5>
      {/if}
      <p class="text-lg">Añada su ingreso mensual en la caja de texto</p>
      <br>
      <hr class="solid" style="border-top: 0.5px solid #bbb;">
      {#if Detailedmode }
      <Detailed></Detailed>
      {:else}
      <Simple></Simple>
      {/if}
      <div class="rounded-md w-28 shadow mx-auto">
        {#if Detailedmode }
        <a href="/" on:click={changeMode} class="w-full flex items-center justify-center px-8 py-3 border border-transparent text-base font-medium rounded-md text-white bg-teal-600 hover:bg-teal-700 md:py-4 md:text-lg md:px-10">Simple </a>
        {:else}
        <a href="/" on:click={changeMode} class="w-full flex items-center justify-center px-8 py-3 border border-transparent text-base font-medium rounded-md text-white bg-teal-600 hover:bg-teal-700 md:py-4 md:text-lg md:px-10">Detailed </a>
        {/if}
      </div>
    </div>
  </div>