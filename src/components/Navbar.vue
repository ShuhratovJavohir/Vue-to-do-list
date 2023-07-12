<template>
	<header class="header">
		<nav class="header__nav" v-if="header">
			<button class="header__nav-lang">Ru</button>
			<h1 class="header__nav-title">Заметки</h1>
			<button class="header__nav-search" @click="header = false">
				<img src="@/assets/images/search.svg" alt="search">
			</button>
		</nav>
		<nav class="header__search" v-else>
			<button class="header__search-back" @click="header = true, search = ''">
				<img src="../assets/images/back.svg" alt="">
			</button>
			<input 
				placeholder="Поиск" 
				type="text" 
				class="header__search-input"
				autofocus
				v-model="search"
			>
			<button class="header__search-close" @click="search = ''">
				<img src="../assets/images/close.svg" alt="">
			</button>
		</nav>
	</header>
</template>

<script>
export default {
	data(){
		return{
			header: true,
			search: '',
		}
	}
}
</script>