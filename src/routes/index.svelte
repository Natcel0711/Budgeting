<script>
      let selectedCurrency = "$";
      let amount = 0;

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
    <div class="block p-6 rounded-lg shadow-lg bg-white max-w-xl border-t-4 border-t-teal-600 w-full">
      <h5 class="text-gray-900 text-3xl leading-tight font-medium mb-2"><strong>Calculadora 50/30/20</strong></h5>
      <p class="text-lg">Añada su ingreso mensual en la caja de texto</p>
      <br>
      <hr class="solid" style="border-top: 0.5px solid #bbb;">
      <div class="flex justify-left">
        <div class="mb-3 xl:w-96 m-6">
          <label for="exampleFormControlInput1" class="text-lg form-label inline-block mb-2 text-gray-700"
            >Ingreso mensual</label>
          <div class="h-12">
            <label for="price" class="block text-sm font-medium text-gray-700">Price</label>
            <div class="mt-1 relative rounded-md shadow-sm h-11">
              <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
                <span class="text-gray-500 sm:text-sm"> {selectedCurrency} </span>
              </div>
              <input bind:value={amount} type="text" name="price" id="price" class="focus:ring-indigo-500 focus:border-indigo-500 block w-full pl-7 pr-12 sm:text-sm border-gray-300 rounded-md h-11" placeholder="0.00">
              <div class="absolute inset-y-0 right-0 flex items-center">
                <label for="currency" class="sr-only">Currency</label>
                <select id="currency" on:change={onCurrencyChange} name="currency" class="focus:ring-indigo-500 focus:border-indigo-500 h-full py-0 pl-2 pr-7 border-transparent bg-transparent text-gray-500 sm:text-sm rounded-md">
                  <option>USD</option>
                  <option>CAD</option>
                  <option>EUR</option>
                </select>
              </div>
            </div>
          </div>
          <br>
          <h5 class="text-gray-900 text-2xl leading-tight font-bold mb-2">Tu resultado 50/30/20 son:</h5>
          <br>
          <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Necesidades</h5>
          <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .50}</h5>
          <br>
          <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Gustos</h5>
          <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .30}</h5>
          <br>
          <h5 class="text-gray-900 text-3xl leading-tight font-bold mb-2">Ahorros y deudas</h5>
          <h5 class="text-teal-600 text-2xl leading-tight font-bold mb-2">{selectedCurrency}{amount * .20}</h5>
        </div>
      </div>
    </div>
  </div>