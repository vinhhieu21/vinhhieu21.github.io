<script>
	import { onMount } from 'svelte';

	const logs = [
		{
			status: '[ ACTIVE ]',
			index: '01/03',
			title: 'LIVE_GAME_BACKEND',
			copy:
				'Implementing backend services for POP! Slots core game features, including tournaments, dynamic bets, sale configuration, version configuration, and sweepstakes.',
			tags: ['#JAVA', '#SPRING', '#LIVE_GAMES']
		},
		{
			status: '[ ARCHIVED ]',
			index: '02/03',
			title: 'BANKING_SYSTEMS',
			copy:
				'Built enterprise microservices for CIMB Bank Thai digital applications, shipping investment features with Java 17, Spring Boot, MySQL, Redis, and AWS.',
			images: [
				{
					src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuA1Aul3YGyI69X-xj_tkuwZ9fEI0cFxO3bJZTmWzFsTS8FjaaQ43Nz9ndtWqPRamJrJZIncpJdIgb8L6fQVbTLNUtxpyz-mgsmONuH-FeVjPRkCZCwIvwBmGrVPr1HIC9s9dOvsS1E8nUGP68A7DL6w0zWBdQ_I_SIScmS270AI_w7CurjXvi-bnhHfYvDugFTtesDbfTsYSQt6tFk0jNMzW0zpRpV2XFItmIIimJT2ulFx4F_SBnSI2CtIR-xAYlecOVNO5E1Gm4g',
					alt: 'Mist on a forest path'
				},
				{
					src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuAaDIiibtaPV9R9dooIFFgYa0uzEykJFQ0IUy-aCj4ULwL1Nx-OGEusvV8eHPpdjTJjWVEqQkRUF0RzwtTgb4_A8gtGaVSqFGjv-bhERpdHNn-2Z-uN76dB48Z99K_NSE2mkPSLntIUBOlxMsmCDvzD7Q9143pxWh3zGXPrrOanmOguBhQqEFJ4wpv4Bad7d4AI597r8um92O2gAIJOX4_tp4F0Lk3PUm2Yx9qc79L6uBKvA8r3ypjKUmwjJcg_bWzu2AA3ST34QmQ',
					alt: 'Dark mountain silhouette'
				}
			]
		},
		{
			status: '[ ACTIVE ]',
			index: '03/03',
			title: 'DELIVERY_TRACK_RECORD',
			copy:
				'Career path across playStudios, CIMB Bank Thai, IBM APAC, and Viettel, focused on backend systems, microservices, cloud-native delivery, and distributed architecture.',
			tags: ['#MICROSERVICES', '#AWS', '#KUBERNETES']
		}
	];

	const experience = [
		{
			ref: '#001_PLAYSTUDIOS',
			code: '001_JAVA_BACKEND_ENGINEER',
			years: 'TIMESTAMP: 11/2025 — PRESENT',
			company: 'playSTUDIOS',
			role: 'Java Backend Engineer · Hanoi, Vietnam',
			featured: true,
			items: [
				'Implement backend services for POP! Slots core game features, including tournaments, dynamic bets, sale configuration, version configuration, and sweepstakes.',
				'Collaborate with product, client, and DevOps teams to deliver backend features smoothly and reliably.',
				'Contribute to code reviews, design reviews, and scalable service architecture for live game systems.'
			]
		},
		{
			ref: '#002_CIMB',
			code: '002_SENIOR_BACKEND_ENGINEER',
			years: 'TIMESTAMP: 01/2023 — 10/2025',
			company: 'CIMB Bank Thai',
			role: 'Senior Backend Engineer · Remote, Vietnam',
			items: [
				'Built enterprise microservice applications for CIMB Bank Thai digital products using Java 17, Spring Boot, MySQL, Redis, and AWS.',
				'Designed scalable APIs and background workers with REST, gRPC, Apache Kafka, and RabbitMQ, serving thousands of daily license requests with no production issues.',
				'Led products end-to-end across requirements, partner coordination, testing, observability, and delivery with Jenkins, JMeter, CloudWatch, Datadog, ArgoCD, Grafana, and Zipkin.'
			]
		},
		{
			ref: '#003_IBM',
			code: '003_SOFTWARE_DEVELOPMENT_ENGINEER',
			years: 'TIMESTAMP: 05/2021 — 01/2023',
			company: 'IBM APAC',
			role: 'Software Development Engineer · Remote, Vietnam',
			items: [
				'Implemented enterprise fintech applications for IBM EngageAR using Java 8, Spring, Gradle, IBM DB2, IBM Cloudant, and TravisCI.',
				'Developed and rolled out the HECP automation letters feature on IBM Cloud and Kubernetes.',
				'Applied event-driven architecture, Saga pattern, and test-driven development within a global Agile team across NA, EMEA, and APAC.'
			]
		},
		{
			ref: '#004_VIETTEL',
			code: '004_SOFTWARE_ENGINEER',
			years: 'TIMESTAMP: 06/2020 — 05/2021',
			company: 'Viettel',
			role: 'Software Engineer · Hanoi, Vietnam',
			items: [
				'Implemented RESTful APIs for Viettel Post using Java 8, Spring Boot, Kafka, PostgreSQL, MongoDB, and Maven.',
				'Built employee information search features with Java 7, Spring Framework, Oracle DB, and ZK Framework.',
				'Worked with Docker, Kubernetes, AWS EC2, Kafka consumers, scalable system design, and unit testing in a professional Agile environment.'
			]
		}
	];

	const diagnostics = [
		{ label: 'CAREER_SPAN', value: '5+Y', width: '92%' },
		{ label: 'COMPANIES', value: '04', width: '80%' },
		{ label: 'CERTIFICATIONS', value: '02', width: '58%' },
		{ label: 'TOEIC_SCORE', value: '870', width: '87%' }
	];

	const compilers = ['JAVA', 'SPRING', 'GOLANG', 'PYTHON', 'AWS', 'K8S', 'DOCKER', 'GRPC'];

	const gallery = [
		{
			ref: 'REF_ID: PX_772.01',
			kind: 'wide',
			src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuD8lC1kXU0Pi1fokdi9OFraHbQ6tZbafaX7D5MJfmYM3hMPlxMPAkWqlLGmW11GXOy2suncbQ3UdAHXWtAhsPWuV7RVffRaFwrzSjwILp8XhdQ8mLAf_lUJi7UhRs87IQUjOX6pRg_slyIy1qM2_ZslJu9Cb-jicmCx82i5K4mTbSPqAKBrhMQoc7ji303qGhycbtUVrbMi3L_-DHXNXFuoePECKTul9i-3cdYq--ULKc51t4gao3gSmLkh3oGrHREjSX8FJsa23oo',
			alt: 'High contrast black and white street corner with long shadows',
			meta: [
				['LENS_OPTIC', 'SUMMICRON 35MM F2'],
				['EXPOSURE', '1/500 @ F/8.0'],
				['SUBSTRATE', 'KODAK TRI-X 400'],
				['GEOSPATIAL', 'BERLIN_MITE // 52.5200° N']
			]
		},
		{
			ref: 'REF_ID: PX_772.02',
			kind: 'portrait',
			src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBONdlyvfZzQPwVB_Yvzm1rgCSsidOOXZl_k99_0t_bd0itR6pJ26tc2lBpqoiih22OyliS1uDBdyhk0soCNvMMAiXZChr8K83NtfvAxf-5681-sESpvmBq1rMPahBtLu188bLgTCozruk4MLlh3tvbjyMaQwJ1gNnWvSSAXYzqQMNYIcwEtip9QXKKT22IN3vIsbNO48ZKrlWSwDnxrzK3Luliw1Towpkl9GTNmsE3D7fqrrjuXs8JkLvJj3xMg94O2RfNO7igIx0',
			alt: 'Monochrome geometric skyscraper architectural detail',
			meta: [
				['SUBSTRATE', 'ILFORD HP5 PLUS'],
				['COORDINATES', 'TOKYO_SHIBUYA']
			]
		},
		{
			kind: 'square',
			src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBv6cWDTRJnobO6ploMdMhDdD51-ToZ27RPiojXVY57WEgC_nGxEP0HprSceQ1bM4FyhzywKasOCoZ9d8js8ne5y2WNaXz2Wrzo-2ACpPEC0USffyfsBhLe2YM5dYOu6vlIrdOaTf8Z8pmlfMR-oXH0A06Rt_5-2Uf_52NA1wz4woQleFJyOGlX1EmmHl7IcRcf6KI-of9IqdeDJTkSg5adw_h8Uz6qUoYrNRqb_MheINoMj4FrI_zHDDKzYFYHN32PKfx-Iscd4CU',
			alt: 'Blurred motion of a person crossing a high contrast street',
			note:
				'Subject captured in transit. Motion blur intentional to emphasize the kinetic decay of the urban environment. Film pushed +2 stops in chemical processing.'
		},
		{
			kind: 'panorama',
			src: 'https://lh3.googleusercontent.com/aida-public/AB6AXuBzwaGwNEQAX2U0Q1DbcIXWEYZU1uwSWYq94KiazDFRalhfChjn2zAMeB09VbB369hHheCvTl9cipu9wPlpL5imEVsPpnraZTl1b8UUX8HlogcfBVInzUIN1Agio2r0cx-4gn1kh1w4s_hIxwC12KfVHYeZvKclAMbkiqeF6-qqAaCxEvDZLNzYIqgduJbBg7cmQNOAgfZu3ZMe1bbUkz4VOdHn5hMxHeni6qmv-wq2ChVdBNck0yccHTrcINi1GxJuvflscoTGRvg',
			alt: 'Wide shot of an empty brutalist concrete plaza in black and white',
			badges: ['LOCKED', 'VERIFIED_DATA'],
			stats: [
				['SHUTTER', '1/1000s'],
				['APERTURE', 'f/11'],
				['FILM_ISO', '400']
			]
		}
	];

	const externalNodes = [
		{ label: '/social/github', href: 'https://github.com/vinhhieu21' },
		{ label: '/mail/buivinhhieu217', href: 'mailto:buivinhhieu217@gmail.com' },
		{ label: '/call/+84_978713957', href: 'tel:+84978713957' }
	];

	let theme = $state('dark');

	/** @param {string} nextTheme */
	function applyTheme(nextTheme) {
		theme = nextTheme;

		if (typeof document !== 'undefined') {
			document.documentElement.setAttribute('data-theme', nextTheme);
			document.body.setAttribute('data-theme', nextTheme);
		}

		if (typeof localStorage !== 'undefined') {
			localStorage.setItem('theme', nextTheme);
		}
	}

	function toggleTheme() {
		applyTheme(theme === 'dark' ? 'light' : 'dark');
	}

	onMount(() => {
		const currentTheme =
			document.documentElement.getAttribute('data-theme') ||
			document.body.getAttribute('data-theme') ||
			'dark';
		document.body.setAttribute('data-theme', currentTheme);
		theme = currentTheme;
	});
</script>

<svelte:head>
	<title>Hieu Bui Vinh | Backend Engineer</title>
	<meta
		name="description"
		content="Personal website of Hieu Bui Vinh, a backend engineer focused on Java, Spring, microservices, distributed systems, and cloud-native delivery."
	/>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		href="https://fonts.googleapis.com/css2?family=Newsreader:ital,wght@0,300..800;1,300..800&family=Space+Grotesk:wght@300..700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>

<div class="page-shell">
	<header class="topbar reveal">
		<a class="brand" href="#top" aria-label="Go to top">[HIEU_BUI_VINH]</a>
		<nav class="nav" aria-label="Primary">
			<a href="#top">HOME</a>
			<a href="#experience">EXPERIENCE</a>
			<a href="#gallery">GALLERY</a>
			<a href="#contact">CONTACT</a>
		</nav>
		<div class="toolbar">
			<span class="system-status">SYSTEM_STATUS: ONLINE</span>
			<button class="theme-toggle" type="button" aria-label="Toggle color theme" onclick={toggleTheme}>
				{theme === 'dark' ? 'SOLAR' : 'RITUAL'}
			</button>
		</div>
	</header>

	<main id="top">
		<section class="hero section reveal delay-1">
			<div class="hero-copy">
				<div class="terminal-line">
					<span class="status-dot"></span>
					HANOI, VIETNAM // BACKEND_ENGINEER
				</div>
				<h1>BUILDING RELIABLE BACKEND SYSTEMS FOR REAL PRODUCTS.</h1>
				<div class="hero-actions">
					<a class="primary-cta" href="#experience">VIEW_EXPERIENCE</a>
					<p>
						I am Hieu Bui Vinh, a backend engineer working across Java, Spring, Go, cloud-native
						platforms, microservices, and distributed systems. I build production services that stay
						scalable, maintainable, and observable.
					</p>
				</div>
			</div>

			<aside class="hero-visual">
				<div class="hero-asset">
					<div class="visual-ref">REF_ID: #8821-X</div>
					<img
						src="https://lh3.googleusercontent.com/aida-public/AB6AXuDPkkyuJRviz1ZWcNJFjuSICsn2UCHJfRvFPWmVxVSACEEH6xPj8wEntP05Taf3xtOdwYsfBEZFmqPjIgF29CkdBcmlcYN4xAlGAp6nI98N_5cRkEf8_3PPHzRN6S6tdB1qyJGCUEIhXpstwSf1vViWHi8c74wBUu1gtWA5j6uDhAATs4VDSSylFjWG1ZN_ndB2xk-sSyYhgHkag_nTjNkG6eSHOQli0OoQ9umQXdwq0euJneolmUxkYACh139alww09_C24OzE4Q8"
						alt="Cyberpunk city street at night"
					/>
					<div class="visual-meta">
						<div><span>SHUTTER</span><strong>1/250s</strong></div>
						<div><span>APERTURE</span><strong>f/1.4</strong></div>
						<div><span>ISO</span><strong>400</strong></div>
						<div><span>LENS</span><strong>35MM_PRIME</strong></div>
					</div>
				</div>
				<p class="visual-caption">CURRENT_STACK: JAVA // SPRING // AWS // MICROSERVICES</p>
			</aside>
		</section>

		<section class="logs section reveal delay-2">
			<div class="section-head">
				<h2>SELECTED_LOGS</h2>
				<span>FILTER: ALL_ASSETS</span>
			</div>

			<div class="log-grid">
				{#each logs as log}
					<article class="log-card">
						<div class="log-head">
							<span class:archived={log.status === '[ ARCHIVED ]'}>{log.status}</span>
							<span>{log.index}</span>
						</div>

						{#if log.images}
							<div class="log-images">
								{#each log.images as image}
									<img src={image.src} alt={image.alt} />
								{/each}
							</div>
						{/if}

						<h3>{log.title}</h3>
						<p>{log.copy}</p>

						{#if log.tags}
							<div class="tag-row">
								{#each log.tags as tag}
									<span>{tag}</span>
								{/each}
							</div>
						{/if}
					</article>
				{/each}
			</div>
		</section>

		<section class="experience section reveal delay-2" id="experience">
			<div class="section-header-block">
				<span class="kicker">CAREER_TIMELINE // 2020_TO_PRESENT</span>
				<h2>EXEC_PROFESSIONAL_HISTORY</h2>
				<p>
					Professional experience across gaming, banking, fintech, and logistics platforms. Focus on
					backend development, microservices, distributed systems, performance, observability, and
					reliable delivery.
				</p>
			</div>

			<div class="experience-grid">
				<div class="experience-list">
					{#each experience as item}
						<article class:featured={item.featured} class="experience-card">
							<div class="card-ref">{item.ref}</div>
							<div class="card-head">
								<span>{item.code}</span>
								<span>{item.years}</span>
							</div>
							<div class="company-block">
								<h3>{item.company}</h3>
								<p>{item.role}</p>
							</div>
							<div class="transmission-label">Transmission Log</div>
							<ul>
								{#each item.items as detail}
									<li>{detail}</li>
								{/each}
							</ul>
						</article>
					{/each}
				</div>

				<aside class="diagnostics">
					<div class="diagnostics-panel">
						<div class="panel-head">
							<h3>SYSTEM_DIAGNOSTICS</h3>
							<span>ACTIVE</span>
						</div>
						<div class="meter-list">
								{#each diagnostics as stat}
									<div class="meter">
										<div class="meter-label">
											<span>{stat.label}</span>
											<span>{stat.value}</span>
										</div>
										<div class="meter-track">
											<div class="meter-fill" style={`width: ${stat.width}`}></div>
										</div>
									</div>
								{/each}
						</div>

						<div class="compiler-cluster">
								<div class="cluster-label">Core_Stack</div>
							<div class="chip-row">
								{#each compilers as compiler}
									<span>{compiler}</span>
								{/each}
							</div>
						</div>
					</div>
				</aside>
			</div>
		</section>

		<section class="gallery section reveal delay-3" id="gallery">
			<div class="section-header-block gallery-intro">
				<span class="kicker">PROFILE_SIGNAL // CORE_CAPABILITIES</span>
				<h2>ENGINEERING <em>SIGNALS</em></h2>
				<div class="gallery-overview">
					<p>
						Core strengths pulled from recent work: backend architecture, API design, event-driven
						systems, cloud operations, testing, and cross-team execution.
					</p>
					<div class="collection-count">
						<span>TOEIC Score</span>
						<strong>870</strong>
					</div>
				</div>
			</div>

			<div class="gallery-grid">
				<article class="gallery-card gallery-wide">
					<div class="media-frame">
						<img src={gallery[0].src} alt={gallery[0].alt} />
						<span class="media-ref">{gallery[0].ref}</span>
					</div>
					<div class="meta-grid four">
						{#each gallery[0].meta as item}
							<div>
								<span>{item[0]}</span>
								<strong>{item[1]}</strong>
							</div>
						{/each}
					</div>
				</article>

				<article class="gallery-card gallery-portrait">
					<div class="media-frame portrait">
						<img src={gallery[1].src} alt={gallery[1].alt} />
						<span class="media-ref right">{gallery[1].ref}</span>
					</div>
					<div class="meta-stack">
						{#each gallery[1].meta as item}
							<div>
								<span>{item[0]}</span>
								<strong>{item[1]}</strong>
							</div>
						{/each}
					</div>
				</article>

				<article class="gallery-card gallery-square">
					<div class="media-frame square">
						<img src={gallery[2].src} alt={gallery[2].alt} />
					</div>
					<div class="annotation">
						<span>ANNOTATION</span>
						<p>{gallery[2].note}</p>
					</div>
				</article>

				<article class="gallery-card gallery-panorama">
					<div class="media-frame panorama">
						<img src={gallery[3].src} alt={gallery[3].alt} />
						<div class="badge-row">
							{#each gallery[3].badges as badge}
								<span>{badge}</span>
							{/each}
						</div>
					</div>
					<div class="meta-grid three">
						{#each gallery[3].stats as item}
							<div>
								<span>{item[0]}</span>
								<strong>{item[1]}</strong>
							</div>
						{/each}
					</div>
				</article>
			</div>
		</section>

		<section class="contact section reveal delay-4" id="contact">
			<div class="section-header-block">
				<span class="kicker">SECURE_UPLINK_ESTABLISHED // CONTACT_NODE</span>
				<h2>LET'S CONNECT</h2>
			</div>

			<div class="contact-grid">
				<div class="contact-panel">
					<div class="contact-ref">COMM_INTERFACE_v4.2</div>
					<form class="terminal-form">
						<label>
							<span>&gt; ENTER_IDENTITY_STRING</span>
							<input type="text" placeholder="YOUR_NAME" />
						</label>
						<label>
							<span>&gt; RETURN_PATH</span>
							<input type="email" placeholder="YOUR_EMAIL@DOMAIN.COM" />
						</label>
						<label>
							<span>&gt; TRANSMISSION_BODY</span>
							<textarea rows="6" placeholder="PROJECT_SCOPE_OR_MESSAGE..."></textarea>
						</label>
						<button type="submit">EXECUTE_SEND</button>
					</form>
				</div>

				<aside class="contact-sidebar">
					<div class="side-panel">
						<div class="panel-head compact">
							<h3>COMM_STATUS: ACTIVE</h3>
						</div>
						<div class="status-list">
							<div><span>EMAIL</span><strong>buivinhhieu217@gmail.com</strong></div>
							<div><span>PHONE</span><strong>(+84) 978713957</strong></div>
							<div><span>LOCATION</span><strong>HANOI, VIETNAM</strong></div>
							<div><span>ENGLISH</span><strong>PROFESSIONAL</strong></div>
						</div>
					</div>

					<div class="side-panel">
						<h3 class="side-title">EXTERNAL_NODES</h3>
						<div class="external-list">
							{#each externalNodes as node}
								<a href={node.href}>{node.label}</a>
							{/each}
						</div>
					</div>

					<div class="side-panel visual-node">
						<div class="dot-field"></div>
						<div class="fingerprint">
							<div class="fingerprint-mark">◎</div>
							<p>MTA_CS_GRADUATE</p>
						</div>
					</div>
				</aside>
			</div>
		</section>
	</main>

	<footer class="footer">
		<div class="footer-left">
			<span>HIEU BUI VINH</span>
			<span>MILITARY TECHNICAL ACADEMY · COMPUTER SCIENCE</span>
		</div>
		<div class="footer-right">
			<a href="https://github.com/vinhhieu21" target="_blank" rel="noreferrer">GITHUB</a>
			<a href="mailto:buivinhhieu217@gmail.com">EMAIL</a>
			<a href="tel:+84978713957">PHONE</a>
		</div>
	</footer>
</div>

<style>
	:global(html) {
		scroll-behavior: smooth;
	}

	:global(*) {
		box-sizing: border-box;
	}

	:global(body) {
		--bg: #131313;
		--surface: #0e0e0e;
		--surface-low: #1c1b1b;
		--surface-mid: #201f1f;
		--surface-high: #2a2a2a;
		--surface-line: rgba(159, 142, 120, 0.18);
		--text: #e5e2e1;
		--text-muted: #d6c4ac;
		--text-faint: #9f8e78;
		--gold: #ffd698;
		--gold-strong: #ffb100;
		--green: #4ce337;
		--shadow: 0 24px 70px rgba(0, 0, 0, 0.45);
		margin: 0;
		min-height: 100vh;
		background:
			linear-gradient(to right, rgba(81, 69, 51, 0.1) 1px, transparent 1px),
			linear-gradient(to bottom, rgba(81, 69, 51, 0.08) 1px, transparent 1px),
			radial-gradient(circle at top center, rgba(255, 177, 0, 0.08), transparent 28%),
			#131313;
		background-size: 40px 40px, 40px 40px, auto, auto;
		color: var(--text);
		font-family: 'Space Grotesk', monospace;
		transition: background-color 220ms ease, color 220ms ease;
	}

	:global(body[data-theme='light']) {
		color-scheme: light;
		--bg: #f7f3ed;
		--surface: #ffffff;
		--surface-low: #f3ede5;
		--surface-mid: #ebe3d8;
		--surface-high: #e1d7ca;
		--surface-line: rgba(115, 90, 58, 0.18);
		--text: #1d1a16;
		--text-muted: #514433;
		--text-faint: #7f6a50;
		--gold: #7f5600;
		--gold-strong: #a26f08;
		--green: #0f7a0f;
		--shadow: 0 24px 60px rgba(96, 69, 38, 0.14);
		background:
			linear-gradient(to right, rgba(115, 90, 58, 0.08) 1px, transparent 1px),
			linear-gradient(to bottom, rgba(115, 90, 58, 0.07) 1px, transparent 1px),
			radial-gradient(circle at top center, rgba(127, 86, 0, 0.07), transparent 28%),
			#f7f3ed;
		background-size: 40px 40px, 40px 40px, auto, auto;
	}

	:global(a) {
		color: inherit;
		text-decoration: none;
	}

	:global(img) {
		display: block;
		max-width: 100%;
	}

	.page-shell {
		width: min(1280px, calc(100% - 32px));
		margin: 0 auto;
		padding: 18px 0 36px;
	}

	.topbar {
		position: sticky;
		top: 0;
		z-index: 30;
		display: grid;
		grid-template-columns: auto 1fr auto;
		gap: 24px;
		align-items: center;
		padding: 14px 0;
		background: color-mix(in srgb, var(--bg) 88%, transparent);
		backdrop-filter: blur(14px);
		border-bottom: 1px solid rgba(255, 255, 255, 0.05);
	}

	.brand,
	.nav a,
	.system-status,
	.theme-toggle,
	.kicker,
	.terminal-line,
	.section-head span,
	.log-head,
	.tag-row span,
	.card-head,
	.transmission-label,
	.panel-head,
	.cluster-label,
	.meta-grid span,
	.meta-stack span,
	.annotation span,
	.contact-ref,
	.terminal-form label span,
	.footer,
	.external-list a,
	.status-list span,
	.status-list strong,
	.collection-count span {
		font-size: 0.72rem;
		letter-spacing: 0.16em;
		text-transform: uppercase;
	}

	.brand,
	.theme-toggle,
	.primary-cta,
	.visual-caption,
	.media-ref,
	.badge-row span {
		font-family: 'Space Grotesk', monospace;
	}

	.brand {
		font-family: 'Newsreader', serif;
		font-style: italic;
		font-size: 1.7rem;
		color: var(--gold-strong);
	}

	.nav {
		display: flex;
		justify-content: center;
		gap: clamp(16px, 2vw, 32px);
	}

	.nav a,
	.system-status {
		color: var(--text-faint);
	}

	.nav a:hover,
	.nav a:focus-visible,
	.footer-right a:hover,
	.footer-right a:focus-visible,
	.external-list a:hover,
	.external-list a:focus-visible {
		color: var(--gold);
	}

	.toolbar {
		display: flex;
		align-items: center;
		gap: 14px;
	}

	.theme-toggle {
		border: 1px solid var(--surface-line);
		background: transparent;
		color: var(--gold-strong);
		padding: 8px 10px;
		cursor: pointer;
	}

	.section {
		padding: 34px 0 18px;
	}

	.hero {
		display: grid;
		grid-template-columns: minmax(0, 1.15fr) minmax(320px, 0.9fr);
		gap: 32px;
		align-items: start;
	}

	.terminal-line,
	.kicker {
		display: flex;
		align-items: center;
		gap: 10px;
		color: var(--green);
		margin-bottom: 16px;
	}

	.status-dot {
		width: 8px;
		height: 8px;
		background: currentColor;
		box-shadow: 0 0 12px currentColor;
	}

	h1,
	h2,
	h3 {
		margin: 0;
		font-family: 'Newsreader', serif;
	}

	h1 {
		max-width: 8ch;
		font-size: clamp(4rem, 9vw, 7.5rem);
		line-height: 0.9;
		color: var(--gold);
	}

	h2 {
		font-size: clamp(2.6rem, 5vw, 4.6rem);
		line-height: 0.95;
		font-style: italic;
	}

	.hero-actions {
		display: grid;
		grid-template-columns: auto minmax(0, 22rem);
		gap: 20px;
		align-items: end;
		margin-top: 34px;
	}

	.hero-actions p,
	.section-header-block p,
	.log-card p,
	.annotation p,
	.fingerprint p {
		margin: 0;
		color: var(--text-muted);
		line-height: 1.7;
	}

	.primary-cta {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		padding: 15px 22px;
		background: var(--gold-strong);
		color: #2f1d00;
		font-weight: 700;
	}

	.hero-visual {
		position: relative;
	}

	.hero-asset,
	.log-card,
	.experience-card,
	.diagnostics-panel,
	.gallery-card,
	.contact-panel,
	.side-panel {
		background: var(--surface);
		box-shadow: var(--shadow);
	}

	.hero-asset {
		position: relative;
		border: 1px solid var(--surface-line);
		overflow: hidden;
	}

	.hero-asset img,
	.media-frame img,
	.log-images img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		filter: grayscale(1) contrast(1.15);
	}

	.hero-asset img {
		aspect-ratio: 4 / 5;
		opacity: 0.84;
	}

	.visual-ref,
	.media-ref {
		position: absolute;
		top: 16px;
		left: 16px;
		padding: 6px 10px;
		border: 1px solid var(--surface-line);
		background: color-mix(in srgb, var(--bg) 84%, transparent);
		color: var(--text-muted);
	}

	.media-ref.right {
		right: 16px;
		left: auto;
	}

	.visual-meta,
	.meta-grid,
	.meta-stack {
		display: grid;
		gap: 0;
		border-top: 1px solid var(--surface-line);
	}

	.visual-meta {
		grid-template-columns: repeat(4, minmax(0, 1fr));
		background: color-mix(in srgb, var(--bg) 88%, transparent);
		backdrop-filter: blur(8px);
	}

	.visual-meta div,
	.meta-grid div,
	.meta-stack div {
		padding: 14px 16px;
	}

	.visual-meta div + div,
	.meta-grid div + div,
	.meta-stack div + div {
		border-left: 1px solid var(--surface-line);
	}

	.visual-meta span,
	.meta-grid span,
	.meta-stack span,
	.collection-count span,
	.status-list span {
		display: block;
		color: var(--text-faint);
		margin-bottom: 6px;
	}

	.visual-meta strong,
	.meta-grid strong,
	.meta-stack strong,
	.collection-count strong,
	.status-list strong {
		font-size: 0.86rem;
		color: var(--text);
	}

	.visual-caption {
		margin: 10px 0 0;
		text-align: right;
		color: var(--text-faint);
	}

	.section-head {
		display: flex;
		justify-content: space-between;
		align-items: flex-end;
		gap: 20px;
		padding-bottom: 14px;
		border-bottom: 1px solid var(--surface-line);
		margin-bottom: 18px;
	}

	.log-grid {
		display: grid;
		grid-template-columns: repeat(3, minmax(0, 1fr));
	}

	.log-card {
		min-height: 100%;
		padding: 28px;
		border-right: 1px solid var(--surface-line);
		border-bottom: 1px solid var(--surface-line);
	}

	.log-card:first-child {
		border-left: 1px solid var(--surface-line);
	}

	.log-head {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 34px;
		color: var(--text-faint);
	}

	.log-head .archived {
		color: var(--gold-strong);
	}

	.log-head span:first-child:not(.archived) {
		color: var(--green);
	}

	.log-card h3,
	.company-block p,
	.panel-head h3,
	.side-title {
		font-family: 'Space Grotesk', monospace;
		font-size: 1.05rem;
		font-weight: 700;
		letter-spacing: 0.08em;
		text-transform: uppercase;
	}

	.log-card h3 {
		margin-bottom: 16px;
	}

	.log-images {
		display: grid;
		grid-template-columns: repeat(2, minmax(0, 1fr));
		gap: 8px;
		margin-bottom: 18px;
	}

	.log-images img {
		aspect-ratio: 1;
		opacity: 0.66;
	}

	.tag-row,
	.chip-row,
	.badge-row {
		display: flex;
		flex-wrap: wrap;
		gap: 12px;
	}

	.tag-row {
		margin-top: 20px;
		color: var(--text-faint);
	}

	.section-header-block {
		max-width: 66rem;
		padding-left: 24px;
		border-left: 2px solid var(--gold-strong);
		margin-bottom: 28px;
	}

	.section-header-block p {
		max-width: 44rem;
		margin-top: 14px;
	}

	.experience-grid,
	.contact-grid {
		display: grid;
		grid-template-columns: minmax(0, 1.5fr) minmax(280px, 0.8fr);
		gap: 30px;
	}

	.experience-list {
		display: grid;
		gap: 18px;
	}

	.experience-card {
		position: relative;
		padding: 28px;
		border-left: 4px solid var(--text-faint);
		background: var(--surface-low);
	}

	.experience-card.featured {
		border-left-color: var(--gold-strong);
		background: var(--surface);
	}

	.card-ref,
	.contact-ref {
		position: absolute;
		top: 16px;
		right: 18px;
		color: var(--text-faint);
		opacity: 0.56;
	}

	.card-head {
		display: flex;
		flex-wrap: wrap;
		gap: 12px 20px;
		margin-bottom: 22px;
	}

	.card-head span:first-child {
		color: var(--gold-strong);
		font-weight: 700;
	}

	.card-head span:last-child {
		color: var(--text-faint);
	}

	.company-block {
		margin-bottom: 22px;
	}

	.company-block h3 {
		font-size: 2rem;
		font-style: italic;
		margin-bottom: 4px;
	}

	.company-block p {
		color: var(--green);
		font-size: 0.72rem;
	}

	.transmission-label {
		padding-bottom: 10px;
		border-bottom: 1px solid var(--surface-line);
		margin-bottom: 12px;
		color: var(--text-faint);
	}

	.experience-card ul {
		margin: 0;
		padding: 0;
		list-style: none;
		display: grid;
		gap: 14px;
	}

	.experience-card li {
		position: relative;
		padding-left: 18px;
		color: var(--text-muted);
		line-height: 1.6;
	}

	.experience-card li::before {
		content: '•';
		position: absolute;
		left: 0;
		color: var(--gold-strong);
	}

	.diagnostics-panel,
	.side-panel {
		padding: 24px;
		border: 1px solid var(--surface-line);
		background: var(--surface-high);
	}

	.panel-head {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 22px;
	}

	.panel-head span {
		color: var(--green);
	}

	.meter-list {
		display: grid;
		gap: 18px;
	}

	.meter-label {
		display: flex;
		justify-content: space-between;
		gap: 12px;
		margin-bottom: 8px;
		font-size: 0.72rem;
		letter-spacing: 0.1em;
		text-transform: uppercase;
	}

	.meter-track {
		height: 4px;
		background: var(--surface);
	}

	.meter-fill {
		height: 100%;
		background: var(--gold-strong);
	}

	.compiler-cluster {
		margin-top: 26px;
	}

	.cluster-label {
		color: var(--text-faint);
		margin-bottom: 12px;
	}

	.chip-row span {
		border: 1px solid var(--surface-line);
		background: var(--surface);
		padding: 7px 10px;
		font-size: 0.72rem;
	}

	.gallery-intro {
		margin-bottom: 32px;
	}

	.gallery-overview {
		display: flex;
		justify-content: space-between;
		gap: 24px;
		align-items: end;
		margin-top: 14px;
	}

	.collection-count {
		text-align: right;
		min-width: 12rem;
	}

	.collection-count strong {
		font-family: 'Newsreader', serif;
		font-size: 2.2rem;
		font-style: italic;
	}

	.gallery-grid {
		display: grid;
		grid-template-columns: repeat(12, minmax(0, 1fr));
		gap: 22px;
	}

	.gallery-card {
		border: 1px solid var(--surface-line);
		padding: 4px;
		background: var(--surface);
	}

	.gallery-wide {
		grid-column: span 8;
	}

	.gallery-portrait {
		grid-column: span 4;
	}

	.gallery-square {
		grid-column: span 5;
	}

	.gallery-panorama {
		grid-column: span 7;
	}

	.media-frame {
		position: relative;
		overflow: hidden;
	}

	.media-frame img {
		transition: transform 600ms ease, opacity 220ms ease;
	}

	.gallery-card:hover img {
		transform: scale(1.04);
	}

	.gallery-wide .media-frame img {
		aspect-ratio: 16 / 9;
	}

	.gallery-portrait .media-frame img {
		aspect-ratio: 3 / 4;
	}

	.gallery-square .media-frame img {
		aspect-ratio: 1;
	}

	.gallery-panorama .media-frame img {
		aspect-ratio: 21 / 9;
	}

	.meta-grid.four {
		grid-template-columns: repeat(4, minmax(0, 1fr));
	}

	.meta-grid.three {
		grid-template-columns: repeat(3, minmax(0, 1fr));
		text-align: center;
	}

	.meta-stack div + div {
		border-left: 0;
		border-top: 1px solid var(--surface-line);
	}

	.annotation {
		padding: 18px;
		background: var(--surface-low);
	}

	.annotation span {
		display: block;
		color: var(--text-faint);
		margin-bottom: 10px;
	}

	.badge-row {
		position: absolute;
		left: 16px;
		bottom: 16px;
	}

	.badge-row span {
		padding: 6px 10px;
		border: 1px solid var(--surface-line);
		background: color-mix(in srgb, var(--bg) 84%, transparent);
	}

	.badge-row span:first-child {
		color: var(--green);
	}

	.badge-row span:last-child {
		color: var(--gold);
	}

	.contact-panel {
		position: relative;
		padding: 32px;
		border: 1px solid var(--surface-line);
	}

	.terminal-form {
		display: grid;
		gap: 28px;
	}

	.terminal-form label {
		display: grid;
		gap: 8px;
	}

	.terminal-form label span {
		color: var(--gold);
		opacity: 0.76;
	}

	.terminal-form input,
	.terminal-form textarea {
		width: 100%;
		border: 0;
		border-bottom: 1px solid var(--surface-line);
		background: transparent;
		padding: 12px 0;
		font: inherit;
		font-size: 1.15rem;
		color: var(--text);
		resize: vertical;
	}

	.terminal-form input::placeholder,
	.terminal-form textarea::placeholder {
		color: color-mix(in srgb, var(--text-faint) 70%, transparent);
	}

	.terminal-form button {
		width: fit-content;
		border: 0;
		background: var(--gold-strong);
		color: #2f1d00;
		padding: 16px 26px;
		font: inherit;
		font-weight: 700;
		letter-spacing: 0.18em;
		text-transform: uppercase;
		cursor: pointer;
	}

	.contact-sidebar {
		display: grid;
		gap: 18px;
	}

	.panel-head.compact {
		margin-bottom: 16px;
	}

	.panel-head.compact h3 {
		color: var(--text);
	}

	.status-list,
	.external-list {
		display: grid;
		gap: 12px;
	}

	.status-list div {
		display: flex;
		justify-content: space-between;
		gap: 16px;
		padding-bottom: 10px;
		border-bottom: 1px solid var(--surface-line);
	}

	.status-list div:last-child {
		border-bottom: 0;
		padding-bottom: 0;
	}

	.status-list strong:first-of-type,
	.status-list div:first-child strong {
		color: var(--green);
	}

	.external-list a {
		display: inline-flex;
		align-items: center;
		gap: 10px;
		color: var(--text-muted);
	}

	.external-list a::after {
		content: '↗';
	}

	.visual-node {
		position: relative;
		min-height: 260px;
		overflow: hidden;
		background: var(--surface);
	}

	.dot-field {
		position: absolute;
		inset: 0;
		opacity: 0.16;
		background-image: radial-gradient(circle at 2px 2px, var(--gold) 1px, transparent 0);
		background-size: 24px 24px;
	}

	.fingerprint {
		position: relative;
		z-index: 1;
		min-height: 212px;
		display: grid;
		place-items: center;
		text-align: center;
	}

	.fingerprint-mark {
		font-size: 4rem;
		color: var(--gold-strong);
		line-height: 1;
	}

	.fingerprint p {
		margin-top: 12px;
		font-size: 0.72rem;
		letter-spacing: 0.18em;
		text-transform: uppercase;
	}

	.footer {
		display: flex;
		justify-content: space-between;
		gap: 20px;
		align-items: center;
		padding: 18px 0 8px;
		border-top: 1px solid var(--surface-line);
		margin-top: 24px;
		color: var(--text-faint);
	}

	.footer-left,
	.footer-right {
		display: flex;
		flex-wrap: wrap;
		gap: 18px;
	}

	.reveal {
		opacity: 0;
		transform: translateY(18px);
		animation: rise 650ms ease forwards;
	}

	.delay-1 {
		animation-delay: 80ms;
	}

	.delay-2 {
		animation-delay: 140ms;
	}

	.delay-3 {
		animation-delay: 220ms;
	}

	.delay-4 {
		animation-delay: 300ms;
	}

	@keyframes rise {
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (max-width: 960px) {
		.topbar,
		.hero,
		.experience-grid,
		.contact-grid,
		.footer {
			grid-template-columns: 1fr;
		}

		.topbar {
			position: relative;
		}

		.nav {
			justify-content: flex-start;
			flex-wrap: wrap;
		}

		.toolbar {
			justify-content: flex-start;
			flex-wrap: wrap;
		}

		.hero-actions {
			grid-template-columns: 1fr;
		}

		.log-grid {
			grid-template-columns: 1fr;
		}

		.log-card,
		.log-card:first-child {
			border-left: 1px solid var(--surface-line);
		}

		.gallery-grid {
			grid-template-columns: 1fr;
		}

		.gallery-wide,
		.gallery-portrait,
		.gallery-square,
		.gallery-panorama {
			grid-column: auto;
		}

		.gallery-overview {
			flex-direction: column;
			align-items: start;
		}

		.collection-count {
			text-align: left;
		}

		.footer {
			align-items: start;
		}
	}

	@media (max-width: 640px) {
		.page-shell {
			width: min(100%, calc(100% - 20px));
		}

		.topbar {
			gap: 14px;
		}

		.brand {
			font-size: 1.35rem;
		}

		h1 {
			font-size: clamp(3.3rem, 20vw, 5.2rem);
		}

		h2 {
			font-size: clamp(2.1rem, 14vw, 3rem);
		}

		.section {
			padding-top: 28px;
		}

		.visual-meta,
		.meta-grid.four,
		.meta-grid.three {
			grid-template-columns: repeat(2, minmax(0, 1fr));
		}

		.card-head {
			flex-direction: column;
			align-items: start;
		}

		.contact-panel,
		.diagnostics-panel,
		.side-panel,
		.experience-card,
		.log-card {
			padding: 20px;
		}

		.terminal-form input,
		.terminal-form textarea {
			font-size: 1rem;
		}
	}
</style>
