<script>
  let pilihan = "";
  let bb, tb_imt, tb_bb;
  let hasil = "";

  function hitungIMT() {
    const imt = bb / (tb_imt * tb_imt);
    let kategori = "";

    if (imt < 18.5) kategori = "Kurus";
    else if (imt < 25) kategori = "Normal";
    else if (imt < 30) kategori = "Gemuk";
    else kategori = "Obesitas";

    hasil = `IMT: ${imt.toFixed(2)} (${kategori})`;
  }

  function hitungBBIdeal() {
    const bbIdeal = (tb_bb - 100) * 0.9;
    hasil = `BB Ideal: ${bbIdeal.toFixed(1)} kg`;
  }
</script>

<h1>Perhitungan IMT dan BB Ideal</h1>

<select bind:value={pilihan}>
  <option value="">-- Pilih Perhitungan --</option>
  <option value="imt">Hitung IMT</option>
  <option value="bbIdeal">Hitung BB Ideal</option>
</select>

{#if pilihan === "imt"}
  <div>
    <input type="number" bind:value={bb} placeholder="Berat badan (kg)" />
    <input type="number" bind:value={tb_imt} placeholder="Tinggi badan (m)" />
    <button on:click={hitungIMT}>Hitung IMT</button>
  </div>
{/if}

{#if pilihan === "bbIdeal"}
  <div>
    <input type="number" bind:value={tb_bb} placeholder="Tinggi badan (cm)" />
    <button on:click={hitungBBIdeal}>Hitung BB Ideal</button>
  </div>
{/if}

<p id="hasil">{hasil}</p>

<style>
  body {
    font-family: Arial, sans-serif;
    background: #f5f7fa;
    padding: 40px;
    display: block;
    margin: auto;
  }

  h1 {
    text-align: center;
    color: #333;
  }

  select {
    display: block;
    margin: 20px auto;
    padding: 10px;
    width: 220px;
    border-radius: 6px;
    border: 1px solid #ccc;
  }

  div {
    background: white;
    max-width: 320px;
    margin: 20px auto;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  }

  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 12px;
    border-radius: 6px;
    border: 1px solid #ccc;
  }

  button {
    width: 100%;
    padding: 10px;
    background: #4f46e5;
    color: white;
    border: none;
    border-radius: 6px;
    font-weight: bold;
    cursor: pointer;
  }

  button:hover {
    background: #4338ca;
  }

  #hasil {
    text-align: center;
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
    color: #111;
  }
</style>
