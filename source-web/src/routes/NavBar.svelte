<script>
	import categories from '@/assets/categories.js';
	import { page } from '$app/stores';

	$: categoryParam = $page.params.category;
</script>

<nav>
	<ul class="flex gap-2 flex-wrap">
		<li class="flex-grow">
			<a
				href="/"
				class={`flex items-center w-full justify-center gap-2 bg-blue-500 rounded-md px-4 py-1.5 flex-grow outline-2 outline-blue-500 outline-offset-2 cursor-pointer hover:scale-[1.03] transition-transform ${
					categoryParam === undefined ? 'outline' : ''
				}`}
			>
				<img src="/categories-icons/all.svg" alt="" class="invert w-6" />
				All
			</a>
		</li>
		{#each categories as category}
			<li class="flex-grow md:min-w-[12rem] text-base">
				<a
					href={`/${category.name.toLowerCase().replaceAll(' ', '-')}`}
					class={`flex items-center w-full justify-center gap-2 bg-[--item-color] rounded-md px-4 py-1.5 flex-grow outline-2 outline-[--item-color] outline-offset-2 cursor-pointer hover:scale-[1.03] transition-transform ${
						category.name.toLowerCase().replaceAll(' ', '-') === categoryParam
							? 'scale-[1.03] outline'
							: ''
					}`}
					style={`--item-color: ${category.color}`}
				>
					<img
						src={'/categories-icons/' +
							category.name.toLowerCase().replaceAll(/\/|\s/g, '-') +
							'.svg'}
						alt=""
						class="invert w-6"
					/>
					{category.name}
				</a>
			</li>
		{/each}
	</ul>
</nav>
