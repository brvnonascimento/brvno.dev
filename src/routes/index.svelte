<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">
	// import ProfilePhoto from '/profile-photo.jpg?w=100&h=100&webp';
	import Container from '$lib/Container.svelte';
	import GithubIcon from '$lib/icons/GitHubIcon.svelte';
	import LinkedInIcon from '$lib/icons/LinkedInIcon.svelte';
	import { onMount } from 'svelte';

	let ParticlesComponent;

	onMount(async () => {
		const module = await import('svelte-particles');

		ParticlesComponent = module.default;
	});

	const particlesConfig = {
		particles: {
			number: {
				value: 355,
				density: {
					enable: true,
					value_area: 789.1476416322727
				}
			},
			color: {
				value: '#ffffff'
			},
			shape: {
				type: 'circle',
				stroke: {
					width: 0,
					color: '#000000'
				},
				polygon: {
					nb_sides: 5
				}
			},
			opacity: {
				value: 0.48927153781200905,
				random: false,
				anim: {
					enable: true,
					speed: 0.2,
					opacity_min: 0,
					sync: false
				}
			},
			size: {
				value: 2,
				random: true,
				anim: {
					enable: true,
					speed: 2,
					size_min: 0,
					sync: false
				}
			},
			line_linked: {
				enable: false,
				distance: 150,
				color: '#ffffff',
				opacity: 0.4,
				width: 1
			},
			move: {
				enable: true,
				speed: 0.2,
				direction: 'none',
				random: true,
				straight: false,
				out_mode: 'out',
				bounce: false,
				attract: {
					enable: false,
					rotateX: 600,
					rotateY: 1200
				}
			}
		},
		interactivity: {
			detect_on: 'canvas',
			events: {
				onhover: {
					enable: true,
					mode: 'bubble'
				},
				onclick: {
					enable: true,
					mode: 'push'
				},
				resize: true
			},
			modes: {
				grab: {
					distance: 400,
					line_linked: {
						opacity: 1
					}
				},
				bubble: {
					distance: 83.91608391608392,
					size: 1,
					duration: 3,
					opacity: 1,
					speed: 3
				},
				repulse: {
					distance: 200,
					duration: 0.4
				},
				push: {
					particles_nb: 4
				},
				remove: {
					particles_nb: 2
				}
			}
		},
		retina_detect: true
	};

	const links = [
		{
			title: 'GitHub',
			Icon: GithubIcon,
			href: 'https://github.com/brvnonascimento'
		},
		{
			title: 'LinkedIn',
			Icon: LinkedInIcon,
			href: 'https://www.linkedin.com/in/bruno-henrique-nascimento-62a65416a/?locale=en_US'
		}
	];
</script>

<svelte:head>
	<title>Bruno Nascimento - UI Engineer</title>
	<meta
		name="description"
		content="UI Engineer with focus on Web Development using cutting-edge technologies such as React and Svelte. Lover of the JAM Stack and matching high complexity business logic with a beautiful UI experience."
	/>
</svelte:head>

<section class="hero">
	<svelte:component this={ParticlesComponent} id="particles-container" options={particlesConfig} />

	<Container class="hero-content">
		<div class="personal-info">
			<img
				class="hero-profile-photo"
				alt="Bruno Nascimento Profile Photo"
				src="/profile-photo.jpg"
				width="100"
				height="100"
				loading="lazy"
			/>

			<div>
				<h1 class="personal-info__heading">Bruno Nascimento</h1>
				<h2>UI Engineer</h2>
				<h3>Powered by <span class="typescript-label">Typescript</span></h3>
				<p class="personal-info__description">
					UI Engineer with focus on Web Development using cutting-edge technologies such as React
					and Svelte. Lover of the JAM Stack and matching high complexity business logic with a
					beautiful UI experience.
				</p>

				<ul class="personal-info__links" aria-label="Social Media Links">
					{#each links as { title, Icon, href }}
						<li class="personal-info__links__link">
							<a target="_blank" rel="noopener" {href} {title} aria-label={title}>
								<Icon width={24} height={24} />
							</a>
						</li>
					{/each}
				</ul>
			</div>
		</div>
	</Container>
</section>

<style lang="scss">
	@import '../styles/breakpoint';

	:global(#particles-container) {
		position: absolute;
		width: 100%;
		height: 100%;
	}

	.hero {
		display: flex;
		min-height: 100vh;
		align-items: center;
		background: var(--color-bg-primary);
	}

	:global(.hero-content) {
		z-index: 1;
		grid-area: 2 / 1 / 3 / 3;
		height: min-content;
	}

	:global(.hero-profile-photo) {
		--image-padding-effect: 2rem;
		--offset: calc(var(--image-padding-effect) / 2);

		object-fit: cover;
		border-radius: 50%;
		padding: 0 var(--image-padding-effect) var(--image-padding-effect) 0;
		position: relative;
		left: var(--offset);
		top: var(--offset);

		@include md {
			left: 0;
		}
	}

	.personal-info {
		display: grid;
		row-gap: 1rem;
		column-gap: 1.5rem;
		justify-items: center;
		align-items: center;
		text-align: center;

		@include md {
			margin: 0 auto;
		}

		&__heading {
			color: tomato;
		}

		&__description {
			max-width: 45ch;
			padding: 1rem 0;
		}

		&__links {
			display: flex;
			justify-content: center;
			padding: 1rem 0;

			@include md {
				justify-content: unset;
			}

			&__link {
				&:not(:last-child) {
					margin-right: 1rem;
				}
			}
		}

		.typescript-label {
			color: var(--color-typescript);
		}

		@include md {
			text-align: left;
			width: max-content;
			grid-template-columns: 100px 1fr;
			justify-items: unset;
			align-items: unset;
		}
	}
</style>
