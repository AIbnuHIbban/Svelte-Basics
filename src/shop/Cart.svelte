<script>
    export let items;

    $: hargaTotal = items.reduce((sum, curValue) => {
		return sum + curValue.harga
	}, 0);
</script>


<div class="card">
    <div class="card-body">
        <h4 class="text-center text-danger mb-3">
            Keranjang Belanja
        </h4>
        
        {#if items.length === 0}
            <h5 class="text-center my-3 text-muted">Keranjang Belanja anda masih Kosong</h5>
        {:else}
            <div class="row">
                {#each items as item}
                <div class="col-md-3 mb-3">
                    <div class="card">
                        <div class="card-body">
                            <h4>{item.nama}</h4>
                            <p>Rp. <strong class="font-weight-bold"> {item.harga}</strong></p>
                        </div>
                    </div>
                </div>
                {/each}
            </div>
        {/if}

        <div class="col-md-5 offset-md-7">
            <h3>Total : Rp. {hargaTotal}</h3>
        </div>
    </div>
</div>

<style>

</style>