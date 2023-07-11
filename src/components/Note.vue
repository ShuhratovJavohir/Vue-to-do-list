<template>
	<div class="note">
		<div :class="view ? 'note__list' : 'note__grid'">
			<h2 class="note-title">{{ note.title }}</h2>
			<p class="note-data">{{ note.date }}</p>
		</div>
		<p class="note-text">{{ note.text }}</p>
		<div class="note__btns">
			<button class="note__btns-edit">
				<img src="@/assets/images/edit.svg" alt="">
				<span>РЕДАКТИРОВАТЬ</span>
			</button>
			<button class="note__btns-delete" @click="$emit('delNotes', note.id)">
				<img src="@/assets/images/delete.svg" alt="">
				<span>Удалить</span>
			</button>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		note: { typeof: Object},
		view: { typeof: Boolean}
	},
	data() {
		return {

		}
	}
}
</script>