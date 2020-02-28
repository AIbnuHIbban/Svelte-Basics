<script>
    import { createEventDispatcher } from "svelte"
    export let judulProduk,
        deskripsiProduk,
        hargaProduk;

    const dispatch = createEventDispatcher();

    const addtoCart = () => {
        dispatch('addCart', judulProduk)
    }
    
</script>

<div class="col-md-6 mb-3">
    <div class="card">
        <div class="card-body">
            <p class="mb-0">
                <strong>
                    {judulProduk}
                </strong>
            </p>
            <em>{deskripsiProduk}</em>
            <p class="mt-1">Rp. {hargaProduk}</p>
            <button on:click="{addtoCart}" class="btn btn-block btn-sm btn-danger">+ Tambah ke Keranjang</button>
        </div>
    </div>
</div>

<style>

</style>
