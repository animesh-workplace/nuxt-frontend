<template>
	<v-container>
		<h1>Login</h1>
		<UserAuthForm buttonText="Login" :submitForm="loginUser"/>
	</v-container>
</template>

<script>
import UserAuthForm from '@/components/authform'
	export default {
		components: {
			UserAuthForm
		},
		methods: {
			loginUser(loginInfo) {
				this.$auth.loginWith('local', {
					data: loginInfo
				})
				// alert('you pressed it')
			}
		}
	};
</script>