<template>
  <section>
    <div class="container">

    <form class="well form-horizontal" action=" " method="post"  id="contact_form" @submit.prevent='inputData'>
<!-- <fieldset> -->

<!-- Form Name -->
<legend><center><h2><b>TAMBAH BARANG</b></h2></center></legend><br>

<!-- Text input-->
<center>
<div class="form-group">
  <label class="col-md-4 control-label">Foto</label>  
  <div class="col-md-4 inputGroupContainer">
  <div class="input-group">
  <span class="input-group-addon"><i class="glyphicon glyphicon-user"></i></span>
  <input v-model='foto'  name="foto" placeholder="Foto link url" class="form-control"  type="text">
    </div>
  </div>
</div>

<!-- Text input-->

<div class="form-group">
  <label class="col-md-4 control-label" >Nama</label> 
    <div class="col-md-4 inputGroupContainer">
    <div class="input-group">
  <span class="input-group-addon"><i class="glyphicon glyphicon-user"></i></span>
  <input v-model='nama' name="nama" placeholder="Nama" class="form-control"  type="text">
    </div>
  </div>
</div>

  <div class="form-group"> 
  <label class="col-md-4 control-label">Harga Beli</label>
    <div class="col-md-4 selectContainer">
    <div class="input-group">
        <span class="input-group-addon"><i class="glyphicon glyphicon-list"></i></span>
    <input v-model='harga_beli' name="haga_beli" placeholder="Harga Beli" class="form-control"  type="number">
  </div>
</div>

<div class="form-group"> 
  <label class="col-md-4 control-label">Harga Jual</label>
    <div class="col-md-4 selectContainer">
    <div class="input-group">
        <span class="input-group-addon"><i class="glyphicon glyphicon-list"></i></span>
    <input v-model='harga_jual' name="haga_jual" placeholder="Harga Jual" class="form-control"  type="number">
  </div>
</div>
</div>

<div class="form-group"> 
  <label class="col-md-4 control-label">Stok</label>
    <div class="col-md-4 selectContainer">
    <div class="input-group">
        <span class="input-group-addon"><i class="glyphicon glyphicon-list"></i></span>
    <input v-model='stok' name="stok" placeholder="Stok" class="form-control"  type="number">
  </div>
</div>
</div>
  
      <input type="submit">
    </center>
</form>
</div>
   
  </section>
</template>

<script>
import axios from 'axios'
export default {
    props: ['showForm', 'fetchProduct', 'baseUrl'],
    data(){
        return {
            foto: '',
            nama: '',
            harga_beli:'',
            harga_jual: '',
            stok: ''
        }
    },
    methods: {
        inputData(){
            axios({
                method: 'POST',
                url: `${this.baseUrl}barang`,
                data: {
                    foto : this.foto,
                    nama : this.nama,
                    harga_beli : this.harga_beli,
                    harga_jual : this.harga_jual,
                    stok : this.stok
                }
            })
            .then(({data})=>{
                console.log(data)
                this.showForm(true)
                this.fetchProduct()

            })
            .catch(({response})=>{
                console.log(response)
            })
            .then(_=>{
                this.foto = ''
                this.nama = ''
                this.harga_beli = ''
                this.harga_jual = ''
                this.stok = ''
            })
        }
    }
}
</script>

<style>

</style>

