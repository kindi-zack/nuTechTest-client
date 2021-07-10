<template>
  <main>
    <!-- <div class="container-fluid bg-trasparent my-4 p-3" style="position: relative;">
        <div class="row row-cols-1 row-cols-xs-2 row-cols-sm-2 row-cols-lg-4 g-3"> -->
            <div class="col">
                <div class="card h-100 shadow-sm"> <img :src="item.foto" class="card-img-top" alt="...">
                    <div class="card-body">
                        <div class="clearfix mb-3"> <span class="float-start badge  bg-primary">{{item.nama}}</span></div>
                        <div class="clearfix mb-3"> <span class="float-start badge rounded-pill bg-primary">Harga Beli</span> <span class="float-end price-hp">{{item.harga_beli}}.00 $</span> </div>
                        <!-- <h5 class="card-title">{{item.harga_jual}}</h5> -->
                        <div class="clearfix mb-3"> <span class="float-start badge rounded-pill bg-primary">Harga Jual</span> <span class="float-end price-hp">{{item.harga_jual}}.00 $</span> </div>
                        <div class="clearfix mb-3"> <span class="float-start badge rounded-pill bg-primary">Stok</span> <span class="float-end price-hp">{{item.stok}}</span> </div>
                        <div class="text-center my-4"> <a href="#" class="btn btn-warning">Check offer</a> </div>
                    </div>
                </div>
            </div>
  </main>
</template>

<script>
export default {
    props: ['item']

}
</script>

<style>

</style>