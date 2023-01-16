<script>
  let baseAmount = 0;
  let CGST = 9;
  let SGST = 9;
  let finalAmount = 0;

  function calculateBaseAmount() {
    if (!finalAmount || finalAmount < 0) {
      return;
    }
    baseAmount = Math.round(finalAmount / (1 + (CGST/100) + (SGST/100)));
  }

  function calculateFinalAmount() {
    if(!baseAmount || baseAmount < 0) {
      return;
    }
    finalAmount = Math.round(baseAmount + (baseAmount * (CGST/100)) + (baseAmount * (SGST/100)));
  }
</script>

<main>
  <div>
    <label for="base">Base Amount</label>
    <input bind:value={baseAmount} type="number" placeholder="Base" id="base">
  </div>

  <div>
    <label for="cgst">
    CGST
    </label>
    <input bind:value={CGST} type="number" placeholder="CGST" id="cgst">
  </div>

  <div>
    <label for="sgst">SGST</label>
    <input bind:value={SGST} type="number" placeholder="SGST" id="sgst">
  </div>


  <div>
    <label for="final">Final</label>
    <input bind:value={finalAmount} type="number" placeholder="Final" id="final">
  </div>

  <div >
    <button on:click={calculateFinalAmount}>Calculate final</button>
    <button on:click={calculateBaseAmount}>Calculate Base</button>
  </div>
</main>

<style>

</style>
