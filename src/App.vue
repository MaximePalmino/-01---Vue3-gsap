<script>
import { gsap, Power3 } from "gsap";
export default {
	data() {
		return { state: false };
	},
	name: "App",
	methods: {
		clickHandler() {
			const { red } = this.$refs;
			const { circle } = this.$refs;

			const clickUp = () => {
				this.state = !this.state;
				gsap.to(red, { width: 150, height: 150, ease: Power3.easeOut });
				gsap.to(circle, {
					width: 75,
					height: 75,
					ease: Power3.easeOut,
				});
			};
			const clickDown = () => {
				this.state = !this.state;
				gsap.to(red, { width: 75, height: 75, ease: Power3.easeOut });
				gsap.to(circle, {
					width: 150,
					height: 150,
					ease: Power3.easeOut,
				});
			};

			if (this.state == false) {
				console.log("this is true", this.$refs.circle);
				clickUp();
			} else {
				console.log("this is false");
				clickDown();
			}
		},
	},
	mounted() {
		console.log(this.state);
		const { red } = this.$refs;
		const { circle } = this.$refs;
		gsap.from(red, {
			opacity: 0,
			x: 80,
			ease: Power3.easeOut,
			duration: 0.8,
			delay: 0.1,
		});
		gsap.from(circle, {
			opacity: 0,
			x: 80,
			ease: Power3.easeOut,
			duration: 0.8,
			delay: 0.4,
		});
	},
};
</script>
<template>
	<div class="container">
		<div @click="clickHandler" ref="red" class="red"></div>
		<div class="orange" ref="circle" @click="clickHandler"></div>
	</div>
</template>

<style>
#app {
	height: 100vh;
	display: flex;
	flex-direction: column;
	justify-items: center;
	align-items: center;
}
.container {
	height: 100vh;
	display: flex;
	justify-items: center;
	align-items: center;
}
.red {
	background-color: #ff5f6d;
	margin: 30px;
	opacity: 1;
	width: 75px;
	height: 75px;
	border-radius: 100%;
}
.red:hover {
	cursor: pointer;
}

.orange {
	background-color: #ffc371;
	width: 75px;
	height: 75px;
	border-radius: 100%;
	margin: 30px;
}
.orange:hover {
	cursor: pointer;
}
</style>
