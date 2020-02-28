<script>
	import Produk from "./Produk.svelte";
	import Cart from "./Cart.svelte"

    let nama = '',
		deskripsi = '',
		harga = 0,
		listProduk = [],
		itemKeranjang = [];

	const setNama = (event) => {
		nama = event.target.value
	}

	const addProduk = () => {
		const detailProduk = {
			nama : nama,
			harga : harga,
			deskripsi : deskripsi
		};

		listProduk = listProduk.concat(detailProduk);
	}

	const tambahKeranjang = (event) => {
		const judulTerpilih = event.detail
		itemKeranjang = itemKeranjang.concat({
			...listProduk.find(prod => prod.nama === judulTerpilih)
		});
		console.log(itemKeranjang)
		
	}
</script>


<main>
    <div class="row mb-3">
		<div class="col-md-6">
			<div class="card">
				<div class="card-body">
					<h3 class="text-center text-primary">Tambah Produk</h3>
					<hr>
					<div class="text-left">
						<div class="form-group">
							<label for="">Nama Produk</label>
							<input type="text" class="form-control" id="name" placeholder="Nama Produk" bind:value="{nama}" on:input={setNama}>
						</div>
						<div class="form-group">
							<label for="">Deskripsi</label>
							<textarea class="form-control" id="deskripsi" placeholder="Deskripsi Produk" bind:value="{deskripsi}"></textarea>
						</div>
						<div class="form-group">
							<label for="">Harga Produk</label>
							<input type="number" class="form-control" id="harga" placeholder="Harga Produk" bind:value="{harga}">
						</div>
						<button on:click="{addProduk}" class="btn btn-danger btn-sm btn-block">Tambah Produk</button>
					</div>
				</div>
			</div>
		</div>
		<div class="col-md-6">
			<div class="card">
				<div class="card-body">
					{#if listProduk.length === 0}
						<p class="font-weight-bold p-0 text-center">Tidak ada Produk</p>
					{:else}
						<div class="row">
							{#each listProduk as produk}
								<Produk on:addCart={tambahKeranjang} judulProduk={produk.nama} deskripsiProduk={produk.deskripsi} hargaProduk={produk.harga}/>
							{/each}
						</div>
					{/if}
				</div>
			</div>
		</div>
	</div>
	<Cart items={itemKeranjang}/>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>