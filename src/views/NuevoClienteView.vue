<script setup>
	import axios from 'axios';
	import { FormKit } from '@formkit/vue';

	import { useRouter } from 'vue-router';

	import Heading from '../components/ui/Heading.vue';
	import RouterLink from '../components/ui/RouterLink.vue';

	const router = useRouter();

	defineProps({
		titulo: {
			type: String,
		},
	});

	const handleSubmit = data => {
		axios
			.post('http://localhost:4000/clientes', data)
			.then(respuesta => {
				// Redireccionar
				console.log(respuesta);
				router.push({ name: 'listado-cliente' });
			})
			.catch(error => console.log('Error'));
	};
</script>

<template>
	<div>
		<div class="flex justify-end">
			<RouterLink to="listado-cliente">Volver</RouterLink>
		</div>

		<Heading>{{ titulo }}</Heading>
		<div class="mx-auto mt-10 bg-white shadow">
			<div class="mx-auto md:w-2/3 py-20 px-6">
				<FormKit
					type="form"
					submit-label="Agregar Cliente"
					incomplete-message="No se pudo enviar, revisar los mensajes"
					@submit="handleSubmit"
				>
					<FormKit
						type="text"
						label="Nombre"
						name="nombre"
						placeholder="Nombre del Cliente"
						validation="required"
						:validation-messages="{ required: 'El nombre del cliente es obligatorio' }"
					/>

					<FormKit
						type="text"
						label="Apellido"
						name="apellido"
						placeholder="Apellido del Cliente"
						validation="required"
						:validation-messages="{ required: 'El apellido del cliente es obligatorio' }"
					/>

					<FormKit
						type="email"
						label="Email"
						name="email"
						placeholder="Email del Cliente"
						validation="required|email"
						:validation-messages="{
							required: 'El email del cliente es obligatorio',
							email: 'Coloca un email valido',
						}"
					/>

					<FormKit
						type="text"
						label="Telefono"
						name="telefono"
						placeholder="Telefono: XXX-XXX-XXXX"
						validation="*matches:/^[0-9]{3}-[0-9]{3}-[0-9]{4}/"
						:validation-messages="{ matches: 'El formato no es valido' }"
					/>

					<FormKit
						type="text"
						label="Empresa"
						name="empresa"
						placeholder="Empresa del Cliente"
					/>

					<FormKit
						type="text"
						label="Puesto"
						name="puesto"
						placeholder="Puesto del Cliente"
					/>
				</FormKit>
			</div>
		</div>
	</div>
</template>

<style>
	.formkit-wrapper {
		max-width: 100%;
	}
</style>
