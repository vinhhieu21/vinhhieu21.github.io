<script>
	import { onMount } from 'svelte';

	const email = 'buivinhhieu217@gmail.com';

	const links = [
		{ label: 'GitHub', href: 'https://github.com/vinhhieu21', external: true },
		{ label: 'Email', href: `mailto:${email}` },
		{ label: '+84 978 713 957', href: 'tel:+84978713957' }
	];

	const experience = [
		{
			company: 'playSTUDIOS',
			role: 'Java Backend Engineer',
			location: 'Hanoi',
			period: '2025 - Now',
			items: [
				'Build backend services for POP! Slots live game features: tournaments, dynamic bets, sale and version configuration, and sweepstakes.',
				'Take part in design and code reviews for scalable live game service architecture.',
				'Work with product, client, and DevOps teams to ship features reliably.'
			],
			stack: ['Java', 'Spring', 'Microservices']
		},
		{
			company: 'CIMB Bank Thai',
			role: 'Senior Backend Engineer',
			location: 'Remote',
			period: '2023 - 2025',
			items: [
				'Built microservices for digital banking and investment products.',
				'Designed APIs and background workers over REST, gRPC, Kafka, and RabbitMQ, serving thousands of daily license requests with no production incidents.',
				'Led products end to end, from requirements and partner coordination to load testing, observability, and delivery.'
			],
			stack: ['Java 17', 'Spring Boot', 'MySQL', 'Redis', 'Kafka', 'RabbitMQ', 'AWS', 'ArgoCD']
		},
		{
			company: 'IBM APAC',
			role: 'Software Development Engineer',
			location: 'Remote',
			period: '2021 - 2023',
			items: [
				'Built enterprise fintech applications for IBM EngageAR.',
				'Developed and rolled out the HECP automation letters feature on IBM Cloud and Kubernetes.',
				'Applied event-driven architecture, the Saga pattern, and TDD in a global Agile team across NA, EMEA, and APAC.'
			],
			stack: ['Java 8', 'Spring', 'DB2', 'Cloudant', 'Kubernetes']
		},
		{
			company: 'Viettel',
			role: 'Software Engineer',
			location: 'Hanoi',
			period: '2020 - 2021',
			items: [
				'Implemented RESTful APIs and Kafka consumers for Viettel Post.',
				'Built employee information search for internal systems.'
			],
			stack: ['Java', 'Spring Boot', 'Kafka', 'PostgreSQL', 'MongoDB', 'Oracle']
		}
	];

	const skills = [
		{ group: 'Languages', items: 'Java, Go, Python, SQL' },
		{ group: 'Frameworks', items: 'Spring Boot, Spring, gRPC' },
		{ group: 'Messaging', items: 'Kafka, RabbitMQ' },
		{ group: 'Data', items: 'MySQL, PostgreSQL, Redis, MongoDB, Oracle, DB2' },
		{ group: 'Infrastructure', items: 'AWS, Kubernetes, Docker, Jenkins, ArgoCD' },
		{ group: 'Observability', items: 'Datadog, CloudWatch, Grafana, Zipkin, JMeter' },
		{ group: 'Practices', items: 'Microservices, event-driven design, Saga, TDD' }
	];

	let theme = $state('light');

	function toggleTheme() {
		theme = theme === 'dark' ? 'light' : 'dark';
		document.documentElement.dataset.theme = theme;
		localStorage.setItem('theme', theme);
	}

	onMount(() => {
		theme = document.documentElement.dataset.theme || 'light';
	});
</script>

<svelte:head>
	<title>Hieu Bui Vinh - Backend Engineer</title>
	<meta
		name="description"
		content="Hieu Bui Vinh is a backend engineer in Hanoi building Java and Spring microservices, event-driven systems, and cloud-native platforms."
	/>
</svelte:head>

<div class="page">
	<header class="intro">
		<div class="intro-top">
			<h1>Hieu Bui Vinh</h1>
			<button
				class="theme-toggle"
				type="button"
				aria-label={theme === 'dark' ? 'Switch to light theme' : 'Switch to dark theme'}
				onclick={toggleTheme}
			>
				{#if theme === 'dark'}
					<svg viewBox="0 0 24 24" aria-hidden="true">
						<circle cx="12" cy="12" r="4" />
						<path
							d="M12 2v2M12 20v2M4.93 4.93l1.41 1.41M17.66 17.66l1.41 1.41M2 12h2M20 12h2M4.93 19.07l1.41-1.41M17.66 6.34l1.41-1.41"
						/>
					</svg>
				{:else}
					<svg viewBox="0 0 24 24" aria-hidden="true">
						<path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z" />
					</svg>
				{/if}
			</button>
		</div>
		<p class="role">Backend Engineer · Hanoi, Vietnam</p>
		<p class="summary">
			I build backend systems for real products in live games, digital banking, fintech, and
			logistics. Since 2020 I have worked on Java and Spring microservices, event-driven pipelines,
			and cloud-native delivery, with a focus on services that stay reliable, observable, and easy
			to change.
		</p>
		<ul class="links">
			{#each links as link}
				<li>
					<a
						href={link.href}
						target={link.external ? '_blank' : undefined}
						rel={link.external ? 'noreferrer' : undefined}>{link.label}</a
					>
				</li>
			{/each}
		</ul>
	</header>

	<main>
		<section aria-labelledby="experience">
			<h2 id="experience">Experience</h2>
			<ol class="jobs">
				{#each experience as job}
					<li class="job">
						<p class="period">{job.period}</p>
						<div>
							<h3>{job.company}</h3>
							<p class="job-role">{job.role} · {job.location}</p>
							<ul class="job-items">
								{#each job.items as item}
									<li>{item}</li>
								{/each}
							</ul>
							<ul class="stack" aria-label="Tech stack">
								{#each job.stack as tech}
									<li>{tech}</li>
								{/each}
							</ul>
						</div>
					</li>
				{/each}
			</ol>
		</section>

		<section aria-labelledby="skills">
			<h2 id="skills">Skills</h2>
			<dl class="skills">
				{#each skills as skill}
					<div>
						<dt>{skill.group}</dt>
						<dd>{skill.items}</dd>
					</div>
				{/each}
			</dl>
		</section>

		<section aria-labelledby="education">
			<h2 id="education">Education</h2>
			<dl class="skills">
				<div>
					<dt>Degree</dt>
					<dd>Computer Science, Military Technical Academy</dd>
				</div>
				<div>
					<dt>English</dt>
					<dd>Professional working proficiency (TOEIC 870)</dd>
				</div>
			</dl>
		</section>

		<section aria-labelledby="contact">
			<h2 id="contact">Contact</h2>
			<p class="contact">
				Open to backend and distributed systems roles. The fastest way to reach me is
				<a href={`mailto:${email}`}>{email}</a>.
			</p>
		</section>
	</main>

	<footer>
		<span>© {new Date().getFullYear()} Hieu Bui Vinh</span>
		<a href="https://github.com/vinhhieu21/vinhhieu21.github.io" target="_blank" rel="noreferrer"
			>Source</a
		>
	</footer>
</div>

<style>
	:global(html) {
		--bg: #ffffff;
		--text: #18181b;
		--muted: #52525b;
		--faint: #71717a;
		--line: #e4e4e7;
		--chip: #f4f4f5;
		--accent: #2563eb;
		color-scheme: light;
		background: var(--bg);
		color: var(--text);
		-webkit-text-size-adjust: 100%;
	}

	:global(html[data-theme='dark']) {
		--bg: #0f0f11;
		--text: #e4e4e7;
		--muted: #a1a1aa;
		--faint: #8b8b94;
		--line: #27272a;
		--chip: #1c1c1f;
		--accent: #60a5fa;
		color-scheme: dark;
	}

	:global(body) {
		margin: 0;
		font-family:
			ui-sans-serif,
			system-ui,
			-apple-system,
			'Segoe UI',
			Roboto,
			'Helvetica Neue',
			Arial,
			sans-serif;
		font-size: 16px;
		line-height: 1.6;
		-webkit-font-smoothing: antialiased;
	}

	:global(::selection) {
		background: color-mix(in srgb, var(--accent) 25%, transparent);
	}

	:global(:focus-visible) {
		outline: 2px solid var(--accent);
		outline-offset: 2px;
		border-radius: 2px;
	}

	.page {
		--mono: ui-monospace, 'SF Mono', SFMono-Regular, Menlo, Consolas, monospace;
		max-width: 44rem;
		margin: 0 auto;
		padding: 5rem 1.5rem 3rem;
	}

	a {
		color: var(--text);
		text-decoration: underline;
		text-decoration-color: var(--line);
		text-underline-offset: 3px;
		transition: text-decoration-color 150ms ease;
	}

	a:hover {
		text-decoration-color: var(--accent);
	}

	h1,
	h2,
	h3,
	p,
	ul,
	ol,
	dl,
	dd {
		margin: 0;
	}

	ul,
	ol {
		padding: 0;
		list-style: none;
	}

	/* Intro */

	.intro-top {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
	}

	h1 {
		font-size: 1.75rem;
		font-weight: 600;
		letter-spacing: -0.02em;
		line-height: 1.2;
	}

	.theme-toggle {
		display: grid;
		place-items: center;
		width: 2.25rem;
		height: 2.25rem;
		padding: 0;
		border: 1px solid var(--line);
		border-radius: 8px;
		background: transparent;
		color: var(--muted);
		cursor: pointer;
		transition:
			color 150ms ease,
			border-color 150ms ease;
	}

	.theme-toggle:hover {
		color: var(--text);
		border-color: var(--faint);
	}

	.theme-toggle svg {
		width: 1.05rem;
		height: 1.05rem;
		fill: none;
		stroke: currentColor;
		stroke-width: 2;
		stroke-linecap: round;
		stroke-linejoin: round;
	}

	.role {
		margin-top: 0.25rem;
		color: var(--muted);
	}

	.summary {
		margin-top: 1.5rem;
		color: var(--muted);
	}

	.links {
		display: flex;
		flex-wrap: wrap;
		gap: 0.5rem 1.5rem;
		margin-top: 1.5rem;
		font-size: 0.9375rem;
	}

	/* Sections */

	section {
		margin-top: 4rem;
	}

	h2 {
		margin-bottom: 1.5rem;
		font-family: var(--mono);
		font-size: 0.8125rem;
		font-weight: 500;
		letter-spacing: 0.04em;
		text-transform: uppercase;
		color: var(--faint);
	}

	/* Experience */

	.jobs {
		display: grid;
		gap: 2.5rem;
	}

	.job {
		display: grid;
		grid-template-columns: 7.5rem minmax(0, 1fr);
		gap: 1rem;
	}

	.period {
		padding-top: 0.15rem;
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--faint);
		white-space: nowrap;
	}

	h3 {
		font-size: 1rem;
		font-weight: 600;
		line-height: 1.5;
	}

	.job-role {
		color: var(--muted);
		font-size: 0.9375rem;
	}

	.job-items {
		display: grid;
		gap: 0.375rem;
		margin-top: 0.75rem;
		color: var(--muted);
		font-size: 0.9375rem;
	}

	.job-items li {
		position: relative;
		padding-left: 1rem;
	}

	.job-items li::before {
		content: '';
		position: absolute;
		left: 0;
		top: 0.8em;
		width: 0.375rem;
		height: 1px;
		background: var(--faint);
	}

	.stack {
		display: flex;
		flex-wrap: wrap;
		gap: 0.375rem;
		margin-top: 0.875rem;
	}

	.stack li {
		padding: 0.125rem 0.5rem;
		border-radius: 4px;
		background: var(--chip);
		font-family: var(--mono);
		font-size: 0.75rem;
		line-height: 1.6;
		color: var(--muted);
	}

	/* Skills and education */

	.skills {
		display: grid;
		gap: 0.625rem;
	}

	.skills div {
		display: grid;
		grid-template-columns: 7.5rem minmax(0, 1fr);
		gap: 1rem;
	}

	dt {
		font-family: var(--mono);
		font-size: 0.8125rem;
		line-height: 1.85;
		color: var(--faint);
	}

	dd {
		font-size: 0.9375rem;
	}

	.contact {
		color: var(--muted);
	}

	footer {
		display: flex;
		justify-content: space-between;
		gap: 1rem;
		margin-top: 5rem;
		padding-top: 1.5rem;
		border-top: 1px solid var(--line);
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--faint);
	}

	footer a {
		color: var(--faint);
	}

	@media (max-width: 600px) {
		.page {
			padding-top: 3rem;
		}

		section {
			margin-top: 3rem;
		}

		.job,
		.skills div {
			grid-template-columns: 1fr;
			gap: 0.25rem;
		}

		.skills {
			gap: 1rem;
		}

		.period {
			order: -1;
		}
	}
</style>
