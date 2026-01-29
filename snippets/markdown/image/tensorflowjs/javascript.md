Learn more about how to use the code snippet on [github](https://github.com/googlecreativelab/teachablemachine-community/tree/master/libraries/image).

```html
<input type="text" id="sampah" placeholder="contoh: plastik">
<button onclick="deteksi()">Deteksi</button>

<p id="hasil"></p>

<script>
function deteksi() {
    let sampah = document.getElementById("sampah").value.toLowerCase();
    let hasil = document.getElementById("hasil");

    if (sampah.includes("daun") || sampah.includes("makanan")) {
        hasil.innerText = "🟢 Sampah ORGANIK";
    } 
    else if (sampah.includes("plastik") || sampah.includes("kaleng")) {
        hasil.innerText = "🔵 Sampah ANORGANIK";
    } 
    else if (sampah.includes("baterai")) {
        hasil.innerText = "🔴 Sampah B3";
    } 
    else {
        hasil.innerText = "❓ Tidak dikenali";
    }
}
</script>
