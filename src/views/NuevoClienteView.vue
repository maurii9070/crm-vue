<script setup>
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
	</div>
</template>
