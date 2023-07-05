<script setup>
	import { FormKit } from '@formkit/vue';

	import Heading from '../components/ui/Heading.vue';
	import RouterLink from '../components/ui/RouterLink.vue';
	defineProps({
		titulo: {
			type: String,
		},
	});
</script>

<template>
	<div>
		<div class="flex justify-end">
			<RouterLink to="inicio">Volver</RouterLink>
		</div>

		<Heading>{{ titulo }}</Heading>
		<div class="mx-auto mt-10 bg-white shadow"></div>
	</div>
</template>
