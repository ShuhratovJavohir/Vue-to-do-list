<template>
	<div class="note">
		<div class="note__top">
			<h2 class="note-title">{{ title }}</h2>
			<p class="note-data">{{ date }}</p>
		</div>
		<p class="note-text">{{ text }}</p>
		<div class="note__btns">
			<button class="note__btns-edit">
				<img src="@/assets/images/edit.svg" alt="">
				<span>РЕДАКТИРОВАТЬ</span>
			</button>
			<button class="note__btns-delete">
				<img src="@/assets/images/delete.svg" alt="">
				<span>Удалить</span>
			</button>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		title: { typeof: String },
		text: { typeof: String },
		date: { typeof: String }
	},
	data() {
		return {

		}
	}
}
</script>