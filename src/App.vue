<script >
  export default {
    data() {
      return {
        riwayat:[
          {
            id: 1,
            nama: 'PT.Adinata Luhung Sentosa',
            posisi: 'Administrasi Umum',
            desc: 'Melayani Customer, Melakukan Foto Studio dan membuat pas foto customer untuk visa dan lainnya',
          },

          {
            id: 2,
            nama: 'PT.Indigo Cakra Wangsa',
            posisi: 'Operator Multi Media',
            desc: 'Melakukan penayangan screen besar di acara" seperti pernikahan dan rapt atau lainya, berkordinasi dengan WO yang bermenjalankan rounded acara tersebut',
          },

          {
            id: 3, 
            nama: 'PT.Makmur Bersama Gomesin',
            posisi: 'Admin & Editor',
            desc: 'Melayanin customer melalui marketplace dan mengedit produk untuk postingan marketplace',
          }
        ],
        
        show: true,

        keahlian: [
          {id: 1, nama:'Edit', presentase: 80},  
          {id: 2, nama:'Mengetik', presentase: 90},
          {id: 3, nama:'Marketing', presentase: 50}
        ],

        nama: '',
        email: '',
        pesan: '',
      }
    },

  methods: {
    kirim() {
      alert  ('terima kasih'+ ' ' + this.nama + ' email anda'+ ' ' + this.email + ' ' + 'masukan anda akan kami proses' + ' ' + this.pesan)
             // atau lebih efek menggunakan tanda (`) diawal dan diakhir
            //(`terima kasih ${this.nama}, email anda ${this.email}, masukan anda akan kam proses ${this.pesan}`)
      this.$refs.form.reset()
    }
  }   
}
</script>

<template>
<div class="border-form">
  <div class="resume">
    <h1 style="text-align:center; text-shadow: 2px 2px;">Daftar Riwayat Hidup</h1>
    <hr>
    <h2>KK Arya Setiawan</h2>
    <p>Saya Mahasiswa Universitas Indraprasta PGRI, Sedang mengikuti kegiatan MSIB yang bertempat di <strong>PT.Qatros Teknologi Nusantara</strong> yang berlokasi di D.I Yogyakarta</p>
  </div>
   <hr>

  <div id="riwayat">
    <h2 style="text-decoration: underline;">Pengalaman</h2>
    <div class="riwayat" v-for="rwy in riwayat" :key="rwy.id">
      <p class="riwayat-list" @click="rwy.show = !rwy.show" >
       <b>{{ rwy.id}}. {{rwy.nama}} - {{rwy.posisi}}</b>
      </p>
      <p class="desc" v-if="rwy.show">{{rwy.desc}}</p>
    </div>
  </div>
<hr>

  <div class="kemampuan">
    <h2 style="text-decoration: underline;">Keahlian</h2>
    <div class="keahlian">
      <ul>
        <li class="keahlian-list" v-for="skl in keahlian" :key="skl.id">
          <p>{{skl.nama}}</p>
          <div class="progress_bar" :style="{width: skl.presentase + '%'}"> {{skl.presentase}}%</div>
        </li>
      </ul>
    </div>
  </div>
  <hr>

  <div class="informasi">
    <h2 style="text-decoration: underline;">Hubungi</h2>
      <form @submit.prevent="kirim" ref="form">
        <div class="form-kontak">
          <label>Nama : </label><br>
          <input type="text" v-model="nama" required/>
        </div>
        <div class="form-kontak">
          <label>Email : </label><br>
          <input type="email" v-model="email" required/>
        </div>
        <div class="form-kontak">
          <label>Pesan :</label><br>
          <textarea type="text" v-model="pesan" required></textarea> 
        </div>
        <div class="form-kontak" style="justify-content: center; display: flex;">
          <button class="btn" type="submit"> Kirim</button>
        </div>
      </form> 
  </div>
</div> 
</template>

<style >
body {
  background-color: rgba(169, 169, 169, 0.719);
  color: black;
  height: 100%;

}

.border-form {
  border-radius: 10px; /* lengkungan pada ujung kotak */
  max-width: 600px; /* lebar atau tinggi kotak*/
  border: 2px /* ukuran list pada pinggiran kotak*/solid black; 
  padding: 12px; /* untuk space kanan kiri posisi teks */
  margin: auto; 
  background-color: rgb(126, 121, 121);
  
  
}

.progress_bar {
  background: blue;
  border: solid 1px black;
  height:25px;
  border-radius:5px;
  overflow:hidden;
  text-align: center;
}

.informasi {
  border: 2px solid black;
  background-color: brown;
  border-radius: 10px;
  padding: 10px;

}
.btn {
  background: blue;
  border: solid 2px black;
  text-align: center;
}


</style>
