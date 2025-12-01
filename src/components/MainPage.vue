<template>
  <div class="bg-linear-to-b from-blue-600 to-blue-700 mx-auto py-14">
    <div class="text-center pt-16 p-4">
      <span class="bg-white/10 rounded-full text-white py-2 px-4"
        >Peluang Usaha 2025</span
      >
      <div class="mt-5">
        <h1 class="text-white font-black text-3xl lg:text-6xl mb-6">
          Mitra Usaha Franchise <br />
          <span class="text-yellow-500">Mandiri Supplier</span>
        </h1>
        <p class="text-white text-base max-w-xl mx-auto lg:text-xl">
          Usaha Kebutuhan Pokok Terjangkau. Mulai bisnis sendiri dengan modal
          terjangkau dan dukungan penuh dari kami.
        </p>
      </div>
      <a
        href="#form"
        class="bg-yellow-500 inline-block mt-8 rounded-xl py-3 px-8 text-white font-bold"
        >Gabung Sekarang</a
      >
    </div>
  </div>
  <div class="mx-auto py-10 mt-8 p-4">
    <div>
      <div class="text-center mb-10">
        <h1 class="text-slate-950 font-black text-2xl lg:text-4xl">
          Franchise Mandiri Supplier
        </h1>
        <p class="text-gray-500 text-base lg:text-xl mt-2">
          Starter Pack Mandiri Supplier - Harga
          <span class="font-black text-blue-500 lg:text-xl">5 Juta</span>
          anda bisa dapetin system franchise dibawah ini
        </p>
      </div>

      <div>
        <div class="relative w-full flex justify-center items-center">
          <div
            class="absolute w-72 h-72 md:w-96 md:h-96 rounded-full bg-blue-500/50 blur-3xl opacity-70"
            style="filter: blur(70px)"
          ></div>

          <img
            :src="franchise_image"
            alt="franchise-image"
            class="relative z-10 mx-auto px-4 float-down"
          />
        </div>

        <div
          class="grid grid-cols-1 max-w-5xl mx-auto md:grid-cols-2 lg:grid-cols-3 gap-6 px-4"
        >
          <div
            v-for="(item, i) in fiturFranchise"
            :key="i"
            class="bg-white rounded-2xl shadow p-6 flex items-start gap-4 transition transform duration-300 hover:-translate-y-2 hover:shadow-xl"
          >
            <div class="bg-blue-600 text-white p-3 rounded-xl">
              <component :is="item.icon" class="w-6 h-6" />
            </div>
            <div>
              <h3 class="font-bold text-slate-950 text-lg">{{ item.title }}</h3>
              <p class="text-gray-500 text-sm">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div class="mt-12 pb-20">
    <div>
      <div class="w-full flex justify-center mb-4">
        <div
          class="bg-blue-500/20 inline-block text-center rounded-full text-blue-400 py-2 px-4"
        >
          Produk Unggulan
        </div>
      </div>
      <h1 class="text-slate-950 text-4xl text-center font-black mb-2">
        Pilihan Paket 5 Juta
      </h1>
      <p class="text-gray-500 text-lg text-center">
        Kebutuhan pokok berkualitas dengan harga terjangkau untuk kebutuhan
        sehari-hari
      </p>
    </div>
    <div
      class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-5xl mx-auto mt-10 px-4"
    >
      <!-- Paket A (Dengan Border Orange) -->
      <div class="relative rounded-2xl h-full">
        <!-- Border Orange -->
        <div
          class="absolute inset-0 rounded-2xl border-4 border-orange-400 pointer-events-none"
        ></div>

        <!-- Isi Card -->
        <div
          class="bg-blue-500 rounded-2xl shadow p-6 m-1.5 flex flex-col overflow-hidden"
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

          <ul class="text-white space-y-1 mt-auto">
            <li>✔ Minyak Saudara 800ML</li>
            <li>✔ Beras Rojolele 1KG</li>
            <li>✔ Gulaku 500GR</li>
            <li>✔ 20 Box</li>
          </ul>
        </div>
      </div>

      <!-- Paket B -->
      <div
        class="bg-blue-500 rounded-2xl shadow p-6 flex flex-col overflow-hidden"
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

        <ul class="text-white space-y-1 mt-auto">
          <li>✔ Minyak Saudara 1LTR</li>
          <li>✔ Beras Rojolele 5KG</li>
          <li>✔ Gulaku 500GR</li>
          <li>✔ 30 Box</li>
        </ul>
      </div>
    </div>
  </div>

  <div
    id="form"
    class="bg-linear-to-b from-blue-600 to-blue-700 pt-16 px-4 pb-16"
  >
    <div class="max-w-2xl mx-auto bg-white rounded-2xl shadow p-8">
      <h2 class="text-3xl font-black text-slate-950 text-center mb-2">
        Mitra Franchise
      </h2>
      <p class="text-base text-gray-500 text-center mb-5">
        Daftar Sekarang dan mulai usaha anda
      </p>
      <form class="space-y-5" @submit.prevent="submitFranchise">
        <!-- Input Nama -->
        <div class="relative">
          <User
            class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-500"
          />
          <input
            v-model="nama"
            type="text"
            placeholder="Nama lengkap.."
            class="w-full px-11 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
          />
        </div>

        <!-- Input Telepon -->
        <div class="relative">
          <Phone
            class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-500"
          />
          <input
            v-model="telepon"
            type="text"
            placeholder="No HP.."
            class="w-full px-11 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
          />
        </div>

        <!-- Input Alamat -->
        <div class="relative">
          <MapPin
            class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-gray-500"
          />
          <input
            v-model="alamat"
            type="text"
            placeholder="Kota & Kelurahan.."
            class="w-full px-11 py-3 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-400 focus:outline-none"
          />
        </div>

        <button
          type="submit"
          class="w-full flex items-center justify-center gap-2 bg-blue-500 text-white font-bold py-3 rounded-xl hover:bg-blue-600 transition"
        >
          Gabung Mitra
          <Send class="w-5 h-5" />
        </button>

        <!-- Tombol WhatsApp -->
        <a
          href="https://wa.me/6285694419400"
          target="_blank"
          class="w-full flex items-center justify-center gap-2 bg-green-500 text-white font-bold py-3 rounded-xl hover:bg-green-600 transition"
        >
          <message-circle class="w-5 h-5" />
          Chat via WhatsApp
        </a>
      </form>
    </div>
  </div>

  <footer class="bg-slate-950 py-5 text-center text-white">
    <p class="flex justify-center items-center gap-2">
      <span>“Hak Cipta © 2025 Mandiri Supplier</span>
    </p>
  </footer>

  <a
    href="https://wa.me/6285694419400"
    target="_blank"
    class="fixed bottom-6 right-6 bg-green-500 p-4 rounded-full shadow-lg hover:bg-green-600 transition z-50"
  >
    <MessageCircle class="w-7 h-7 text-white" />
  </a>
</template>

<script setup>
import paket_A from "../assets/A.jpg";
import paket_B from "../assets/B.jpg";
import franchise_image from "../assets/shop-img.png";
import { ref } from "vue";
import { supabase } from "../supabase";
import {
  Package,
  Globe,
  Megaphone,
  IdCard,
  Wrench,
  Send,
  MessageCircle,
  Image,
  User,
  Phone,
  MapPin,
} from "lucide-vue-next";

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
const fiturFranchise = [
  {
    icon: Package,
    title: "Produk Paket A & B",
    desc: "Paket produk lengkap siap jual",
  },
  {
    icon: Globe,
    title: "Web UMKM",
    desc: "Website toko online untuk usaha Anda",
  },
  {
    icon: Megaphone,
    title: "Marketing Kit",
    desc: "Materi promosi siap pakai",
  },
  {
    icon: IdCard,
    title: "Lisensi Franchise",
    desc: "Hak usaha resmi dari kami",
  },
  {
    icon: Wrench,
    title: "Alat Packaging",
    desc: "Perlengkapan pengemasan produk",
  },
  {
    icon: Image,
    title: "Spanduk & Banner",
    desc: "Media promosi fisik untuk toko",
  },
];
</script>
