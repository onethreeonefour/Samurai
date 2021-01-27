<template>
	<div class="hero-container">
		<div class="hero-initial-anim">
			<div class="hydra">
				<h1>&lt; System rebooting &gt;</h1>
				<h3>Hydra Ver 2.1 Sys Recovery</h3>
				<h3>Process: {{ progress }}%</h3>
			</div>
		</div>
		<div class="hero-secondary-anim">
			<div class="text-container">
				<div class="glitch anim-text-1" data-text="wake the">wake the&#160;</div>
				<div class="glitch anim-text-1" data-text="fuck up">fuck up,&#160;</div>
				<div class="glitch anim-text-1" data-text="samurai">samurai</div>
				<br />
				<div class="glitch anim-text-2" data-text="we have">we have&#160;</div>
				<div class="glitch anim-text-2" data-text="a city">a city&#160;</div>
				<div class="glitch anim-text-2" data-text="to burn">to burn</div>
			</div>
		</div>
		<div class="hero-final-anim">
			<img src="../assets/Samurai.gif" alt="samurai" class="samurai" @load="onImgLoad" />
		</div>
	</div>
</template>
<script>
import { gsap } from "gsap";
export default {
	data() {
		return {
			isLoaded: false,
			progress: 0,
		};
	},
	methods: {
		onImgLoad() {
			this.isLoaded = true;
		},
	},
	mounted() {
		//animations
		gsap
			.timeline()
			.from(".anim-text-1", 1.5, {
				autoAlpha: 0,
				y: 100,
				stagger: 0.5,
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			})
			.from(".anim-text-2", 1.5, {
				autoAlpha: 0,
				y: -100,
				stagger: 0.5,
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			})
			.to(".text-container", 1.5, {
				delay: 1.25,
				display: "none",
				autoAlpha: 0,
				y: -200,
				stagger: 0.5,
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			})
			.to(".samurai", 0.25, {
				display: "block",
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			})
			.from(".hero-final-anim", 1.5, {
				autoAlpha: 0,
				y: -100,
				ease: "back",
			});
	},
};
</script>

<style lang="scss" scoped>
.hero-initial-anim {
	display: flex;
	height: 100vh;
	justify-content: center;
	align-items: center;
	color: red;
	text-transform: uppercase;
	.hydra {
		text-align: center;
		border: 4px solid red;
		padding: 3rem 5rem;
		font-family: "Dosis", sans-serif;
	}
}
.hero-secondary-anim {
	div {
		display: inline-block;
	}
	text-transform: uppercase;
	padding: 2rem;
}
.hero-final-anim {
	img {
		object-fit: cover;
		display: none;
		width: 50vw;
		height: 100%;
	}
}

.glitch {
	color: red;
	font-size: 5rem;
	position: relative;
	margin: 0 auto;
	font-weight: bolder;
}

@keyframes noise-anim {
	$steps: 20;
	@for $i from 0 through $steps {
		#{percentage($i*(1/$steps))} {
			clip: rect(random(100) + px, 9999px, random(100) + px, 0);
		}
	}
}
.glitch:after {
	content: attr(data-text);
	position: absolute;
	left: 2px;
	text-shadow: -2px 0 rgb(0, 255, 0);
	top: 0;
	color: red;
	background: black;
	overflow: hidden;
	clip: rect(0, 900px, 0, 0);
	animation: noise-anim 2s infinite linear alternate-reverse;
}

@keyframes noise-anim-2 {
	$steps: 20;
	@for $i from 0 through $steps {
		#{percentage($i*(1/$steps))} {
			clip: rect(random(100) + px, 9999px, random(100) + px, 0);
		}
	}
}
.glitch:before {
	content: attr(data-text);
	position: absolute;
	left: -2px;
	text-shadow: 2px 0 blue;
	top: 0;
	color: red;
	background: black;
	overflow: hidden;
	clip: rect(0, 900px, 0, 0);
	animation: noise-anim-2 3s infinite linear alternate-reverse;
}
</style>
