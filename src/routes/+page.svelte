<script lang="ts">
	let activeCategory = $state('Semua');

	const categories = ['Semua', 'Makanan', 'Minuman', 'Camilan'];

	const menu = [
		{
			id: 1,
			name: 'Nasi Goreng Nusantara',
			description: 'Nasi goreng rempah dengan telur mata sapi dan kerupuk.',
			price: 28000,
			category: 'Makanan',
			tag: 'Favorit',
			image:
				'https://images.unsplash.com/photo-1603133872878-684f208fb84b?auto=format&fit=crop&w=800&q=85'
		},
		{
			id: 2,
			name: 'Sate Ayam Madura',
			description: 'Sate ayam empuk dengan bumbu kacang dan kecap.',
			price: 32000,
			category: 'Makanan',
			tag: 'Best seller',
			image:
				'https://images.unsplash.com/photo-1529563021893-cc83c992d75d?auto=format&fit=crop&w=800&q=85'
		},
		{
			id: 3,
			name: 'Es Kopi Aren',
			description: 'Kopi pilihan, susu creamy, dan manisnya gula aren.',
			price: 18000,
			category: 'Minuman',
			tag: '',
			image:
				'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?auto=format&fit=crop&w=800&q=85'
		},
		{
			id: 4,
			name: 'Pisang Goreng',
			description: 'Pisang goreng renyah dengan madu dan taburan wijen.',
			price: 16000,
			category: 'Camilan',
			tag: '',
			image:
				'https://images.unsplash.com/photo-1587132137056-bfbf0166836e?auto=format&fit=crop&w=800&q=85'
		},
		{
			id: 5,
			name: 'Ayam Bakar Rempah',
			description: 'Ayam bakar berbumbu khas dengan nasi hangat dan lalapan.',
			price: 35000,
			category: 'Makanan',
			tag: 'Rekomendasi',
			image:
				'https://images.unsplash.com/photo-1532550907401-a500c9a57435?auto=format&fit=crop&w=800&q=85'
		},
		{
			id: 6,
			name: 'Es Teh Melati',
			description: 'Teh melati dingin yang ringan dan menyegarkan.',
			price: 10000,
			category: 'Minuman',
			tag: '',
			image:
				'https://images.unsplash.com/photo-1556679343-c7306c1976bc?auto=format&fit=crop&w=800&q=85'
		}
	];

	let filteredMenu = $derived(
		activeCategory === 'Semua' ? menu : menu.filter((item) => item.category === activeCategory)
	);

	const formatPrice = (price: number) =>
		new Intl.NumberFormat('id-ID', {
			style: 'currency',
			currency: 'IDR',
			maximumFractionDigits: 0
		}).format(price);
</script>

<svelte:head>
	<title>Kaloka Resto — Rasa yang Selalu Dirindukan</title>
	<meta
		name="description"
		content="Temukan cita rasa Nusantara di Kaloka Resto. Hidangan hangat, bahan pilihan, dan suasana yang membuatmu betah."
	/>
	<meta name="theme-color" content="#f8f6ef" />
</svelte:head>

<div class="min-h-screen bg-[#f8f6ef] text-[#242b20] selection:bg-[#dce6ca]">
	<!-- Navbar -->
	<header class="sticky top-0 z-50 border-b border-[#e8e5d9] bg-[#f8f6ef]/95 backdrop-blur-md">
		<nav class="mx-auto flex max-w-7xl items-center justify-between px-5 py-4 sm:px-8">
			<a href="#home" class="flex items-center gap-3">
				<div
					class="flex h-10 w-10 items-center justify-center rounded-2xl bg-[#344b35] text-lg text-white"
				>
					K.
				</div>
				<div>
					<p class="text-lg font-extrabold tracking-tight">
						kaloka<span class="text-[#c66b3d]">.</span>
					</p>
					<p class="-mt-1 text-[10px] tracking-[0.25em] text-[#7e8376] uppercase">
						Indonesian kitchen
					</p>
				</div>
			</a>

			<div class="hidden items-center gap-8 text-sm font-medium text-[#686e61] md:flex">
				<a href="#home" class="transition hover:text-[#344b35]">Beranda</a>
				<a href="#menu" class="transition hover:text-[#344b35]">Menu</a>
				<a href="#story" class="transition hover:text-[#344b35]">Cerita kami</a>
				<a href="#visit" class="transition hover:text-[#344b35]">Lokasi</a>
			</div>

			<a
				href="#menu"
				class="rounded-full bg-[#344b35] px-5 py-3 text-sm font-semibold text-white transition hover:bg-[#263a28]"
			>
				Lihat menu <span aria-hidden="true">↗</span>
			</a>
		</nav>
	</header>

	<main>
		<!-- Hero -->
		<section
			id="home"
			class="mx-auto grid max-w-7xl items-center gap-12 px-5 py-14 sm:px-8 md:grid-cols-2 md:py-24"
		>
			<div class="order-2 md:order-1">
				<div
					class="mb-6 inline-flex items-center gap-2 rounded-full border border-[#dedfd2] bg-white/70 px-4 py-2 text-xs font-semibold tracking-[0.15em] text-[#59694e] uppercase"
				>
					<span class="h-2 w-2 rounded-full bg-[#c66b3d]"></span>
					Sajian hangat, setiap hari
				</div>

				<h1
					class="max-w-xl text-5xl leading-[1.08] font-semibold tracking-tight sm:text-6xl lg:text-7xl"
				>
					Rasa yang
					<span class="font-serif text-[#c66b3d] italic">selalu</span>
					dirindukan.
				</h1>

				<p class="mt-6 max-w-lg text-base leading-8 text-[#74776c] sm:text-lg">
					Dari resep Nusantara hingga racikan modern. Kami percaya, makanan yang baik bukan sekadar
					mengenyangkan, tetapi juga menciptakan cerita.
				</p>

				<div class="mt-9 flex flex-wrap gap-3">
					<a
						href="#menu"
						class="rounded-full bg-[#344b35] px-7 py-4 text-sm font-semibold text-white transition hover:-translate-y-0.5 hover:bg-[#263a28]"
					>
						Jelajahi menu <span class="ml-2">↗</span>
					</a>
					<a
						href="#story"
						class="rounded-full border border-[#dcdccf] px-7 py-4 text-sm font-semibold transition hover:bg-white"
					>
						Tentang kami
					</a>
				</div>

				<div class="mt-12 flex items-center gap-5 border-t border-[#e4e1d6] pt-7">
					<div class="flex -space-x-3">
						<img
							class="h-10 w-10 rounded-full border-2 border-[#f8f6ef] object-cover"
							src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=100&q=80"
							alt="Pelanggan Kaloka"
						/>
						<img
							class="h-10 w-10 rounded-full border-2 border-[#f8f6ef] object-cover"
							src="https://images.unsplash.com/photo-1500648767791-00dcc994a43e?auto=format&fit=crop&w=100&q=80"
							alt="Pelanggan Kaloka"
						/>
						<img
							class="h-10 w-10 rounded-full border-2 border-[#f8f6ef] object-cover"
							src="https://images.unsplash.com/photo-1531123897727-8f129e1688ce?auto=format&fit=crop&w=100&q=80"
							alt="Pelanggan Kaloka"
						/>
					</div>
					<div>
						<p class="text-sm font-bold">Dibuat dengan sepenuh hati</p>
						<p class="mt-1 text-xs text-[#85877b]">Bahan pilihan · Rasa autentik</p>
					</div>
				</div>
			</div>

			<div class="relative order-1 md:order-2">
				<div
					class="absolute -top-4 -right-3 z-10 flex h-24 w-24 rotate-12 flex-col items-center justify-center rounded-full bg-[#d9e2c8] text-center text-[#344b35] shadow-sm sm:-top-5 sm:-right-5"
				>
					<span class="text-xs font-medium">Made with</span>
					<span class="text-lg font-bold">♥</span>
					<span class="text-xs font-medium">local love</span>
				</div>

				<div class="overflow-hidden rounded-[2rem] rounded-bl-[7rem] bg-[#e7e1d2]">
					<img
						class="h-[380px] w-full object-cover sm:h-[520px]"
						src="https://images.unsplash.com/photo-1547592180-85f173990554?auto=format&fit=crop&w=1200&q=90"
						alt="Hidangan Nusantara tersaji di meja makan"
					/>
				</div>

				<div
					class="absolute right-5 -bottom-6 left-5 rounded-2xl border border-white/70 bg-white/95 p-4 shadow-xl sm:right-10 sm:left-10 sm:p-5"
				>
					<div class="flex items-center justify-between gap-4">
						<div>
							<p class="text-xs font-medium text-[#85877b]">Pilihan hari ini</p>
							<p class="mt-1 font-bold">Nasi Goreng Nusantara</p>
							<p class="mt-1 text-sm text-[#74776c]">Rempah lokal, rasa maksimal.</p>
						</div>
						<a
							href="#menu"
							aria-label="Lihat menu nasi goreng"
							class="flex h-12 w-12 shrink-0 items-center justify-center rounded-full bg-[#344b35] text-xl text-white transition hover:bg-[#263a28]"
							>↗</a
						>
					</div>
				</div>
			</div>
		</section>

		<!-- Highlights -->
		<section class="mt-14 border-y border-[#e8e5d9] bg-[#f0eee5]">
			<div class="mx-auto grid max-w-7xl grid-cols-1 gap-7 px-5 py-9 sm:grid-cols-3 sm:px-8">
				<div class="flex items-center gap-4">
					<div class="flex h-12 w-12 items-center justify-center rounded-2xl bg-white text-xl">
						✳
					</div>
					<div>
						<p class="font-bold">Bahan pilihan</p>
						<p class="mt-1 text-sm text-[#777a6e]">Segar dan berkualitas.</p>
					</div>
				</div>
				<div class="flex items-center gap-4">
					<div class="flex h-12 w-12 items-center justify-center rounded-2xl bg-white text-xl">
						♨
					</div>
					<div>
						<p class="font-bold">Dimasak saat dipesan</p>
						<p class="mt-1 text-sm text-[#777a6e]">Hangat di setiap sajian.</p>
					</div>
				</div>
				<div class="flex items-center gap-4">
					<div class="flex h-12 w-12 items-center justify-center rounded-2xl bg-white text-xl">
						⌂
					</div>
					<div>
						<p class="font-bold">Suasana nyaman</p>
						<p class="mt-1 text-sm text-[#777a6e]">Tempat untuk berkumpul.</p>
					</div>
				</div>
			</div>
		</section>

		<!-- Menu -->
		<section id="menu" class="mx-auto max-w-7xl px-5 py-20 sm:px-8 md:py-28">
			<div class="flex flex-col justify-between gap-7 sm:flex-row sm:items-end">
				<div>
					<p class="text-xs font-bold tracking-[0.25em] text-[#c66b3d] uppercase">
						Dari dapur kami
					</p>
					<h2 class="mt-4 text-4xl font-semibold tracking-tight sm:text-5xl">
						Menu pilihan<span class="text-[#c66b3d]">.</span>
					</h2>
					<p class="mt-4 max-w-md leading-7 text-[#777a6e]">
						Rasa yang akrab, dibuat dengan cara yang istimewa. Temukan favoritmu di sini.
					</p>
				</div>

				<div class="flex flex-wrap gap-2">
					{#each categories as category, i (i)}
						<button
							class={`rounded-full px-5 py-3 text-sm font-medium transition ${
								activeCategory === category
									? 'bg-[#344b35] text-white'
									: 'border border-[#e0dfd4] text-[#73776b] hover:bg-white'
							}`}
							aria-pressed={activeCategory === category}
							onclick={() => (activeCategory = category)}
						>
							{category}
						</button>
					{/each}
				</div>
			</div>

			<div class="mt-10 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
				{#each filteredMenu as item (item.id)}
					<article
						class="group overflow-hidden rounded-3xl border border-[#e9e6dc] bg-white transition duration-300 hover:-translate-y-1 hover:shadow-xl hover:shadow-[#344b35]/5"
					>
						<div class="relative overflow-hidden bg-[#eee9df]">
							<img
								src={item.image}
								alt={item.name}
								loading="lazy"
								class="h-60 w-full object-cover transition duration-500 group-hover:scale-105"
							/>
							{#if item.tag}
								<span
									class="absolute top-4 left-4 rounded-full bg-[#f8f6ef] px-3 py-2 text-xs font-bold text-[#344b35]"
								>
									{item.tag}
								</span>
							{/if}
						</div>

						<div class="p-5">
							<div class="flex items-start justify-between gap-3">
								<div>
									<p class="text-xs font-medium tracking-wider text-[#99998d] uppercase">
										{item.category}
									</p>
									<h3 class="mt-2 text-lg font-bold">{item.name}</h3>
								</div>
								<span class="shrink-0 text-sm font-bold text-[#c66b3d]">
									{formatPrice(item.price)}
								</span>
							</div>
							<p class="mt-3 min-h-12 text-sm leading-6 text-[#777a6e]">{item.description}</p>
							<a
								href="#visit"
								class="mt-5 flex items-center justify-between border-t border-[#efede5] pt-4 text-sm font-semibold transition group-hover:text-[#c66b3d]"
							>
								Temukan di restoran
								<span aria-hidden="true">↗</span>
							</a>
						</div>
					</article>
				{/each}
			</div>

			<p class="mt-8 text-center text-xs text-[#929386]">
				Harga dan menu pada halaman ini merupakan contoh untuk keperluan proyek.
			</p>
		</section>

		<!-- Story -->
		<section id="story" class="bg-[#344b35] text-[#f8f6ef]">
			<div
				class="mx-auto grid max-w-7xl items-center gap-12 px-5 py-20 sm:px-8 md:grid-cols-2 md:py-24"
			>
				<div class="relative">
					<img
						src="https://images.unsplash.com/photo-1559339352-11d035aa65de?auto=format&fit=crop&w=1100&q=85"
						alt="Suasana restoran yang hangat dan nyaman"
						loading="lazy"
						class="h-[350px] w-full rounded-[2rem] object-cover sm:h-[450px]"
					/>
					<div
						class="absolute -right-3 -bottom-5 rounded-2xl bg-[#dce4ce] px-6 py-4 text-[#344b35] shadow-lg sm:-right-5"
					>
						<p class="font-serif text-2xl italic">Rasa. Cerita. Rumah.</p>
					</div>
				</div>

				<div class="pt-5 md:pl-8">
					<p class="text-xs font-bold tracking-[0.25em] text-[#d9b18b] uppercase">Cerita Kaloka</p>
					<h2 class="mt-5 text-4xl leading-tight font-semibold tracking-tight sm:text-5xl">
						Lebih dari sekadar tempat makan.
					</h2>
					<p class="mt-6 leading-8 text-white/70">
						Kaloka Resto lahir dari gagasan sederhana: menghadirkan makanan yang terasa dekat,
						suasana yang membuat nyaman, dan pengalaman yang ingin diulang.
					</p>
					<p class="mt-4 leading-8 text-white/70">
						Kami menggabungkan kekayaan rasa Nusantara dengan sentuhan modern, tanpa kehilangan hal
						terpenting: kehangatan dalam setiap hidangan.
					</p>
					<a
						href="#visit"
						class="mt-8 inline-flex items-center gap-3 rounded-full bg-[#f8f6ef] px-6 py-4 text-sm font-bold text-[#344b35] transition hover:bg-[#dce4ce]"
					>
						Kunjungi Kaloka <span aria-hidden="true">↗</span>
					</a>
				</div>
			</div>
		</section>

		<!-- Visit -->
		<section id="visit" class="mx-auto max-w-7xl px-5 py-20 sm:px-8 md:py-24">
			<div class="rounded-[2rem] border border-[#e5e2d7] bg-white p-7 sm:p-12">
				<div class="grid gap-10 md:grid-cols-2 md:items-center">
					<div>
						<p class="text-xs font-bold tracking-[0.25em] text-[#c66b3d] uppercase">
							Sampai jumpa di meja kami
						</p>
						<h2 class="mt-4 text-4xl font-semibold tracking-tight sm:text-5xl">
							Makan enak, <span class="font-serif text-[#c66b3d] italic">tanpa terburu-buru.</span>
						</h2>
						<p class="mt-5 max-w-md leading-7 text-[#777a6e]">
							Ajak teman, keluarga, atau datang sendiri. Selalu ada tempat untuk menikmati makanan
							yang baik.
						</p>
					</div>

					<div class="rounded-3xl bg-[#f4f2e9] p-6 sm:p-8">
						<div class="border-b border-[#deddd1] pb-5">
							<p class="text-xs font-bold tracking-wider text-[#85877b] uppercase">
								Jam operasional
							</p>
							<p class="mt-2 text-lg font-bold">Setiap hari, 10.00–22.00</p>
						</div>
						<div class="border-b border-[#deddd1] py-5">
							<p class="text-xs font-bold tracking-wider text-[#85877b] uppercase">Lokasi</p>
							<p class="mt-2 font-semibold">Purworejo, Jawa Tengah</p>
							<p class="mt-1 text-sm text-[#777a6e]">Alamat ini merupakan contoh untuk demo.</p>
						</div>
						<a
							href="#home"
							class="mt-5 flex w-full items-center justify-between rounded-full bg-[#344b35] px-6 py-4 text-sm font-semibold text-white transition hover:bg-[#263a28]"
						>
							Kembali ke beranda
							<span aria-hidden="true">↑</span>
						</a>
					</div>
				</div>
			</div>
		</section>
	</main>

	<!-- Footer -->
	<footer class="border-t border-[#e8e5d9]">
		<div
			class="mx-auto flex max-w-7xl flex-col gap-5 px-5 py-8 text-sm text-[#777a6e] sm:flex-row sm:items-center sm:justify-between sm:px-8"
		>
			<a href="#home" class="text-lg font-extrabold tracking-tight text-[#242b20]">
				kaloka<span class="text-[#c66b3d]">.</span>
			</a>
			<p>Rasa yang baik, cerita yang tinggal.</p>
			<p>© {new Date().getFullYear()} Kaloka Resto. Demo project.</p>
		</div>
	</footer>
</div>
