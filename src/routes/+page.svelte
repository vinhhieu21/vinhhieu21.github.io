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
			diagram: true
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

	const navLinks = [
		{ href: '#top', label: 'HOME' },
		{ href: '#experience', label: 'EXPERIENCE' },
		{ href: '#signals', label: 'SIGNALS' },
		{ href: '#contact', label: 'CONTACT' }
	];

	const externalNodes = [
		{ label: '/social/github', href: 'https://github.com/vinhhieu21', external: true },
		{ label: '/mail/buivinhhieu217', href: 'mailto:buivinhhieu217@gmail.com' },
		{ label: '/call/+84_978713957', href: 'tel:+84978713957' }
	];

	let theme = $state('dark');
	let menuOpen = $state(false);

	let contactName = $state('');
	let contactEmail = $state('');
	let contactMessage = $state('');

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

	/** @param {SubmitEvent} event */
	function submitContact(event) {
		event.preventDefault();
		const subject = encodeURIComponent(`Website contact — ${contactName || 'visitor'}`);
		const body = encodeURIComponent(
			`${contactMessage}\n\n— ${contactName}${contactEmail ? ` (${contactEmail})` : ''}`
		);
		window.location.href = `mailto:buivinhhieu217@gmail.com?subject=${subject}&body=${body}`;
	}

	onMount(() => {
		const currentTheme =
			document.documentElement.getAttribute('data-theme') ||
			document.body.getAttribute('data-theme') ||
			'dark';
		document.body.setAttribute('data-theme', currentTheme);
		theme = currentTheme;

		const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
		if (reduceMotion || !('IntersectionObserver' in window)) return;

		const observer = new IntersectionObserver(
			(entries) => {
				for (const entry of entries) {
					if (entry.isIntersecting) {
						entry.target.classList.add('reveal-visible');
						observer.unobserve(entry.target);
					}
				}
			},
			{ threshold: 0.1, rootMargin: '0px 0px -40px' }
		);

		for (const node of document.querySelectorAll('[data-reveal]')) {
			node.classList.add('reveal-init');
			observer.observe(node);
		}

		return () => observer.disconnect();
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
	<header class="topbar">
		<a class="brand" href="#top" aria-label="Go to top">
			<span class="brand-icon">⌘</span>
			<span>[HIEU_BUI_VINH]</span>
		</a>
		<nav class="nav" aria-label="Primary">
			{#each navLinks as link}
				<a href={link.href}>{link.label}</a>
			{/each}
		</nav>
		<div class="toolbar">
			<span class="system-status">SYSTEM_STATUS: ONLINE</span>
			<button
				class="menu-toggle"
				type="button"
				aria-label="Toggle section menu"
				aria-expanded={menuOpen}
				aria-controls="menu-panel"
				onclick={() => (menuOpen = !menuOpen)}
			>
				{menuOpen ? 'CLOSE' : 'MENU'}
			</button>
			<button class="theme-toggle" type="button" aria-label="Toggle color theme" onclick={toggleTheme}>
				{theme === 'dark' ? 'LIGHT_MODE' : 'DARK_MODE'}
			</button>
		</div>
		{#if menuOpen}
			<nav class="menu-panel" id="menu-panel" aria-label="Section menu">
				{#each navLinks as link}
					<a href={link.href} onclick={() => (menuOpen = false)}>{link.label}</a>
				{/each}
			</nav>
		{/if}
	</header>

	<main id="top">
		<section class="hero section" data-reveal>
			<div class="hero-copy">
				<div class="terminal-line">
					<span class="status-dot"></span>
					HANOI, VIETNAM // BACKEND_ENGINEER
				</div>
				<h1>BUILDING RELIABLE BACKEND SYSTEMS FOR REAL PRODUCTS.</h1>
				<div class="mobile-profile">
					<div class="monogram" aria-hidden="true">HBV</div>
					<div>
						<strong>HIEU_BUI_VINH</strong>
						<span>Java Backend Engineer / Distributed Systems</span>
						<p>
							Building production services across gaming, banking, fintech, and logistics with Java,
							Spring, AWS, and Kubernetes.
						</p>
					</div>
				</div>
				<div class="hero-actions">
					<a class="primary-cta" href="#experience">VIEW_EXPERIENCE</a>
					<a class="secondary-cta" href="#contact">CONTACT_NODE</a>
					<p>
						I am Hieu Bui Vinh, a backend engineer working across Java, Spring, Go, cloud-native
						platforms, microservices, and distributed systems. I build production services that stay
						scalable, maintainable, and observable.
					</p>
				</div>
				<div class="mobile-stats">
					<div>
						<span>CAREER</span>
						<strong>5+Y</strong>
					</div>
					<div>
						<span>ROLES</span>
						<strong>04</strong>
					</div>
					<div>
						<span>TOEIC</span>
						<strong>870</strong>
					</div>
				</div>
			</div>

			<aside class="hero-visual">
				<div class="hero-asset">
					<div class="visual-ref">TOPOLOGY: LIVE_BACKEND</div>
					<svg
						class="diagram hero-diagram"
						viewBox="0 0 400 500"
						role="img"
						aria-label="Diagram of a distributed backend: API gateway routing to services, an event bus, workers, and data stores"
					>
						<defs>
							<pattern id="grid-hero" width="20" height="20" patternUnits="userSpaceOnUse">
								<path class="d-gridline" d="M 20 0 L 0 0 0 20" fill="none" />
							</pattern>
						</defs>
						<rect width="400" height="500" fill="url(#grid-hero)" opacity="0.45" />

						<rect class="d-node accent" x="130" y="40" width="140" height="40" />
						<text class="d-label" x="200" y="65" text-anchor="middle">API_GATEWAY</text>
						<circle class="d-dot" cx="258" cy="50" r="3" />

						<path class="d-line" d="M200 80 V110 M80 110 H320 M80 110 V140 M200 110 V140 M320 110 V140" />

						<rect class="d-node" x="30" y="140" width="100" height="40" />
						<text class="d-label small" x="80" y="164" text-anchor="middle">SVC_TOURNEY</text>
						<rect class="d-node" x="150" y="140" width="100" height="40" />
						<text class="d-label small" x="200" y="164" text-anchor="middle">SVC_BETS</text>
						<rect class="d-node" x="270" y="140" width="100" height="40" />
						<text class="d-label small" x="320" y="164" text-anchor="middle">SVC_CONFIG</text>

						<path class="d-flow" d="M80 180 V230" />
						<path class="d-flow" d="M200 180 V230" />
						<path class="d-flow" d="M320 180 V230" />

						<rect class="d-bus" x="40" y="230" width="320" height="36" />
						<text class="d-label" x="200" y="253" text-anchor="middle">EVENT_BUS // KAFKA</text>

						<path class="d-line" d="M120 266 V300 M280 266 V300" />
						<rect class="d-node" x="60" y="300" width="120" height="40" />
						<text class="d-label small" x="120" y="324" text-anchor="middle">WORKERS</text>
						<rect class="d-node" x="220" y="300" width="120" height="40" />
						<text class="d-label small" x="280" y="324" text-anchor="middle">SETTLEMENT</text>

						<path class="d-line dashed" d="M120 340 V380 M280 340 V380" />
						<rect class="d-node" x="60" y="380" width="120" height="40" />
						<text class="d-label small" x="120" y="404" text-anchor="middle">MYSQL</text>
						<rect class="d-node" x="220" y="380" width="120" height="40" />
						<text class="d-label small" x="280" y="404" text-anchor="middle">REDIS</text>

						<text class="d-label small" x="30" y="464">UPLINK: AWS // AP_SOUTHEAST</text>
						<text class="d-label green" x="30" y="482">STATUS: OPERATIONAL</text>
					</svg>
					<div class="visual-meta">
						<div><span>RUNTIME</span><strong>JAVA_17</strong></div>
						<div><span>FRAMEWORK</span><strong>SPRING</strong></div>
						<div><span>CLOUD</span><strong>AWS</strong></div>
						<div><span>PLATFORM</span><strong>K8S</strong></div>
					</div>
				</div>
				<p class="visual-caption">CURRENT_STACK: JAVA // SPRING // AWS // MICROSERVICES</p>
			</aside>
		</section>

		<section class="logs section" data-reveal>
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

						{#if log.diagram}
							<div class="log-diagram">
								<svg
									class="diagram"
									viewBox="0 0 480 160"
									role="img"
									aria-label="Banking request flow: channels through an open API to a ledger service, with RabbitMQ handling async work"
								>
									<rect class="d-node" x="20" y="50" width="100" height="40" />
									<text class="d-label small" x="70" y="74" text-anchor="middle">CHANNELS</text>
									<path class="d-flow" d="M120 70 H160" />
									<rect class="d-node accent" x="160" y="50" width="110" height="40" />
									<text class="d-label small" x="215" y="74" text-anchor="middle">OPEN_API</text>
									<circle class="d-dot" cx="260" cy="60" r="3" />
									<path class="d-line" d="M270 70 H310" />
									<rect class="d-node" x="310" y="50" width="120" height="40" />
									<text class="d-label small" x="370" y="74" text-anchor="middle">LEDGER_SVC</text>
									<path class="d-line dashed" d="M370 90 V118" />
									<rect class="d-bus" x="270" y="118" width="180" height="26" />
									<text class="d-label small" x="360" y="135" text-anchor="middle">RABBITMQ</text>
									<text class="d-label small" x="20" y="140">FLOW: LICENSE_REQUESTS</text>
								</svg>
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

		<section class="experience section" data-reveal id="experience">
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

		<section class="gallery section" data-reveal id="signals">
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
						<svg
							class="diagram"
							viewBox="0 0 640 360"
							role="img"
							aria-label="Microservice architecture diagram: clients through a gateway to auth, game, and payment services backed by MySQL and Redis"
						>
							<text class="d-label small" x="30" y="34">SIG_01 // SERVICE_TOPOLOGY</text>

							<rect class="d-node" x="30" y="158" width="100" height="44" />
							<text class="d-label small" x="80" y="184" text-anchor="middle">CLIENTS</text>

							<path class="d-flow" d="M130 180 H170" />

							<rect class="d-node accent" x="170" y="158" width="110" height="44" />
							<text class="d-label small" x="225" y="184" text-anchor="middle">GATEWAY</text>
							<circle class="d-dot" cx="270" cy="168" r="3" />

							<path class="d-line" d="M280 180 H320 M320 62 V298 M320 62 H360 M320 180 H360 M320 298 H360" />
							<text class="d-label small" x="292" y="170">REST</text>

							<rect class="d-node" x="360" y="40" width="120" height="44" />
							<text class="d-label small" x="420" y="66" text-anchor="middle">AUTH_SVC</text>
							<rect class="d-node" x="360" y="158" width="120" height="44" />
							<text class="d-label small" x="420" y="184" text-anchor="middle">GAME_SVC</text>
							<rect class="d-node" x="360" y="276" width="120" height="44" />
							<text class="d-label small" x="420" y="302" text-anchor="middle">PAY_SVC</text>

							<path class="d-line dashed" d="M480 62 H512 V118 H540 M480 180 H512 M512 180 V242 H540 M480 298 H512 V242" />
							<text class="d-label small" x="494" y="106">GRPC</text>

							<rect class="d-node" x="540" y="96" width="80" height="44" />
							<text class="d-label small" x="580" y="122" text-anchor="middle">MYSQL</text>
							<rect class="d-node" x="540" y="220" width="80" height="44" />
							<text class="d-label small" x="580" y="246" text-anchor="middle">REDIS</text>
						</svg>
						<span class="media-ref">SIG_01 // ARCHITECTURE</span>
					</div>
					<div class="meta-grid four">
						<div><span>ENTRY</span><strong>API_GATEWAY</strong></div>
						<div><span>PROTOCOLS</span><strong>REST // GRPC</strong></div>
						<div><span>SERVICES</span><strong>SPRING_BOOT</strong></div>
						<div><span>DATA</span><strong>MYSQL // REDIS</strong></div>
					</div>
				</article>

				<article class="gallery-card gallery-portrait">
					<div class="media-frame">
						<svg
							class="diagram"
							viewBox="0 0 360 480"
							role="img"
							aria-label="Event streaming diagram: producers publishing to Kafka partitions, consumed by a consumer group with a dead letter queue"
						>
							<rect class="d-node" x="100" y="40" width="160" height="40" />
							<text class="d-label small" x="180" y="64" text-anchor="middle">PRODUCERS</text>

							<path class="d-flow" d="M180 80 V128" />
							<text class="d-label small" x="60" y="120">TOPIC: TXN_EVENTS</text>

							<rect class="d-bus" x="60" y="128" width="240" height="28" />
							<text class="d-label small" x="74" y="146">P0</text>
							<rect class="d-bar" x="150" y="138" width="8" height="8" />
							<rect class="d-bar" x="190" y="138" width="8" height="8" />
							<rect class="d-bar" x="240" y="138" width="8" height="8" />

							<rect class="d-bus" x="60" y="168" width="240" height="28" />
							<text class="d-label small" x="74" y="186">P1</text>
							<rect class="d-bar" x="120" y="178" width="8" height="8" />
							<rect class="d-bar" x="205" y="178" width="8" height="8" />

							<rect class="d-bus" x="60" y="208" width="240" height="28" />
							<text class="d-label small" x="74" y="226">P2</text>
							<rect class="d-bar" x="100" y="218" width="8" height="8" />
							<rect class="d-bar" x="170" y="218" width="8" height="8" />
							<rect class="d-bar" x="250" y="218" width="8" height="8" />

							<path class="d-flow" d="M180 236 V290" />

							<rect class="d-node" x="60" y="290" width="240" height="86" />
							<text class="d-label small" x="180" y="310" text-anchor="middle">CONSUMER_GROUP</text>
							<rect class="d-node" x="80" y="322" width="52" height="38" />
							<text class="d-label small" x="106" y="345" text-anchor="middle">C0</text>
							<rect class="d-node" x="154" y="322" width="52" height="38" />
							<text class="d-label small" x="180" y="345" text-anchor="middle">C1</text>
							<rect class="d-node" x="228" y="322" width="52" height="38" />
							<text class="d-label small" x="254" y="345" text-anchor="middle">C2</text>

							<path class="d-line dashed" d="M245 376 V410" />
							<rect class="d-node" x="190" y="410" width="110" height="36" />
							<text class="d-label small" x="245" y="432" text-anchor="middle">DLQ</text>

							<text class="d-label green" x="60" y="466">PATTERN: SAGA // AT_LEAST_ONCE</text>
						</svg>
						<span class="media-ref right">SIG_02 // EVENTS</span>
					</div>
					<div class="meta-stack">
						<div><span>BROKERS</span><strong>KAFKA // RABBITMQ</strong></div>
						<div><span>PATTERNS</span><strong>SAGA // EVENT_DRIVEN</strong></div>
					</div>
				</article>

				<article class="gallery-card gallery-square">
					<div class="media-frame">
						<svg
							class="diagram"
							viewBox="0 0 400 400"
							role="img"
							aria-label="Observability diagram: latency trace sparkline with percentile meters"
						>
							<text class="d-label small" x="40" y="60">SIG_03 // LATENCY_TRACE</text>
							<circle class="d-dot" cx="330" cy="56" r="3" />
							<text class="d-label green" x="342" y="60">LIVE</text>

							<path
								class="d-area"
								d="M40 230 L80 210 L120 225 L160 190 L200 205 L240 160 L280 185 L320 150 L360 170 L360 260 L40 260 Z"
							/>
							<polyline
								class="d-spark"
								points="40,230 80,210 120,225 160,190 200,205 240,160 280,185 320,150 360,170"
							/>
							<path class="d-line" d="M40 260 H360" />

							<text class="d-label small" x="40" y="304">P50</text>
							<rect class="d-track" x="90" y="296" width="270" height="6" />
							<rect class="d-bar" x="90" y="296" width="120" height="6" />

							<text class="d-label small" x="40" y="334">P95</text>
							<rect class="d-track" x="90" y="326" width="270" height="6" />
							<rect class="d-bar" x="90" y="326" width="190" height="6" />

							<text class="d-label small" x="40" y="364">P99</text>
							<rect class="d-track" x="90" y="356" width="270" height="6" />
							<rect class="d-bar" x="90" y="356" width="240" height="6" />
						</svg>
					</div>
					<div class="annotation">
						<span>ANNOTATION</span>
						<p>
							Observability wired into every service: distributed traces, latency percentiles,
							dashboards, and alerting across Datadog, CloudWatch, Grafana, and Zipkin.
						</p>
					</div>
				</article>

				<article class="gallery-card gallery-panorama">
					<div class="media-frame">
						<svg
							class="diagram"
							viewBox="0 0 630 270"
							role="img"
							aria-label="Delivery pipeline diagram: commit, build, test, deploy, and observe stages"
						>
							<text class="d-label small" x="15" y="40">SIG_04 // DELIVERY_PIPELINE</text>

							<rect class="d-node" x="15" y="115" width="90" height="40" />
							<text class="d-label small" x="60" y="139" text-anchor="middle">COMMIT</text>
							<text class="d-label green" x="60" y="100" text-anchor="middle">✓</text>

							<path class="d-flow" d="M105 135 H142" />

							<rect class="d-node" x="142" y="115" width="90" height="40" />
							<text class="d-label small" x="187" y="139" text-anchor="middle">BUILD</text>
							<text class="d-label green" x="187" y="100" text-anchor="middle">✓</text>

							<path class="d-flow" d="M232 135 H269" />

							<rect class="d-node" x="269" y="115" width="90" height="40" />
							<text class="d-label small" x="314" y="139" text-anchor="middle">TEST</text>
							<text class="d-label green" x="314" y="100" text-anchor="middle">✓</text>

							<path class="d-flow" d="M359 135 H396" />

							<rect class="d-node" x="396" y="115" width="90" height="40" />
							<text class="d-label small" x="441" y="139" text-anchor="middle">DEPLOY</text>
							<text class="d-label green" x="441" y="100" text-anchor="middle">✓</text>

							<path class="d-flow" d="M486 135 H523" />

							<rect class="d-node accent" x="523" y="115" width="90" height="40" />
							<text class="d-label small" x="568" y="139" text-anchor="middle">OBSERVE</text>
							<circle class="d-dot" cx="604" cy="124" r="3" />

							<path class="d-line" d="M15 200 H613 M15 200 V206 M135 200 V206 M255 200 V206 M375 200 V206 M495 200 V206 M613 200 V206" />
							<text class="d-label small" x="15" y="234">ZERO_DOWNTIME_ROLLOUT // ARGOCD</text>
							<text class="d-label small" x="613" y="234" text-anchor="end">K8S_CLUSTER: PROD</text>
						</svg>
						<div class="badge-row">
							<span>AUTOMATED</span>
							<span>GITOPS</span>
						</div>
					</div>
					<div class="meta-grid three">
						<div><span>CI</span><strong>JENKINS</strong></div>
						<div><span>CD</span><strong>ARGOCD</strong></div>
						<div><span>RUNTIME</span><strong>KUBERNETES</strong></div>
					</div>
				</article>
			</div>
		</section>

		<section class="contact section" data-reveal id="contact">
			<div class="section-header-block">
				<span class="kicker">SECURE_UPLINK_ESTABLISHED // CONTACT_NODE</span>
				<h2>LET'S CONNECT</h2>
			</div>

			<div class="contact-grid">
				<div class="contact-panel">
					<div class="contact-ref">COMM_INTERFACE_v4.2</div>
					<form class="terminal-form" onsubmit={submitContact}>
						<label>
							<span>&gt; ENTER_IDENTITY_STRING</span>
							<input type="text" placeholder="YOUR_NAME" bind:value={contactName} required />
						</label>
						<label>
							<span>&gt; RETURN_PATH</span>
							<input
								type="email"
								placeholder="YOUR_EMAIL@DOMAIN.COM"
								bind:value={contactEmail}
								required
							/>
						</label>
						<label>
							<span>&gt; TRANSMISSION_BODY</span>
							<textarea
								rows="6"
								placeholder="PROJECT_SCOPE_OR_MESSAGE..."
								bind:value={contactMessage}
								required
							></textarea>
						</label>
						<button type="submit">EXECUTE_SEND</button>
						<p class="form-hint">ROUTE: OPENS_YOUR_MAIL_CLIENT // NO_DATA_STORED</p>
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
								<a
									href={node.href}
									target={node.external ? '_blank' : undefined}
									rel={node.external ? 'noreferrer' : undefined}
								>
									{node.label}
								</a>
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

	<nav class="mobile-bottom-nav" aria-label="Mobile quick links">
		<a href="#top"><span>ROOT</span></a>
		<a href="#experience"><span>FILES</span></a>
		<a href="#signals"><span>LOGS</span></a>
		<a href="#contact"><span>LINK</span></a>
	</nav>
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

	:global(::selection) {
		background: var(--gold-strong);
		color: #2f1d00;
	}

	:global(:focus-visible) {
		outline: 2px solid var(--gold-strong);
		outline-offset: 2px;
	}

	:global(.reveal-init) {
		opacity: 0;
		transform: translateY(18px);
		transition: opacity 650ms ease, transform 650ms ease;
	}

	:global(.reveal-visible) {
		opacity: 1;
		transform: none;
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
	.form-hint,
	.footer,
	.external-list a,
	.status-list span,
	.status-list strong,
	.collection-count span,
	.menu-panel a {
		font-size: 0.72rem;
		letter-spacing: 0.16em;
		text-transform: uppercase;
	}

	.brand,
	.theme-toggle,
	.secondary-cta,
	.primary-cta,
	.visual-caption,
	.media-ref,
	.badge-row span {
		font-family: 'Space Grotesk', monospace;
	}

	.brand {
		display: inline-flex;
		align-items: center;
		gap: 10px;
		font-family: 'Newsreader', serif;
		font-style: italic;
		font-size: 1.7rem;
		color: var(--gold-strong);
	}

	.brand-icon {
		font-family: 'Space Grotesk', monospace;
		font-style: normal;
		font-size: 0.95rem;
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

	.menu-toggle {
		display: none;
		border: 0;
		background: transparent;
		color: var(--gold-strong);
		font: inherit;
		letter-spacing: 0.18em;
		text-transform: uppercase;
		cursor: pointer;
	}

	.menu-panel {
		position: absolute;
		top: 100%;
		left: 0;
		right: 0;
		z-index: 40;
		display: grid;
		background: var(--surface);
		border: 1px solid var(--surface-line);
		box-shadow: var(--shadow);
	}

	.menu-panel a {
		padding: 15px 18px;
		color: var(--text-muted);
		border-bottom: 1px solid var(--surface-line);
	}

	.menu-panel a:last-child {
		border-bottom: 0;
	}

	.menu-panel a:hover,
	.menu-panel a:focus-visible {
		color: var(--gold);
		background: var(--surface-low);
	}

	.theme-toggle {
		border: 1px solid var(--surface-line);
		background: transparent;
		color: var(--gold-strong);
		padding: 8px 10px;
		cursor: pointer;
		transition: border-color 220ms ease;
	}

	.theme-toggle:hover {
		border-color: var(--gold-strong);
	}

	.section {
		padding: 34px 0 18px;
		scroll-margin-top: 84px;
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
		animation: pulse 2.4s ease-in-out infinite;
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
		grid-template-columns: auto auto minmax(0, 22rem);
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
		transition: filter 220ms ease;
	}

	.primary-cta:hover {
		filter: brightness(1.08);
	}

	.secondary-cta {
		display: inline-flex;
		align-items: center;
		justify-content: center;
		padding: 15px 22px;
		border: 1px solid var(--surface-line);
		color: var(--gold);
		transition: border-color 220ms ease;
	}

	.secondary-cta:hover {
		border-color: var(--gold-strong);
	}

	.mobile-profile,
	.mobile-stats,
	.mobile-bottom-nav {
		display: none;
	}

	.mobile-profile {
		align-items: start;
		gap: 14px;
		margin-top: 24px;
		padding: 16px;
		border-left: 2px solid var(--gold-strong);
		background: var(--surface);
	}

	.monogram {
		width: 52px;
		height: 52px;
		display: grid;
		place-items: center;
		border: 1px solid var(--surface-line);
		background: var(--surface-low);
		color: var(--gold-strong);
		font-family: 'Newsreader', serif;
		font-style: italic;
		font-size: 1.25rem;
	}

	.mobile-profile strong,
	.mobile-profile span {
		display: block;
		font-family: 'Space Grotesk', monospace;
	}

	.mobile-profile strong {
		color: var(--gold-strong);
		font-size: 0.9rem;
		letter-spacing: 0.12em;
		text-transform: uppercase;
	}

	.mobile-profile span {
		margin-top: 4px;
		color: var(--text-muted);
		font-size: 0.68rem;
		letter-spacing: 0.12em;
		text-transform: uppercase;
	}

	.mobile-profile p {
		margin: 10px 0 0;
		color: var(--text-muted);
		font-size: 0.78rem;
		line-height: 1.65;
	}

	.mobile-stats {
		grid-template-columns: repeat(3, minmax(0, 1fr));
		margin-top: 16px;
		border-top: 1px solid var(--surface-line);
		border-bottom: 1px solid var(--surface-line);
	}

	.mobile-stats div {
		padding: 14px 10px;
	}

	.mobile-stats div + div {
		border-left: 1px solid var(--surface-line);
	}

	.mobile-stats span,
	.mobile-stats strong {
		display: block;
		font-family: 'Space Grotesk', monospace;
		text-transform: uppercase;
	}

	.mobile-stats span {
		color: var(--text-faint);
		font-size: 0.58rem;
		letter-spacing: 0.14em;
	}

	.mobile-stats strong {
		margin-top: 6px;
		font-size: 1.1rem;
		color: var(--text);
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

	.diagram {
		display: block;
		width: 100%;
		height: auto;
		background: var(--surface-low);
	}

	.d-gridline {
		stroke: var(--surface-line);
		stroke-width: 1;
	}

	.d-node {
		fill: var(--surface);
		stroke: var(--surface-line);
	}

	.d-node.accent {
		stroke: var(--gold-strong);
	}

	.d-bus {
		fill: var(--surface-mid);
		stroke: var(--surface-line);
	}

	.d-label {
		fill: var(--text-muted);
		font-family: 'Space Grotesk', monospace;
		font-size: 12px;
		letter-spacing: 0.08em;
	}

	.d-label.small {
		font-size: 10px;
		fill: var(--text-faint);
	}

	.d-label.green {
		fill: var(--green);
	}

	.d-line {
		stroke: var(--text-faint);
		stroke-width: 1;
		opacity: 0.55;
		fill: none;
	}

	.d-line.dashed {
		stroke-dasharray: 3 5;
	}

	.d-flow {
		stroke: var(--gold-strong);
		stroke-width: 1.5;
		fill: none;
		stroke-dasharray: 5 7;
		animation: flow 2.4s linear infinite;
	}

	.d-dot {
		fill: var(--green);
		animation: pulse 2s ease-in-out infinite;
	}

	.d-bar {
		fill: var(--gold-strong);
	}

	.d-track {
		fill: var(--surface-high);
	}

	.d-area {
		fill: var(--gold-strong);
		opacity: 0.12;
	}

	.d-spark {
		stroke: var(--gold-strong);
		stroke-width: 1.5;
		fill: none;
	}

	@keyframes flow {
		to {
			stroke-dashoffset: -48;
		}
	}

	@keyframes pulse {
		0%,
		100% {
			opacity: 1;
		}
		50% {
			opacity: 0.35;
		}
	}

	.visual-ref,
	.media-ref {
		position: absolute;
		top: 16px;
		left: 16px;
		z-index: 1;
		padding: 6px 10px;
		border: 1px solid var(--surface-line);
		background: color-mix(in srgb, var(--bg) 84%, transparent);
		color: var(--text-muted);
		font-size: 0.62rem;
		letter-spacing: 0.14em;
		text-transform: uppercase;
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

	.log-diagram {
		margin-bottom: 18px;
		border: 1px solid var(--surface-line);
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
		transition: border-left-color 220ms ease;
	}

	.experience-card:hover {
		border-left-color: var(--gold-strong);
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
		transition: border-color 220ms ease, color 220ms ease;
	}

	.chip-row span:hover {
		border-color: var(--gold-strong);
		color: var(--gold);
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
		transition: border-color 220ms ease;
	}

	.gallery-card:hover {
		border-color: color-mix(in srgb, var(--gold-strong) 45%, var(--surface-line));
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
		font-size: 0.62rem;
		letter-spacing: 0.14em;
		text-transform: uppercase;
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
		transition: border-color 220ms ease;
	}

	.terminal-form input:focus,
	.terminal-form textarea:focus {
		outline: none;
		border-bottom-color: var(--gold-strong);
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
		transition: filter 220ms ease;
	}

	.terminal-form button:hover {
		filter: brightness(1.08);
	}

	.form-hint {
		margin: -14px 0 0;
		color: var(--text-faint);
		opacity: 0.8;
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

	.mobile-bottom-nav {
		position: fixed;
		left: 0;
		right: 0;
		bottom: 0;
		z-index: 40;
		grid-template-columns: repeat(4, minmax(0, 1fr));
		height: 62px;
		background: color-mix(in srgb, var(--surface) 94%, transparent);
		backdrop-filter: blur(14px);
		border-top: 1px solid var(--surface-line);
	}

	.mobile-bottom-nav a {
		display: grid;
		place-items: center;
		color: var(--text-faint);
		font-family: 'Space Grotesk', monospace;
		font-size: 0.56rem;
		letter-spacing: 0.18em;
		text-transform: uppercase;
	}

	@media (prefers-reduced-motion: reduce) {
		:global(html) {
			scroll-behavior: auto;
		}

		.d-flow,
		.d-dot,
		.status-dot {
			animation: none;
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
			padding-bottom: 84px;
		}

		.topbar {
			gap: 14px;
			grid-template-columns: minmax(0, 1fr) auto;
			padding: 12px 0;
		}

		.brand {
			font-size: 1.35rem;
		}

		.nav,
		.system-status,
		.theme-toggle {
			display: none;
		}

		.menu-toggle {
			display: inline-flex;
		}

		h1 {
			max-width: 9ch;
			font-size: clamp(3rem, 13vw, 4.2rem);
			line-height: 1;
		}

		h2 {
			font-size: clamp(2.1rem, 14vw, 3rem);
		}

		.section {
			padding-top: 28px;
		}

		.hero {
			gap: 18px;
		}

		.hero-visual {
			display: none;
		}

		.mobile-profile {
			display: grid;
			grid-template-columns: auto minmax(0, 1fr);
		}

		.hero-actions {
			grid-template-columns: 1fr;
			gap: 12px;
		}

		.primary-cta,
		.secondary-cta {
			width: 100%;
		}

		.hero-actions p {
			order: 3;
			max-width: none;
			padding-top: 14px;
			border-top: 1px solid var(--surface-line);
			font-size: 0.8rem;
		}

		.mobile-stats,
		.mobile-bottom-nav {
			display: grid;
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

		.log-card {
			background: transparent;
			box-shadow: none;
			border-right: 0;
			border-left: 0;
			padding-inline: 0;
		}

		.section-header-block {
			padding-left: 14px;
		}

		.terminal-form input,
		.terminal-form textarea {
			font-size: 1rem;
		}

		.footer {
			margin-top: 12px;
			padding-bottom: 0;
		}
	}
</style>
