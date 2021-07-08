<template>
	<form action="" class="form" @submit="enviar">
		<my-input
			name="Usuario"
			:rules="{ required: true, min: 5 }"
			:value="usuario.value"
			@update="update"
			type="text"
		/>
		<!-- {{ usuario }} -->
		<my-input
			name="Password"
			:rules="{ required: true, min: 10 }"
			:value="password.value"
			@update="update"
			type="password"
		>
		</my-input>
		<Button 
      color="white" 
      background="darkslateblue" 
      :disabled="!valid" 
    />
	</form>
</template>

<script>
	import Button from "./components/Button.vue";
	import MyInput from "./components/MyInput.vue";

	export default {
		name: "App",
		components: {
			Button,
			MyInput,
		},
		data() {
			return {
				// valid: true,
				usuario: {
					value: "",
					valid: false,
				},
				password: {
					value: "",
					valid: false,
				},
			};
		},
		computed: {
			valid() {
				return this.usuario.valid && this.password.valid;
			},
		},
		methods: {
      enviar ($evt) {
        $evt.preventDefault();
        console.log( 'enviar' );
      },
			update(payload) {
				console.log(payload);
				this[payload.name.toLowerCase()] = {
					value: payload.value,
					valid: payload.valid,
				};
			},
		},
	};
</script>

<style>
	div {
		display: flex;
		flex-direction: column;
	}

	body {
		font-family: arial;
	}

  .form {
    max-width: 400px;
    width: 50%;
  }
</style>
