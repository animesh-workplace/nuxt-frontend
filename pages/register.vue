<template>
	<v-container>
		<h1>Register</h1>
		<UserAuthForm buttonText="Register" :submitForm="registerUser" hasName="True"/>
	</v-container>
</template>

<script>
import UserAuthForm from '@/components/authform'
	export default {
		components: {
			UserAuthForm
		},
		methods: {
			registerUser() {
				alert('you pressed it')
			}
		}
	};
</script>