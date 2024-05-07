<template>
  <div id="app">
    <header>
      <div class="logo-container">
        <img src="./src/assets/Logo.png" alt="Cafe R" class="logo">
      </div>
      <h1>Welcome to Cafe R</h1>
    </header>
    <nav>
      <a href="#">Home</a>
      <a href="#">Menu</a>
      <a href="#">Locations</a>
      <a href="#">Contact</a>
    </nav>
    <div class="form-container">
      <div>
        <p>From Reservasi Cafe</p>
        <input type="text" v-model="nama" :style="{ 'background-color': buttonBackgroundColor }" @blur="updateText('nama')" placeholder="Nama">
        <p class="input-info">Panjang maksimum teks: 10 teks</p>
        <p>Nilai input teks: <span :class="{ 'red-text': isRedNama }">{{ nama | capitalize }}</span></p>
      </div>
      <div>
        <input type="text" v-model="nomorTelepon" :style="{ 'background-color': buttonBackgroundColor }" @blur="updateText('nomorTelepon')" placeholder="Nomor Telepon (12 digit)">
        <p class="input-info">Panjang maksimum teks: 12 digit</p>
        <p>Nilai input teks: <span :class="{ 'red-text': isRedNomorTelepon }">{{ nomorTelepon }}</span></p>
      </div>
      <div>
        <input type="date" v-model="tanggalPesanan" :style="{ 'background-color': buttonBackgroundColor }" @blur="updateText('tanggalPesanan')" placeholder="Tanggal Pesanan">
        <p class="input-info">Tanggal Pesanan</p>
        <p>Nilai input tanggal: <span>{{ tanggalPesanan }}</span></p>
      </div>
      <button :style="{ 'background-color': buttonBackgroundColor }" @click="changeColor">Ubah Warna Latar Belakang Tombol</button>
    </div>
    <footer>
      <p>&copy; 2024 RIZIA UMAMI AYMAN All rights reserved.</p>
    </footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nama: '',
      nomorTelepon: '',
      tanggalPesanan: '',
      isRedNama: false,
      isRedNomorTelepon: false,
      buttonBackgroundColor: '#3498db',
    };
  },
  methods: {
    updateText(field) {
      if (field === 'nama') {
        this.isRedNama = this[field].length > 10;
      } else if (field === 'nomorTelepon') {
        this.isRedNomorTelepon = this[field].length !== 12;
      }
    },
    changeColor() {
      this.buttonBackgroundColor = 'white';
    },
  },
  filters: {
    capitalize(value) {
      if (!value) return '';
      value = value.toString();
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
};
</script>

<style>
/* CSS untuk tata letak halaman */

body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #333; /* Mengatur latar belakang tubuh menjadi abu-abu hitam monokrom */
}

header {
  background-color: #DD2127;
  color: white;
  padding: 10px 0;
  text-align: center;
}

nav {
  background-color: #222;
  color: white;
  text-align: center;
  padding: 10px 0;
}

nav a {
  color: white;
  text-decoration: none;
  padding: 0 20px;
}

.logo-container {
  vertical-align: middle;
  float: left;
}

.logo {
  height: 50px;
}

section {
  padding: 20px;
}

footer {
  background-color: #222;
  color: white;
  text-align: center;
  padding: 10px 0;
  position: fixed;
  bottom: 0;
  width: 100%;
}
/* CSS untuk gambar */

.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
/* CSS untuk form container */

.form-container {
  background-color: rgba(248, 248, 248, 0.8); /* Semi-transparent white background */
  padding: 5px;
  border-radius: 10px;
  max-width: 400px;
  text-align: center;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1); /* Tambahkan bayangan pada kontainer formulir */
  margin: 20px auto; /* center form-container horizontally */
}

.red-text {
  color: red;
}
</style>
