# Quiz
Quiz pertemuan 5 (genap)

<!DOCTYPE html>
<html>
  <head>
    <title>Isikan Nama dan Nim Anda, Contoh : Agus (101010102)</title>
    <style>
      body {
        font-family: Arial, Helvetica, sans-serif;
      }

      * {
        box-sizing: border-box;
      }

      input[type="text"],
      select,
      textarea {
        width: 100%;
        padding: 12px;
        border: 1px solid #ccc;
        border-radius: 4px;
        resize: vertical;
      }

      label {
        padding: 12px 12px 12px 0;
        display: inline-block;
      }

      input[type="submit"] {
        background-color: #aa7804;
        color: white;
        padding: 12px 20px;
        border: none;
        border-radius: 4px;
        cursor: pointer;
        float: right;
      }

      input[type="submit"]:hover {
        background-color: #aa7804;
      }

      .container {
        border-radius: 5px;
        background-color: #f2f2f2;
        padding: 20px;
      }

      .col-25 {
        float: left;
        width: 25%;
        margin-top: 6px;
      }

      .col-75 {
        float: left;
        width: 75%;
        margin-top: 6px;
      }

      /* Clear floats after the columns */
      .row::after {
        content: "";
        display: table;
        clear: both;
      }

      /* Responsive layout - when the screen is less than 600px wide, make the two columns stack on top of each other instead of next to each other */
      @media screen and (max-width: 600px) {
        .col-25,
        .col-75,
        input[type="submit"] {
          width: 100%;
          margin-top: 0;
        }
      }
    </style>
    <script>
      function tampilHasil() {
        // Mengambil nilai input dari formulir HTML
        var nama = document.getElementById("nama").value;
        var alamat = document.getElementById("alamatPemesan").value;
        var jenisKopi = document.getElementById("jenisKopi").value;
        var ukuran = document.querySelector('input[name="ukuran"]:checked').value;

        // Mendapatkan nilai checkbox makanan pelengkap yang dipilih
        var makananPelengkap = [];
        var checkboxes = document.querySelectorAll('input[name="makananPelengkap"]:checked');
        for (var i = 0; i < checkboxes.length; i++) {
          makananPelengkap.push(checkboxes[i].value);
        }

        // Menghitung harga kopi berdasarkan jenis kopi yang dipilih
        var hargaKopi = 0;
        switch (jenisKopi) {
          case "kopiarabika":
            hargaKopi = 10000;
            break;
          case "kopirobusta":
            hargaKopi = 15000;
            break;
          case "kopiliberika":
            hargaKopi = 20000;
            break;
          case "kopiekselsa":
            hargaKopi = 25000;
            break;
        }

        // Menghitung harga makanan pelengkap yang dipilih
        var hargaMakanan = 0;
        for (var j = 0; j < makananPelengkap.length; j++) {
          switch (makananPelengkap[j]) {
            case "Cake":
              hargaMakanan += 5000;
              break;
            case "Brownies":
              hargaMakanan += 10000;
              break;
            case "Dalgona Candy":
              hargaMakanan += 15000;
              break;
          }
        }

        // Menghitung total harga
        var totalHarga = hargaKopi + hargaMakanan;

        // Menambahkan simbol "Rp" di depan total harga
        var totalHargaDalamRupiah = "Rp " + totalHarga.toLocaleString();

        // Menampilkan hasil di elemen <p> dengan id "hasil"
        var hasilElement = document.getElementById("hasil");
        hasilElement.innerHTML =
          "Nama: " +
          nama +
          "<br>" +
          "Alamat: " +
          alamat +
          "<br>" +
          "Pesanan Jenis Kopi: " +
          jenisKopi +
          "<br>" +
          "Ukuran: " +
          ukuran +
          "<br>" +
          "Makanan Pelengkap: " +
          makananPelengkap.join(", ") +
          "<br>" +
          "Total: " +
          totalHargaDalamRupiah;
      }
    </script>
  </head>
  <body>
    <h2>Form Pemesanan Coffee</h2>

    <div class="container">
      <form>
        <div class="row">
          <div class="col-25">
            <label for="nama">Nama Lengkap Pemesan</label>
          </div>
          <div class="col-75">
            <input type="text" id="nama" name="nama" placeholder="Masukan Nama Anda ..." />
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="jenisKopi">Pilih Jenis Kopi</label>
          </div>
          <div class="col-75">
            <select id="jenisKopi" name="jenisKopi">
              <option value="kopiarabika">Kopi Arabika</option>
              <option value="kopirobusta">Kopi Robusta</option>
              <option value="kopiliberika">Kopi Liberika</option>
              <option value="kopiekselsa">Kopi Ekselsa</option>
            </select>
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="alamatPemesan">Alamat Pemesan</label>
          </div>
          <div class="col-75">
            <textarea id="alamatPemesan" name="alamatPemesan" placeholder="Alamat Pemesan.." style="height: 200px"></textarea>
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="ukuran">Ukuran</label>
          </div>
          <div class="col-25">
            <input type="radio" id="kecil" name="ukuran" value="Kecil" />
            <label for="kecil">Kecil</label><br />
            <input type="radio" id="sedang" name="ukuran" value="Sedang" />
            <label for="sedang">Sedang</label><br />
            <input type="radio" id="besar" name="ukuran" value="Besar" />
            <label for="besar">Besar</label>
          </div>
        </div>
        <div class="row">
          <div class="col-25">
            <label for="makananPelengkap">Makanan Pelengkap</label>
          </div>
          <div class="col-25">
            <input type="checkbox" id="makananPelengkap1" name="makananPelengkap" value="Cake" />
            <label for="makananPelengkap1"> Cake</label><br />
            <input type="checkbox" id="makananPelengkap2" name="makananPelengkap" value="Brownies" />
            <label for="makananPelengkap2"> Brownies</label><br />
            <input type="checkbox" id="makananPelengkap3" name="makananPelengkap" value="Dalgona Candy" />
            <label for="makananPelengkap3"> Dalgona Candy</label>
          </div>
        </div>
        <br />
        <div class="row">
          <input type="button" onClick="tampilHasil()" value="Simpan" />
        </div>
      </form>
    </div>

    <div class="row">
      <div class="col-100">
        <p id="hasil" name="hasil"></p>
      </div>
    </div>
  </body>
</html>
