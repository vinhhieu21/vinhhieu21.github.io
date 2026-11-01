<script>
	import { onMount } from 'svelte';

	const email = 'buivinhhieu217@gmail.com';
	const github = 'https://github.com/vinhhieu21';
	const phone = '+84 978 713 957';

	const nav = [
		{ href: '#work', label: 'Work' },
		{ href: '#skills', label: 'Skills' },
		{ href: '#contact', label: 'Contact' }
	];

	const work = [
		{
			company: 'playSTUDIOS',
			role: 'Java Backend Engineer, Hanoi',
			period: '2025-now',
			summary:
				"Backend services for POP! Slots live game features: tournaments, dynamic bets, sale and version configuration, and sweepstakes. I also built the Server team's AI engineering kit.",
			stack: ['Java', 'Spring', 'Microservices', 'TypeScript', 'AI agents']
		},
		{
			company: 'CIMB Bank Thai',
			role: 'Senior Backend Engineer, remote',
			period: '2023-2025',
			summary:
				'Microservices for digital banking and investment products over REST, gRPC, Kafka, and RabbitMQ, serving thousands of daily license requests with no production incidents. I led products from requirements to load testing and delivery.',
			stack: ['Java 17', 'Spring Boot', 'MySQL', 'Redis', 'Kafka', 'RabbitMQ', 'AWS', 'ArgoCD']
		},
		{
			company: 'IBM APAC',
			role: 'Software Development Engineer, remote',
			period: '2021-2023',
			summary:
				'Enterprise fintech applications for IBM EngageAR, including the HECP automation letters feature on IBM Cloud and Kubernetes, in a global Agile team across NA, EMEA, and APAC.',
			stack: ['Java 8', 'Spring', 'DB2', 'Cloudant', 'Kubernetes']
		},
		{
			company: 'Viettel',
			role: 'Software Engineer, Hanoi',
			period: '2020-2021',
			summary: 'RESTful APIs and Kafka consumers for Viettel Post, plus employee information search for internal systems.',
			stack: ['Java', 'Spring Boot', 'Kafka', 'PostgreSQL', 'MongoDB', 'Oracle']
		}
	];

	const skills = [
		{ group: 'AI engineering', items: 'Agent harness, skills, commands, and automation' },
		{ group: 'Languages', items: 'Java, Go, Python, SQL' },
		{ group: 'Frameworks', items: 'Spring Boot, Spring, gRPC' },
		{ group: 'Messaging', items: 'Kafka, RabbitMQ' },
		{ group: 'Data', items: 'MySQL, PostgreSQL, Redis, MongoDB, Oracle, DB2' },
		{ group: 'Infrastructure', items: 'AWS, Kubernetes, Docker, Jenkins, ArgoCD' },
		{ group: 'Observability', items: 'Datadog, CloudWatch, Grafana, Zipkin, JMeter' },
		{ group: 'Education', items: 'Computer Science, Military Technical Academy' },
		{ group: 'English', items: 'Professional working proficiency, TOEIC 870' }
	];

	const contact = [
		{ label: 'Email', value: email, href: `mailto:${email}` },
		{ label: 'GitHub', value: 'vinhhieu21', href: github, external: true },
		{ label: 'Phone', value: phone, href: `tel:${phone.replaceAll(' ', '')}` }
	];

	const clock = new Intl.DateTimeFormat('en-GB', {
		timeZone: 'Asia/Ho_Chi_Minh',
		hour: '2-digit',
		minute: '2-digit'
	});

	let theme = $state('light');
	/** Hanoi local time. Empty until mount so the prerendered page never shows a stale time. */
	let localTime = $state('');

	function toggleTheme() {
		theme = theme === 'dark' ? 'light' : 'dark';
		document.documentElement.dataset.theme = theme;
		localStorage.setItem('theme', theme);
		syncThemeColor();
	}

	/** Keeps the mobile browser chrome the same color as the page background. */
	function syncThemeColor() {
		const bg = getComputedStyle(document.documentElement).getPropertyValue('--bg').trim();
		document.querySelector('meta[name="theme-color"]')?.setAttribute('content', bg);
	}

	onMount(() => {
		theme = document.documentElement.dataset.theme || 'light';
		syncThemeColor();

		/** @type {ReturnType<typeof setTimeout>} */
		let timer;
		const tick = () => {
			const now = new Date();
			localTime = clock.format(now);
			timer = setTimeout(tick, 60_000 - (now.getTime() % 60_000));
		};
		tick();
		return () => clearTimeout(timer);
	});
</script>

<svelte:head>
	<title>Hieu Bui Vinh - Backend Engineer</title>
	<meta
		name="description"
		content="Hieu Bui Vinh is a backend engineer in Hanoi building Java and Spring microservices, event-driven systems, and an AI engineering kit for the Server team at playSTUDIOS."
	/>
</svelte:head>

<header class="topbar">
	<a class="brand" href="#top">Hieu Bui Vinh</a>
	<nav aria-label="Primary">
		{#each nav as link}
			<a href={link.href}>{link.label}</a>
		{/each}
	</nav>
	<button
		class="theme-toggle"
		type="button"
		aria-label={theme === 'dark' ? 'Switch to light theme' : 'Switch to dark theme'}
		onclick={toggleTheme}
	>
		<svg viewBox="0 0 16 16" aria-hidden="true">
			<circle cx="8" cy="8" r="6.25" />
			<path d="M8 1.75a6.25 6.25 0 0 1 0 12.5z" />
		</svg>
	</button>
</header>

<main id="top" class="column">
	<section class="intro">
		<p class="locale">
			<span class="locale-dot" aria-hidden="true"></span>
			Hanoi, Vietnam
			<span class="meta"><time class="locale-time">{localTime}</time> GMT+7</span>
		</p>
		<h1>Hi, I'm Hieu.</h1>
		<p class="lede">
			Backend engineer at playSTUDIOS in Hanoi. I build Java and Spring services that stay reliable in
			production, and the AI kit my team ships with.
		</p>
		<p class="intro-links">
			<a href={`mailto:${email}`}>Email me</a>
			<a href={github} target="_blank" rel="noreferrer">GitHub</a>
		</p>
	</section>

	<section aria-labelledby="work">
		<h2 id="work">Work</h2>
		<ol class="rows">
			{#each work as job}
				<li class="job">
					<div class="row-head">
						<h3>{job.company}</h3>
						<span class="meta">{job.period}</span>
					</div>
					<p class="job-role">{job.role}</p>
					<p class="job-summary">{job.summary}</p>
					<ul class="job-stack" aria-label="Tech stack">
						{#each job.stack as tech}
							<li>{tech}</li>
						{/each}
					</ul>
				</li>
			{/each}
		</ol>
	</section>

	<section aria-labelledby="skills">
		<h2 id="skills">Skills</h2>
		<dl class="rows">
			{#each skills as skill}
				<div class="row-head pair">
					<dt>{skill.group}</dt>
					<dd>{skill.items}</dd>
				</div>
			{/each}
		</dl>
	</section>

	<section aria-labelledby="contact">
		<h2 id="contact">Contact</h2>
		<ul class="rows">
			{#each contact as item}
				<li>
					<a
						class="row-head pair"
						href={item.href}
						target={item.external ? '_blank' : undefined}
						rel={item.external ? 'noreferrer' : undefined}
					>
						<span class="contact-label">{item.label}</span>
						<span class="meta">{item.value}</span>
					</a>
				</li>
			{/each}
		</ul>
	</section>
</main>

<footer class="footer">
	<nav aria-label="Footer">
		<a href="#top">Home</a>
		{#each nav as link}
			<a href={link.href}>{link.label}</a>
		{/each}
	</nav>
	<a href="https://github.com/vinhhieu21/vinhhieu21.github.io" target="_blank" rel="noreferrer"
		>© {new Date().getFullYear()} Hieu Bui Vinh</a
	>
</footer>

<style>
	:global(html) {
		--bg: #f7f5ef;
		--surface: #fbfaf6;
		--text: #17160f;
		--muted: #403e35;
		--faint: #6f6b5e;
		--line: #e2ded2;
		--track: #ebe7dc;
		--accent: #047857;
		--serif: Charter, 'Iowan Old Style', 'Bitstream Charter', 'Sitka Text', Cambria, Georgia, serif;
		--sans: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
		--mono: ui-monospace, 'SF Mono', SFMono-Regular, Menlo, Consolas, monospace;
		color-scheme: light;
		background: var(--bg);
		color: var(--text);
		scroll-behavior: smooth;
		-webkit-text-size-adjust: 100%;
	}

	:global(html[data-theme='dark']) {
		--bg: #12110f;
		--surface: #181714;
		--text: #ece8dd;
		--muted: #c4bfb1;
		--faint: #8e897c;
		--line: #2b2924;
		--track: #23211d;
		--accent: #34d399;
		color-scheme: dark;
	}

	:global(*),
	:global(*::before),
	:global(*::after) {
		box-sizing: border-box;
	}

	:global(body) {
		margin: 0;
		font-family: var(--sans);
		font-size: 1rem;
		line-height: 1.6;
		-webkit-font-smoothing: antialiased;
	}

	:global(h1),
	:global(h2),
	:global(h3),
	:global(p),
	:global(ol),
	:global(ul),
	:global(dl),
	:global(dd),
	:global(figure) {
		margin: 0;
	}

	:global(ol),
	:global(ul) {
		padding: 0;
		list-style: none;
	}

	:global(a) {
		color: inherit;
		text-decoration: none;
	}

	:global(a:focus-visible),
	:global(button:focus-visible) {
		outline: 2px solid var(--accent);
		outline-offset: 3px;
		border-radius: 2px;
	}

	p {
		text-wrap: pretty;
	}

	/* Top bar */

	.topbar {
		display: flex;
		align-items: center;
		gap: 1.5rem;
		padding: 1.5rem 2rem;
	}

	.brand {
		white-space: nowrap;
		margin-right: auto;
		font-size: 0.8125rem;
		font-weight: 700;
		letter-spacing: 0.08em;
		text-transform: uppercase;
	}

	nav {
		display: flex;
		gap: 1.25rem;
	}

	.brand,
	nav a,
	.footer > a,
	.intro-links a {
		display: inline-block;
		padding-block: 0.25rem;
	}

	nav a {
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--muted);
	}

	nav a:hover {
		color: var(--text);
	}

	.theme-toggle {
		display: grid;
		place-items: center;
		width: 2rem;
		height: 2rem;
		padding: 0;
		border: 1px solid var(--line);
		border-radius: 4px;
		background: transparent;
		color: var(--text);
		cursor: pointer;
	}

	.theme-toggle:hover {
		border-color: var(--faint);
	}

	.theme-toggle svg {
		width: 0.875rem;
		height: 0.875rem;
		fill: none;
		stroke: currentColor;
		stroke-width: 1.5;
	}

	.theme-toggle path {
		fill: currentColor;
		stroke: none;
	}

	/* Layout */

	.column {
		width: min(41rem, 100% - 3rem);
		margin-inline: auto;
	}

	section {
		margin-top: 4.5rem;
	}

	/* Intro */

	.intro {
		margin-top: 4.5rem;
		padding-bottom: 2.5rem;
		border-bottom: 1px solid var(--line);
	}

	.locale {
		display: flex;
		align-items: center;
		gap: 0.5rem;
		margin-bottom: 1.25rem;
		font-size: 0.875rem;
		color: var(--muted);
	}

	.locale-dot {
		width: 0.4375rem;
		height: 0.4375rem;
		border-radius: 50%;
		background: var(--accent);
	}

	.locale-time {
		display: inline-block;
		min-width: 5ch;
	}

	h1 {
		font-family: var(--serif);
		font-size: 2.875rem;
		font-weight: 700;
		line-height: 1.15;
		letter-spacing: -0.015em;
	}

	.lede {
		margin-top: 0.875rem;
		font-family: var(--serif);
		font-size: 1.3125rem;
		line-height: 1.5;
		color: var(--muted);
	}

	.intro-links {
		display: flex;
		gap: 1.25rem;
		margin-top: 1.25rem;
	}

	.intro-links a {
		font-family: var(--mono);
		font-size: 0.8125rem;
		text-decoration: underline;
		text-decoration-color: var(--faint);
		text-underline-offset: 3px;
	}

	.intro-links a:hover {
		text-decoration-color: currentColor;
	}

	/* Section headings */

	h2 {
		font-size: 1.375rem;
		font-weight: 700;
		line-height: 1.3;
		letter-spacing: -0.01em;
	}

	h3 {
		font-family: var(--serif);
		font-size: 1.1875rem;
		font-weight: 600;
		line-height: 1.4;
	}

	.meta {
		font-family: var(--mono);
		font-size: 0.75rem;
		color: var(--faint);
		white-space: nowrap;
	}

	/* Rows: the shared list pattern */

	.rows {
		margin-top: 1.25rem;
	}

	.rows > :global(*) {
		border-bottom: 1px solid var(--line);
	}

	.row-head {
		display: flex;
		align-items: baseline;
		justify-content: space-between;
		gap: 1.5rem;
	}

	/* Work */

	.job {
		padding: 1rem 0 1.125rem;
	}

	.job-role {
		font-size: 0.875rem;
		color: var(--faint);
	}

	.job-summary {
		max-width: 34rem;
		margin-top: 0.375rem;
		font-size: 0.9375rem;
		line-height: 1.55;
		color: var(--muted);
	}

	.job-stack {
		display: flex;
		flex-wrap: wrap;
		column-gap: 0.5em;
		margin-top: 0.5rem;
		font-family: var(--mono);
		font-size: 0.75rem;
		color: var(--faint);
	}

	/* Each separator sticks to the item before it, so a wrapped line never starts with one. */
	.job-stack li:not(:last-child)::after {
		content: ' ·';
	}



	/* Skills and contact */

	.pair {
		padding: 0.75rem 0;
	}

	dt,
	.contact-label {
		flex-shrink: 0;
		font-family: var(--serif);
		font-size: 1.125rem;
	}

	dd {
		font-size: 0.875rem;
		color: var(--muted);
		text-align: right;
	}

	a.pair:hover .meta {
		color: var(--text);
	}

	/* Footer */

	.footer {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1.5rem;
		margin-top: 6rem;
		padding: 1.5rem 2rem 2rem;
		border-top: 1px solid var(--line);
		font-family: var(--mono);
		font-size: 0.75rem;
		color: var(--faint);
	}

	.footer nav a {
		font-size: 0.75rem;
	}

	.footer > a:hover {
		color: var(--text);
	}

	@media (prefers-reduced-motion: reduce) {
		:global(html) {
			scroll-behavior: auto;
		}
	}

	@media (max-width: 359px) {
		.topbar nav {
			display: none;
		}
	}

	@media (max-width: 600px) {
		.topbar {
			gap: 1rem;
			padding: 1.25rem 1.5rem;
		}

		nav {
			gap: 0.875rem;
		}

		.intro {
			margin-top: 2.5rem;
		}

		h1 {
			font-size: 2.25rem;
		}

		.lede {
			font-size: 1.1875rem;
		}

		.pair {
			flex-direction: column;
			gap: 0.125rem;
		}

		dd {
			text-align: left;
		}

		.footer {
			flex-direction: column;
			align-items: flex-start;
			padding-inline: 1.5rem;
		}

		.footer nav {
			flex-wrap: wrap;
		}
	}
</style>
