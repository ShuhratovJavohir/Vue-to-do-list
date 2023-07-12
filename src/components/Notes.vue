<template>
	<div class="notes">
		<div class="container">
			<div class="notes__top">
				<h2 class="notes__top-title">{{ notes.length == 0 ? 'Заметок нет' : 'Все заметки' }}</h2>
				<button @click="view = !view" class="notes__top-btn">
					<img v-show="view" src="@/assets/images/list.svg" alt="list">
					<img v-show="!view" src="@/assets/images/grid.svg" alt="list">
					<span>{{ view ? 'Список' : 'Сетка' }}</span>
				</button>
			</div>
			<div :class="view ? 'notes__list' : 'notes__grid'">
				<Note v-for="note in notes" :key="note.id" :note="note" :view="view" @delNotes="$emit('delNotes', note.id)"
					@change="$emit('change', note.id)" />
			</div>
		</div>
	</div>
</template>
	
<script>
import Note from '@/components/Note.vue'
export default {
	props: {
		notes: { typeof: Array },
		countNote: { typeof: Boolean },
	},
	data() {
		return {
			view: true,
		};
	},
	components: { Note }
}
</script>