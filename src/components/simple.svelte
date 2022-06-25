<script>
  export let selectedCurrency = "$";
      export let amount = 0;
      // @ts-ignore
      export function onCurrencyChange(event) {
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
<div class="flex justify-center mb-6">
  <div class="mb-3 m-6">
    <label for="exampleFormControlInput1" class="text-lg form-label inline-block mb-2 text-gray-700"
      >Ingreso mensual</label>
    <div class="h-12">
      <label for="price" class="block text-sm font-medium text-gray-700">Price</label>
      <div class="mt-1 relative rounded-md shadow-sm h-11 w-fit">
        <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
          <span class="text-gray-500 sm:text-sm"> {selectedCurrency} </span>
        </div>
        <input bind:value={amount} type="text" name="price" id="price" class="focus:ring-teal-500 focus:border-teal-500 block w-full pl-7 pr-12 sm:text-sm border-gray-300 rounded-md h-11" placeholder="0.00">
        <div class="absolute inset-y-0 right-0 flex items-center">
          <label for="currency" class="sr-only">Currency</label>
          <select id="currency" on:change={onCurrencyChange} name="currency" class="focus:ring-teal-500 focus:border-teal-500 h-full py-0 pl-2 pr-7 border-transparent bg-transparent text-gray-500 sm:text-sm rounded-md">
            <option>USD</option>
            <option>CAD</option>
            <option>EUR</option>
          </select>
        </div>
      </div>
    </div>
    <br>
    <h5 class="text-gray-900 text-2xl leading-tight font-bold mb-2 mt-4">Tu resultado 50/30/20 son:</h5>
    <br>
    <div class="grid grid-cols-3 gap-6">
      <div>
        <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Necesidades</h5>
        <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .50}</h5>
      </div>
      <div>
        <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Gustos</h5>
        <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .30}</h5>
      </div>
      <div>
        <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Ahorros y deudas</h5>
        <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .20}</h5>
      </div>
    </div>
  </div>
</div>