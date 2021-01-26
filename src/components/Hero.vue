<template>
	<div class="hero-container">
		<div class="hero-text">
			<div class="text-container" ref="box">
				<div>
					<div class="glitch anim-text-1" data-text="wake the">wake the</div>
					<div class="glitch anim-text-1" data-text="fuck up">fuck up</div>
					<div class="glitch anim-text-1" data-text="samurai">samurai</div>
				</div>
				<div class="right">
					<div class="glitch anim-text-2" data-text="we have">we have</div>
					<div class="glitch anim-text-2" data-text="a city">a city</div>
					<div class="glitch anim-text-2" data-text="to burn">to burn</div>
				</div>
				<div class="cta">
					<a href="#"> Join The Fight </a>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
import { gsap } from "gsap";
export default {
	mounted() {
		gsap
			.timeline()
			.from(".hero-container", 2, {
				autoAlpha: 0,
				height: 0,
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			})
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
			.from(".cta", 1.5, {
				autoAlpha: 0,
				x: 200,
				stagger: 0.5,
				ease: "rough({ template: none.out, strength: 1, points: 20, taper: 'none', randomize: true, clamp: false})",
			});
	},
};
</script>

<style lang="scss" scoped>
.hero-text {
	z-index: 500;
	text-transform: uppercase;
	display: flex;
	height: 100vh;
	align-items: center;
	padding: 2rem;
}

.glitch {
	color: red;
	font-size: 5rem;
	position: relative;
	margin: 0 auto;
	font-weight: bolder;
}
.text-container {
	display: inline;
	width: 100%;
	.right {
		float: right;
	}
}
.cta {
	position: absolute;
	bottom: 25%;
	a {
		background: #000;
		border: 4px solid red;
		padding: 2rem 3rem;
		display: block;
		font-weight: bolder;
		color: red;
		font-size: 1.2rem;
		transition: ease-in-out 0.4s all;
	}
	a:hover {
		background: red;
		color: #000;
	}
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
