<script>
	import { onMount } from 'svelte';

	const email = 'buivinhhieu217@gmail.com';
	const github = 'https://github.com/vinhhieu21';
	const careerStart = 2020;
	const yearsOfExperience = new Date().getFullYear() - careerStart;

	const nav = [
		{ href: '#experience', label: 'Experience' },
		{ href: '#skills', label: 'Skills' },
		{ href: '#contact', label: 'Contact' }
	];

	const stats = [
		{ value: `${yearsOfExperience}+`, label: 'years building backend systems' },
		{ value: '4', label: 'companies, including IBM and CIMB' },
		{ value: '4', label: 'domains: gaming, banking, fintech, logistics' }
	];

	const focus = [
		{
			title: 'Distributed services',
			copy: 'Java and Spring Boot microservices with clear APIs over REST and gRPC, designed to scale and stay easy to change.',
			tech: 'Java · Spring Boot · gRPC'
		},
		{
			title: 'Event-driven systems',
			copy: 'Asynchronous workflows with Kafka and RabbitMQ, using patterns like Saga to keep data consistent across services.',
			tech: 'Kafka · RabbitMQ · Saga'
		},
		{
			title: 'Cloud and operations',
			copy: 'Shipping to AWS and Kubernetes with CI/CD, then watching it in production with traces, metrics, and dashboards.',
			tech: 'AWS · Kubernetes · Datadog'
		}
	];

	const experience = [
		{
			company: 'playSTUDIOS',
			role: 'Java Backend Engineer',
			location: 'Hanoi',
			period: 'Nov 2025 - Present',
			current: true,
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
			period: 'Jan 2023 - Oct 2025',
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
			period: 'May 2021 - Jan 2023',
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
			period: 'Jun 2020 - May 2021',
			items: [
				'Implemented RESTful APIs and Kafka consumers for Viettel Post.',
				'Built employee information search for internal systems.'
			],
			stack: ['Java', 'Spring Boot', 'Kafka', 'PostgreSQL', 'MongoDB', 'Oracle']
		}
	];

	const skills = [
		{ group: 'Languages', items: ['Java', 'Go', 'Python', 'SQL'] },
		{ group: 'Frameworks', items: ['Spring Boot', 'Spring', 'gRPC'] },
		{ group: 'Messaging', items: ['Kafka', 'RabbitMQ'] },
		{ group: 'Data', items: ['MySQL', 'PostgreSQL', 'Redis', 'MongoDB', 'Oracle', 'DB2'] },
		{ group: 'Infrastructure', items: ['AWS', 'Kubernetes', 'Docker', 'Jenkins', 'ArgoCD'] },
		{ group: 'Observability', items: ['Datadog', 'CloudWatch', 'Grafana', 'Zipkin', 'JMeter'] }
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

<header class="topbar">
	<div class="container topbar-inner">
		<a class="brand" href="#top">
			<span class="brand-mark" aria-hidden="true">hb</span>
			<span>Hieu Bui Vinh</span>
		</a>
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
</header>

<main id="top" class="container">
	<section class="hero">
		<div class="hero-copy">
			<p class="status"><span class="status-dot" aria-hidden="true"></span>Backend Engineer at playSTUDIOS</p>
			<h1>I build backend systems that stay reliable in production.</h1>
			<p class="lede">
				I'm Hieu, a backend engineer in Hanoi. Since {careerStart} I have shipped Java and Spring
				microservices, event-driven pipelines, and cloud-native platforms for live games, digital
				banking, fintech, and logistics.
			</p>
			<div class="actions">
				<a class="button primary" href={`mailto:${email}`}>Get in touch</a>
				<a class="button" href={github} target="_blank" rel="noreferrer">GitHub</a>
			</div>
		</div>

		<figure class="terminal" aria-label="Profile shown as an API response">
			<div class="terminal-bar" aria-hidden="true">
				<span></span><span></span><span></span>
				<p>GET /api/whoami</p>
			</div>
			<pre><code><span class="t-dim">HTTP/1.1</span> <span class="t-ok">200 OK</span>
<span class="t-dim">content-type: application/json</span>

&#123;
  <span class="t-key">"name"</span>: <span class="t-str">"Hieu Bui Vinh"</span>,
  <span class="t-key">"role"</span>: <span class="t-str">"Backend Engineer"</span>,
  <span class="t-key">"location"</span>: <span class="t-str">"Hanoi, VN"</span>,
  <span class="t-key">"experience_years"</span>: <span class="t-num">{yearsOfExperience}</span>,
  <span class="t-key">"stack"</span>: [<span class="t-str">"Java"</span>, <span class="t-str">"Spring"</span>, <span class="t-str">"Kafka"</span>,
            <span class="t-str">"AWS"</span>, <span class="t-str">"Kubernetes"</span>],
  <span class="t-key">"focus"</span>: <span class="t-str">"distributed systems"</span>
&#125;</code></pre>
		</figure>
	</section>

	<ul class="stats">
		{#each stats as stat}
			<li>
				<strong>{stat.value}</strong>
				<span>{stat.label}</span>
			</li>
		{/each}
	</ul>

	<section aria-labelledby="focus">
		<div class="section-head">
			<p class="eyebrow">What I do</p>
			<h2 id="focus">Focus areas</h2>
		</div>
		<ul class="focus">
			{#each focus as area, i}
				<li class="card">
					<span class="focus-index">0{i + 1}</span>
					<h3>{area.title}</h3>
					<p>{area.copy}</p>
					<span class="focus-tech">{area.tech}</span>
				</li>
			{/each}
		</ul>
	</section>

	<section aria-labelledby="experience">
		<div class="section-head">
			<p class="eyebrow">Career</p>
			<h2 id="experience">Experience</h2>
		</div>
		<ol class="timeline">
			{#each experience as job}
				<li class="job" class:current={job.current}>
					<div class="job-head">
						<div>
							<h3>{job.company}</h3>
							<p class="job-role">{job.role} · {job.location}</p>
						</div>
						<p class="period">{job.period}</p>
					</div>
					<ul class="job-items">
						{#each job.items as item}
							<li>{item}</li>
						{/each}
					</ul>
					<ul class="chips" aria-label="Tech stack">
						{#each job.stack as tech}
							<li>{tech}</li>
						{/each}
					</ul>
				</li>
			{/each}
		</ol>
	</section>

	<section aria-labelledby="skills">
		<div class="section-head">
			<p class="eyebrow">Toolbox</p>
			<h2 id="skills">Skills</h2>
		</div>
		<div class="skills">
			{#each skills as skill}
				<div class="card">
					<h3>{skill.group}</h3>
					<ul class="chips">
						{#each skill.items as item}
							<li>{item}</li>
						{/each}
					</ul>
				</div>
			{/each}
		</div>
		<dl class="facts">
			<div>
				<dt>Education</dt>
				<dd>Computer Science, Military Technical Academy</dd>
			</div>
			<div>
				<dt>English</dt>
				<dd>Professional working proficiency, TOEIC 870</dd>
			</div>
		</dl>
	</section>

	<section class="contact card" aria-labelledby="contact">
		<div>
			<h2 id="contact">Let's talk backend.</h2>
			<p>Questions about a role, a system design, or something I built? Email is the fastest way to reach me.</p>
		</div>
		<div class="actions">
			<a class="button primary" href={`mailto:${email}`}>{email}</a>
			<a class="button" href="tel:+84978713957">+84 978 713 957</a>
		</div>
	</section>
</main>

<footer class="container footer">
	<span>© {new Date().getFullYear()} Hieu Bui Vinh</span>
	<a href="https://github.com/vinhhieu21/vinhhieu21.github.io" target="_blank" rel="noreferrer"
		>Built with SvelteKit</a
	>
</footer>

<style>
	:global(html) {
		--bg: #fafafa;
		--surface: #ffffff;
		--text: #18181b;
		--muted: #52525b;
		--faint: #71717a;
		--line: #e4e4e7;
		--chip: #f4f4f5;
		--accent: #047857;
		--accent-soft: #ecfdf5;
		--on-accent: #ffffff;
		--mono: ui-monospace, 'SF Mono', SFMono-Regular, Menlo, Consolas, monospace;
		color-scheme: light;
		background: var(--bg);
		color: var(--text);
		scroll-behavior: smooth;
		scroll-padding-top: 5rem;
		-webkit-text-size-adjust: 100%;
	}

	:global(html[data-theme='dark']) {
		--bg: #0c0c0e;
		--surface: #141417;
		--text: #e4e4e7;
		--muted: #a1a1aa;
		--faint: #8b8b94;
		--line: #26262b;
		--chip: #1e1e22;
		--accent: #34d399;
		--accent-soft: #0b2a20;
		--on-accent: #052e1f;
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
		border-radius: 4px;
	}

	h1,
	h2,
	h3,
	p,
	ul,
	ol,
	dl,
	dd,
	figure,
	pre {
		margin: 0;
	}

	ul,
	ol {
		padding: 0;
		list-style: none;
	}

	a {
		color: inherit;
		text-decoration: none;
	}

	.container {
		width: min(64rem, 100% - 3rem);
		margin-inline: auto;
	}

	section {
		margin-top: 6rem;
	}

	.card {
		padding: 1.5rem;
		border: 1px solid var(--line);
		border-radius: 12px;
		background: var(--surface);
	}

	.chips {
		display: flex;
		flex-wrap: wrap;
		gap: 0.375rem;
	}

	.chips li {
		padding: 0.125rem 0.5rem;
		border-radius: 6px;
		background: var(--chip);
		font-family: var(--mono);
		font-size: 0.75rem;
		line-height: 1.7;
		color: var(--muted);
	}

	/* Top bar */

	.topbar {
		position: sticky;
		top: 0;
		z-index: 10;
		border-bottom: 1px solid var(--line);
		background: color-mix(in srgb, var(--bg) 82%, transparent);
		backdrop-filter: saturate(180%) blur(12px);
	}

	.topbar-inner {
		display: flex;
		align-items: center;
		gap: 2rem;
		height: 3.75rem;
	}

	.brand {
		display: inline-flex;
		align-items: center;
		gap: 0.625rem;
		font-weight: 600;
		letter-spacing: -0.01em;
	}

	.brand-mark {
		display: grid;
		place-items: center;
		width: 1.75rem;
		height: 1.75rem;
		border-radius: 6px;
		background: var(--text);
		color: var(--bg);
		font-family: var(--mono);
		font-size: 0.75rem;
		font-weight: 600;
	}

	nav {
		display: flex;
		gap: 1.75rem;
		margin-left: auto;
		font-size: 0.9375rem;
	}

	nav a {
		color: var(--muted);
		transition: color 150ms ease;
	}

	nav a:hover {
		color: var(--text);
	}

	.theme-toggle {
		display: grid;
		place-items: center;
		width: 2.25rem;
		height: 2.25rem;
		padding: 0;
		border: 1px solid var(--line);
		border-radius: 8px;
		background: var(--surface);
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

	/* Hero */

	.hero {
		display: grid;
		grid-template-columns: minmax(0, 1.1fr) minmax(0, 1fr);
		gap: 3.5rem;
		align-items: center;
		margin-top: 5.5rem;
	}

	.status {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		padding: 0.25rem 0.75rem;
		border: 1px solid var(--line);
		border-radius: 999px;
		background: var(--surface);
		font-size: 0.8125rem;
		color: var(--muted);
	}

	.status-dot {
		position: relative;
		width: 0.5rem;
		height: 0.5rem;
		border-radius: 50%;
		background: var(--accent);
	}

	.status-dot::after {
		content: '';
		position: absolute;
		inset: 0;
		border-radius: 50%;
		background: var(--accent);
		animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
	}

	@keyframes ping {
		75%,
		100% {
			transform: scale(2.4);
			opacity: 0;
		}
	}

	h1 {
		margin-top: 1.5rem;
		font-size: clamp(2.25rem, 4.6vw, 3.25rem);
		font-weight: 650;
		line-height: 1.1;
		letter-spacing: -0.035em;
		text-wrap: balance;
	}

	.lede {
		margin-top: 1.25rem;
		max-width: 34rem;
		font-size: 1.0625rem;
		color: var(--muted);
	}

	.actions {
		display: flex;
		flex-wrap: wrap;
		gap: 0.75rem;
		margin-top: 2rem;
	}

	.button {
		display: inline-flex;
		align-items: center;
		height: 2.75rem;
		padding: 0 1.125rem;
		border: 1px solid var(--line);
		border-radius: 8px;
		background: var(--surface);
		font-size: 0.9375rem;
		font-weight: 500;
		transition:
			border-color 150ms ease,
			filter 150ms ease;
	}

	.button:hover {
		border-color: var(--faint);
	}

	.button.primary {
		border-color: var(--accent);
		background: var(--accent);
		color: var(--on-accent);
	}

	.button.primary:hover {
		filter: brightness(1.1);
	}

	/* The terminal stays dark in both themes. */
	.terminal {
		overflow: hidden;
		border: 1px solid #27272a;
		border-radius: 12px;
		background: #111113;
		box-shadow: 0 24px 48px -24px rgb(0 0 0 / 0.35);
		color: #d4d4d8;
	}

	.terminal-bar {
		display: flex;
		align-items: center;
		gap: 0.375rem;
		padding: 0.75rem 1rem;
		border-bottom: 1px solid #27272a;
	}

	.terminal-bar span {
		width: 0.625rem;
		height: 0.625rem;
		border-radius: 50%;
		background: #3f3f46;
	}

	.terminal-bar p {
		margin-left: 0.75rem;
		font-family: var(--mono);
		font-size: 0.75rem;
		color: #a1a1aa;
	}

	.terminal pre {
		overflow-x: auto;
		padding: 1.25rem 1.25rem 1.5rem;
		font-family: var(--mono);
		font-size: 0.8125rem;
		line-height: 1.7;
	}

	.t-dim {
		color: #71717a;
	}

	.t-ok {
		color: #34d399;
	}

	.t-key {
		color: #93c5fd;
	}

	.t-str {
		color: #fcd34d;
	}

	.t-num {
		color: #f9a8d4;
	}

	/* Stats */

	.stats {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		margin-top: 5rem;
		border-block: 1px solid var(--line);
	}

	.stats li {
		padding: 1.5rem 1.5rem 1.5rem 0;
	}

	.stats li + li {
		padding-left: 1.5rem;
		border-left: 1px solid var(--line);
	}

	.stats strong {
		display: block;
		font-size: 2rem;
		font-weight: 650;
		line-height: 1.2;
		letter-spacing: -0.03em;
	}

	.stats span {
		font-size: 0.875rem;
		color: var(--muted);
	}

	/* Section headings */

	.section-head {
		margin-bottom: 2rem;
	}

	.eyebrow {
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--accent);
	}

	h2 {
		margin-top: 0.25rem;
		font-size: 1.75rem;
		font-weight: 650;
		line-height: 1.25;
		letter-spacing: -0.025em;
	}

	h3 {
		font-size: 1rem;
		font-weight: 600;
		line-height: 1.5;
	}

	/* Focus areas */

	.focus {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		gap: 1rem;
	}

	.focus li {
		display: flex;
		flex-direction: column;
	}

	.focus-index {
		margin-bottom: 1rem;
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--faint);
	}

	.focus p {
		margin-top: 0.5rem;
		font-size: 0.9375rem;
		color: var(--muted);
	}

	.focus-tech {
		margin-top: auto;
		padding-top: 1.25rem;
		font-family: var(--mono);
		font-size: 0.75rem;
		color: var(--accent);
	}

	/* Experience timeline */

	.timeline {
		position: relative;
		display: grid;
		gap: 3rem;
		padding-left: 2rem;
	}

	.timeline::before {
		content: '';
		position: absolute;
		top: 0.5rem;
		bottom: 0.5rem;
		left: 0.3125rem;
		width: 1px;
		background: var(--line);
	}

	.job {
		position: relative;
	}

	.job::before {
		content: '';
		position: absolute;
		top: 0.4375rem;
		left: -2rem;
		width: 0.625rem;
		height: 0.625rem;
		box-sizing: border-box;
		border: 2px solid var(--faint);
		border-radius: 50%;
		background: var(--bg);
	}

	.job.current::before {
		border-color: var(--accent);
		background: var(--accent);
		box-shadow: 0 0 0 4px var(--accent-soft);
	}

	.job-head {
		display: flex;
		justify-content: space-between;
		align-items: baseline;
		gap: 0.25rem 1.5rem;
		flex-wrap: wrap;
	}

	.job h3 {
		font-size: 1.0625rem;
	}

	.job-role {
		font-size: 0.9375rem;
		color: var(--muted);
	}

	.period {
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--faint);
		white-space: nowrap;
	}

	.job-items {
		display: grid;
		gap: 0.375rem;
		max-width: 46rem;
		margin-top: 0.875rem;
		font-size: 0.9375rem;
		color: var(--muted);
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

	.job .chips {
		margin-top: 1rem;
	}

	/* Skills */

	.skills {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
		gap: 1rem;
	}

	.skills h3 {
		margin-bottom: 0.75rem;
		font-size: 0.9375rem;
	}

	.facts {
		display: grid;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		gap: 1rem;
		margin-top: 2rem;
	}

	dt {
		font-family: var(--mono);
		font-size: 0.8125rem;
		color: var(--faint);
	}

	dd {
		margin-top: 0.125rem;
		font-size: 0.9375rem;
	}

	/* Contact */

	.contact {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 2rem;
		padding: 2.5rem;
	}

	.contact h2 {
		margin-top: 0;
	}

	.contact p {
		max-width: 28rem;
		margin-top: 0.5rem;
		color: var(--muted);
	}

	.contact .actions {
		flex-shrink: 0;
		margin-top: 0;
	}

	/* Footer */

	.footer {
		display: flex;
		justify-content: space-between;
		gap: 1rem;
		margin-top: 4rem;
		padding: 1.5rem 0 2.5rem;
		border-top: 1px solid var(--line);
		font-size: 0.8125rem;
		color: var(--faint);
	}

	.footer a:hover {
		color: var(--text);
	}

	@media (prefers-reduced-motion: reduce) {
		:global(html) {
			scroll-behavior: auto;
		}

		.status-dot::after {
			animation: none;
		}
	}

	@media (max-width: 860px) {
		.hero {
			grid-template-columns: minmax(0, 1fr);
			gap: 3rem;
			margin-top: 3.5rem;
		}

		.focus,
		.skills {
			grid-template-columns: repeat(2, minmax(0, 1fr));
		}

		.focus li:last-child {
			grid-column: 1 / -1;
		}

		.contact {
			flex-direction: column;
			align-items: flex-start;
		}
	}

	@media (max-width: 600px) {
		.container {
			width: min(64rem, 100% - 2.5rem);
		}

		nav {
			display: none;
		}

		.theme-toggle {
			margin-left: auto;
		}

		section {
			margin-top: 4.5rem;
		}

		.stats {
			grid-template-columns: minmax(0, 1fr);
			margin-top: 3.5rem;
		}

		.stats li,
		.stats li + li {
			display: flex;
			align-items: baseline;
			gap: 1rem;
			padding: 1rem 0;
			border-left: 0;
		}

		.stats li + li {
			border-top: 1px solid var(--line);
		}

		.stats strong {
			min-width: 2.75rem;
			font-size: 1.5rem;
		}

		.focus,
		.skills,
		.facts {
			grid-template-columns: minmax(0, 1fr);
		}

		.timeline {
			padding-left: 1.5rem;
		}

		.job::before {
			left: -1.5rem;
		}

		.contact {
			padding: 1.5rem;
		}

		.contact .actions,
		.contact .button {
			width: 100%;
		}

		.contact .button {
			justify-content: center;
		}

		.footer {
			flex-direction: column;
		}
	}
</style>
