<template>
	<div class="card-container">
		<div class="explore-part">
			<span>
				<a :href="link" target="_blank"> EXPLORE! </a>
			</span>
		</div>
		<div class="project-card">
			<div class="header">
				<h2>{{ projectName }}</h2>
				<div class="tech-icons">
					<img v-for="(tech, index) in techStack" :key="index" :src="tech" />
				</div>
			</div>
			<div class="description">
				<p>{{ description }}</p>
			</div>
			<div class="maintainers">
				<h3>MAINTAINERS:</h3>
				<div class="maintainer-name">
					<h4>{{ maintainer1 }}</h4>
					<h4>{{ maintainer2 }}</h4>
					<h4>{{ maintainer3 }}</h4>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
export default {
	props: {
		projectName: {
			type: String,
			required: true,
		},
		maintainer1: {
			type: String,
			required: true,
		},
		maintainer2: {
			type: String,
			required: true,
		},
		maintainer3: {
			type: String,
			required: false,
		},
		link: {
			type: String,
			required: true,
		},
		techStack: {
			type: Array,
			required: true,
		},
		description: {
			type: String,
			required: true,
		},
	},
}
</script>
<style scoped>
.card-container {
	display: flex;
	height: auto;
	min-height: 330px;
	width: 100%;
	max-width: 600px;
	margin: 0 auto;
	align-items: stretch;
	background-color: #efefef;
	border-radius: 30px;
	border: 1.5px solid #efefef;
	transition:
		background-color 0.3s ease,
		border 0.3s ease;
	box-shadow:
		0 0 5px rgba(8, 145, 179, 0.6),
		0 0 15px rgba(8, 145, 179, 0.4),
		0 0 25px rgba(8, 145, 179, 0.2);
	box-sizing: border-box;
}

.explore-part {
	width: 80px;
	flex-shrink: 0;
	border-top-left-radius: 30px;
	border-bottom-left-radius: 30px;
	display: flex;
	justify-content: center;
	align-items: center;
}

.explore-part span {
	opacity: 0;
	visibility: hidden;
	writing-mode: vertical-rl;
	transform: rotate(180deg);
	font-family: 'Pricedown';
	font-size: clamp(28px, 6vw, 60px);
	color: #ffffff;
	text-align: center;
	justify-content: center;
	transition:
		opacity 0.3s ease,
		visibility 0.3s ease;
}

.card-container:hover .explore-part span {
	opacity: 1;
	visibility: visible;
}

a {
	text-decoration: none;
	color: inherit;
}

.project-card {
	background-color: #111;
	box-sizing: border-box;
	border-radius: 30px;
	padding: 20px;
	width: 100%;
	min-width: 0; 
	color: #efefef;
	font-family: sans-serif;
	box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
	transition: transform 0.3s ease;
}

.card-container:hover .project-card {
	transform: translateX(20px);
}

.header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	flex-wrap: wrap;
	gap: 8px;
	font-size: clamp(20px, 5vw, 36px);
}

.header h2 {
	margin: 0;
	word-break: break-word;
}

.tech-icons {
	display: flex;
	flex-wrap: wrap;
	gap: 10px;
}

.tech-icons img {
	height: clamp(20px, 4vw, 30px);
	width: auto;
}

.description {
	border: 1.5px solid white;
	padding: 12px;
	margin: 16px 0;
	font-size: clamp(14px, 3vw, 18px);
	text-align: left;
	transition:
		background-color 0.3s ease,
		border 0.3s ease;
}

.card-container:hover .description {
	border-color: #0891b3;
}

.maintainers {
	font-size: 10px;
	display: flex;
	flex-wrap: wrap;
	align-items: flex-start;
}

.maintainer-name {
	display: flex;
	flex-direction: column;
	align-items: flex-start;
	margin-left: 10px;
}


@media (max-width: 420px) {
	.card-container {
		flex-direction: column-reverse;
		height: auto;
	}

	.explore-part {
		width: 100%;
		height: 40px;
		border-radius: 20px 20px 0 0;
	}

	.explore-part span {
		writing-mode: horizontal-tb;
		transform: none;
		font-size: 20px;
	}

	.project-card {
		border-radius: 0 0 20px 20px;
	}

	.card-container:hover .project-card {
		transform: translateY(6px);
	}

	.header {
		flex-direction: column;
		align-items: flex-start;
	}
}
</style>
