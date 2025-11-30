<template>
  <div class="bg-blue-500 mx-auto py-10">
    <div class="text-center">
      <h1 class="text-white font-black text-3xl lg:text-5xl">
        Mitra Usaha Franchise Mandiri Supplier
      </h1>
      <p class="text-white text-base lg:text-xl mt-2">
        Usaha Kebutuhan Pokok Terjangkau
      </p>
    </div>
  </div>
  <div class="mx-auto py-10">
    <div class="">
      <div class="text-center mb-10">
        <h1 class="text-slate-950 font-black text-2xl lg:text-4xl">
          Franchise Mandiri Supplier
        </h1>
        <p class="text-slate-950 text-base lg:text-xl mt-2">
          Starter Pack Mandiri Supplier - harga
          <span class="font-black text-blue-500 lg:text-3xl">5 Juta</span> anda
          bisa dapetin system dibawah
        </p>
      </div>

      <img :src="franchise_image" alt="franchise-image" class="mx-auto px-4" />
    </div>

    <div class="p-9">
      <!-- pilihan paket -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-5xl mx-auto">
        <!-- Paket A -->
        <div
          class="bg-blue-500 rounded-2xl shadow p-6 relative transition-all duration-300 hover:-translate-y-2 hover:shadow-xl"
        >
          <img
            :src="paket_A"
            alt="Paket A"
            class="w-fit object-contain rounded-xl mb-4"
          />

          <h2 class="text-xl font-bold text-yellow-300 mb-2">Paket A</h2>
          <p class="text-white text-sm mb-4">
            Solusi praktis untuk kebutuhan dapur sehari-hari
          </p>

          <ul class="text-white space-y-1">
            <li>✔ Minyak Saudara 800ML</li>
            <li>✔ Beras Rojolele 1KG</li>
            <li>✔ Gulaku 500GR</li>
          </ul>
        </div>

        <!-- Paket B -->
        <div
          class="bg-blue-500 rounded-2xl shadow p-6 relative transition-all duration-300 hover:-translate-y-2 hover:shadow-xl"
        >
          <img
            :src="paket_B"
            alt="Paket B"
            class="w-fit object-contain rounded-xl mb-4"
          />

          <h2 class="text-xl text-yellow-300 font-bold mb-2">Paket B</h2>
          <p class="text-white text-sm mb-4">
            Pilihan terbaik untuk stock dan banyak keperluan
          </p>

          <ul class="text-white space-y-1 mb-6">
            <li>✔ Minyak Saudara 1LTR</li>
            <li>✔ Beras Rojolele 5KG</li>
            <li>✔ Gulaku 500GR</li>
          </ul>
        </div>
      </div>

      <!-- nama, nohp, alamat (kelurahan),  -->
    </div>
    <!-- buat container form biru disini minimalis isi dengan field nama, no telepon, alamat, -->
  </div>
  <div class="bg-blue-500 py-10 px-4">
    <div class="max-w-4xl mx-auto bg-white rounded-2xl shadow p-8">
      <h2 class="text-2xl font-black text-blue-600 text-center mb-6">
        Mitra Franchise
      </h2>

      <form class="space-y-5" @submit.prevent="submitFranchise">
        <!-- Nama -->
        <input
          v-model="nama"
          type="text"
          placeholder="Nama lengkap"
          class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
        />

        <!-- Telepon -->
        <input
          v-model="telepon"
          type="text"
          placeholder="08xxxxxxxxx"
          class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
        />

        <!-- Alamat -->
        <input
          v-model="alamat"
          type="text"
          placeholder="Masukkan alamat / kelurahan"
          class="w-full px-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
        />

        <!-- Tombol -->
        <button
          type="submit"
          class="w-full bg-blue-500 text-white font-bold py-3 rounded-xl hover:bg-blue-600 transition"
        >
          Gabung Mitra
        </button>
      </form>
    </div>
  </div>
</template>

<script setup>
import paket_A from "../assets/A.jpg";
import paket_B from "../assets/B.jpg";
import franchise_image from "../assets/image-franchise.png";
import { ref } from "vue";

import { supabase } from "../supabase";

const nama = ref("");
const telepon = ref("");
const alamat = ref("");

const submitFranchise = async () => {
  if (!nama.value.trim()) {
    return Swal.fire({ icon: "error", title: "Nama wajib diisi" });
  }
  if (!telepon.value.trim()) {
    return Swal.fire({ icon: "error", title: "Nomor telepon wajib diisi" });
  }
  if (!alamat.value.trim()) {
    return Swal.fire({ icon: "error", title: "Alamat wajib diisi" });
  }

  const { error } = await supabase.from("tbl_franchise").insert([
    {
      nama: nama.value,
      telepon: telepon.value,
      alamat: alamat.value,
    },
  ]);

  if (error) {
    console.error(error);
    return Swal.fire({
      icon: "error",
      title: "Gagal mengirim!",
      text: "Silakan coba lagi nanti.",
    });
  }

  Swal.fire({
    icon: "success",
    title: "Pendaftaran Berhasil!",
    text: "Terima kasih, kami akan menghubungi Anda.",
  });

  nama.value = "";
  telepon.value = "";
  alamat.value = "";
};
</script>
