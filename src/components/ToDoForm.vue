<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits(['todo-added'])

const label = ref<string | null>('')

function onSubmit() {
	if (label.value === '') {
		return
	}
	console.log('Label: ', label.value)
	emit('todo-added', label.value)
	label.value = ''
}
</script>

<template>
	<form @submit.prevent="onSubmit">
		<label for="new-todo-input"> What needs to be done? </label>
		<input
			type="text"
			id="new-todo-input"
			name="new-todo"
			autocomplete="off"
			class="input__lg"
			v-model.lazy.trim="label"
		/>
		<button type="submit" class="btn btn__primary btn__lg">Add</button>
	</form>
</template>

<style scoped></style>
