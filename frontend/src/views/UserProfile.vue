<template>
	<div v-if="currentUser">
		<header class="jumbotron bg-secondary">
			<h3>
				<span class="text-white"> Xin chào người dùng </span>
				<strong class="text-warning">  {{ currentUser.username }}</strong>
				<br>
				<br>
				<span class="text-white" style="font-style: italic; font-size: large;"> Chào mừng bạn đã đến với ứng dụng quản lý phim được ưa chuộng</span> 
				<br>
				<br>
				<span class="text-white" style="font-style: italic; font-size: large;">Cùng chúng tôi trải nghiệm nhé ! </span> 
			</h3>
		</header>
		<div class="row">
			<div class="col-md-8">
				<p class="text-break">
					<strong>Token:</strong>
					{{ currentUser.accessToken }}
				</p>
				<p>
					<strong>Id:</strong>
					{{ currentUser._id }}
				</p>
				<p>
					<strong>E-mail:</strong>
					{{ currentUser.email }}
				</p>
			</div>
		</div>
	</div>
</template>

<script>
import { mapState } from "pinia";
import { useAuthStore } from "@/stores/auth.store";

export default {
	computed: {
		...mapState(useAuthStore, {
			currentUser: "user",
		}),
	},
	created() {
		if (!this.currentUser) {
			this.$router.push({ name: "login" });
		}
	},
};
</script>
