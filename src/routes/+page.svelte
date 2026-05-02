<script>
	import { fade } from 'svelte/transition';
	import miFoto from '$lib/assets/ProfileMePablo.png';

	import ModalContacto from './components/ModalContacto.svelte';

    let showContact = $state(false);

    const toggleModal = () => showContact = !showContact;

	let name = 'Pablo';
	let role = 'Estudiante de Ingenieria en Ciencias y Sistemas';
	let location = 'Guatemala';

	let misProyectos = $state([
		{
			titulo: 'Aplicación Creador de diagramas de Flujo',
			descripcion:
				'Aplicación Android que permite crear diagramas de flujo en base a instrucciones en pseudocodigo. Implementa principios de compiladores y permite visualizar los diagramas que son personalizables',
			tipo: 'mobile',
			imagenes: [
				'/proyectos/Flujo0.jpeg',
				'/proyectos/Flujo1.jpeg',
				'/proyectos/Flujo2.jpeg',
				'/proyectos/Flujo3.jpeg',
				'/proyectos/Flujo4.jpeg',
				'/proyectos/Flujo5.jpeg'
			],
			tecnologias: ['Kotlin', 'Java', 'Android SDK'],
			repo: 'https://github.com/pablo-mald03/Practica-No1-Compi-1',
			index: 0
		},
		{
			titulo: 'Aplicación Creador de Formularios',
			descripcion:
				"Aplicación Android que permite crear formularios desde un lenguaje de alto nivel. Aplicando principios de compiladores. Y conexion a API'S en servidores remotos",
			tipo: 'mobile',
			imagenes: [
				'/proyectos/PkmPic0.jpeg',
				'/proyectos/PkmPic1.jpeg',
				'/proyectos/PkmPic2.jpeg',
				'/proyectos/PkmPic3.jpeg',
				'/proyectos/PkmPic4.jpeg',
				'/proyectos/PkmPic5.jpeg'
			],
			tecnologias: ['Kotlin', 'Java', 'Android SDK', 'API REST', 'MySQL'],
			repo: 'https://github.com/pablo-mald03/Proyecto-No1-Compi-1/',
			index: 0
		},
		{
			titulo: 'Aplicación de Cine',
			descripcion:
				'Aplicación web para gestion de cines. Implementando tecnologias de cliente servidor. Permite diferentes roles: usuarios, anunciantes, administradores. Y permite la compra de boletos',
			tipo: 'desktop',
			imagenes: [
				'/proyectos/CinemaPic0.png',
				'/proyectos/CinemaPic1.png',
				'/proyectos/CinemaPic2.png',
				'/proyectos/CinemaPic3.png',
				'/proyectos/CinemaPic4.png',
				'/proyectos/CinemaPic5.png',
				'/proyectos/CinemaPic6.png'
			],
			tecnologias: ['API REST', 'Java', 'TypeScript', 'MySQL', 'Angular'],
			repo: 'https://github.com/pablo-mald03/proyecto-No2-IPC2',
			index: 0
		},
		{
			titulo: 'Aplicación de analizadores Sintacticos',
			descripcion:
				'Aplicación web para aprender a crear analizadores sintacticos descendentes. Implementa tecnologias cliente servidor que permiten generar dinamicamente analizadores sintacticos descendentes y poder visualizar su comportamiento en analisis de cadenas de entrada',
			tipo: 'desktop',
			imagenes: [
				'/proyectos/WisonPic0.png',
				'/proyectos/WisonPic1.png',
				'/proyectos/WisonPic2.png',
				'/proyectos/WisonPic3.png',
				'/proyectos/WisonPic4.png'
			],
			tecnologias: ['API REST', 'Java', 'JavaScript', 'MySQL', 'Svelte'],
			repo: 'https://github.com/pablo-mald03/Practica-No2-Compi-1',
			index: 0
		}
	]);

	const next = (p) => {
		p.index = (p.index + 1) % p.imagenes.length;
	};

	const prev = (p) => {
		p.index = (p.index - 1 + p.imagenes.length) % p.imagenes.length;
	};
</script>

<section id="sobre-mi" class="about">
	<div class="section-container">
		<div class="about-content">
			<div class="profile-pic">
				<img src={miFoto} alt="Foto de {name}" />
			</div>
			<div class="about-text">
				<h1>Hola, soy <span class="highlight">{name}</span></h1>
				<h2>{role}</h2>
				<p>
					Soy alguien que siguió ingeniería y el desarrollo de software. Me gusta mucho programar y
					todo lo hago con cariño hacia mi carrera, actualmente soy estudiante y me dedico a hacer
					proyectos en una gran variedad de lenguajes de programación. Me gusta explorar y aprender
					por mi cuenta :)
				</p>
				<div class="cta-buttons">
					<button class="btn-primary" onclick={toggleModal}>Contáctame</button>
					<!-- <a href="/cv-pablo.pdf" download class="btn-secondary">Descargar CV</a> -->
				</div>
			</div>
		</div>
	</div>
</section>

<section id="experiencia" class="cv-info">
	<div class="section-container">
		<h2 class="section-title">Mis areas experimentadas</h2>
		<div class="cv-grid">
			<div class="cv-card">
				<h3>Educación</h3>
				<ul>
					<li>
						<strong>Ingeniería en Ciencias y Sistemas</strong><br />
						Universidad San Carlos de Guatemala
					</li>
					<li>
						<strong>Semestres completados</strong><br />
						5/10 semestres
					</li>
				</ul>
			</div>

			<div class="cv-card">
				<h3>Mi experiencia en desarrollo</h3>
				<div class="tags">
					<span>Java</span>
					<span>Kotlin</span>
					<span>C++</span>
					<span>JavaScript</span>
					<span>MySQL</span>
					<span>Qt Framework</span>
				</div>
			</div>

			<div class="cv-card">
				<h3>Desarrollo web</h3>
				<div class="tags">
					<span>API REST</span>
					<span>Svelte</span>
					<span>Angular</span>
				</div>
			</div>
		</div>
	</div>
</section>

<section id="proyectos" class="projects-section">
	<div class="section-container">
		<h2 class="section-title">Proyectos Realizados</h2>
		<div class="projects-column">
			{#each misProyectos as proyecto}
				<div class="project-card">
					<div class="carousel-master {proyecto.tipo}">
						<button class="nav-btn prev" onclick={() => prev(proyecto)}>‹</button>

						<div class="image-container">
							{#each [proyecto.imagenes[proyecto.index]] as currentImg (currentImg)}
								<img src={currentImg} alt="Preview" transition:fade={{ duration: 300 }} />
							{/each}
						</div>

						<button class="nav-btn next" onclick={() => next(proyecto)}>›</button>

						<div class="dots">
							{#each proyecto.imagenes as _, i}
								<div class="dot" class:active={i === proyecto.index}></div>
							{/each}
						</div>
					</div>

					<div class="project-info">
						<h3>{proyecto.titulo}</h3>
						<p>{proyecto.descripcion}</p>

						<div class="tags" style="margin-bottom: 1.5rem;">
							{#each proyecto.tecnologias as tech}
								<span>{tech}</span>
							{/each}
						</div>

						<a href={proyecto.repo} target="_blank" class="btn-github">Ver GitHub</a>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<ModalContacto show={showContact} email="pablomaldonadobs2603@gmail.com" onAceptar={toggleModal} />

<style>
	:global(body) {
		background-color: var(--bg-color);
		color: var(--text-color);
	}

	.section-title {
		font-family: var(--font-mono);
		font-size: 2.2rem;
		color: var(--accent);
		text-align: center;
		margin-bottom: 4rem;
		position: relative;
		text-transform: uppercase;
	}

	.section-title::after {
		content: '';
		display: block;
		width: 60px;
		height: 4px;
		background: var(--accent);
		margin: 1rem auto 0;
		border-radius: 2px;
	}

	.projects-section {
		padding: 8rem 0;
		background-color: #0f172a;
	}

	.section-container {
		max-width: 1100px;
		margin: 0 auto;
		padding: 0 2rem;
		width: 100%;
	}

	.about {
		padding: 6rem 0;
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 80vh;
		background:
			radial-gradient(circle at top right, rgba(243, 166, 0, 0.05), transparent),
			linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
	}

	.about-text p {
		max-width: 600px;
		margin: 1.5rem 0;
		font-size: 1.1rem;
		color: #cbd5e1;
	}

	.cv-info {
		padding: 6rem 0;
		background-color: #0b1120;
	}

	.cv-card {
		background: var(--card-bg);
		color: var(--text-color);
		padding: 2rem;
		border-radius: 15px;
		box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
		border: 1px solid rgba(255, 255, 255, 0.05);
	}

	.tags span {
		background: #334155;
		color: var(--accent);
		padding: 0.3rem 0.8rem;
		border-radius: 5px;
		font-size: 0.8rem;
		font-family: var(--font-mono);
		border: 1px solid rgba(243, 166, 0, 0.2);
	}

	.about-content {
		display: flex;
		align-items: center;
		gap: 3rem;
		flex-wrap: wrap;
	}

	.profile-pic img {
		width: 250px;
		height: 250px;
		border-radius: 20px;
		object-fit: cover;
		border: 4px solid var(--accent);
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
	}

	.about-text h1 {
		font-size: 3rem;
		margin-bottom: 0.5rem;
	}

	.highlight {
		color: var(--accent);
	}

	.cta-buttons {
		display: flex;
		gap: 1rem;
	}

	.btn-primary {
		background-color: var(--accent);
		color: rgb(7, 7, 7);
		padding: 0.8rem 1.5rem;
		border-radius: 5px;
		text-decoration: none;
		font-weight: bold;
		border: none;
		cursor: pointer;
		font-size: 1rem;
	}

	.btn-secondary {
		border: 2px solid var(--accent);
		color: var(--accent);
		padding: 0.8rem 1.5rem;
		border-radius: 5px;
		text-decoration: none;
		font-weight: bold;
	}

	.cv-grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
		gap: 2rem;
		max-width: 1200px;
		margin: 0 auto;
	}

	.cv-card h3 {
		margin-bottom: 1.5rem;
		border-bottom: 2px solid var(--accent);
		display: inline-block;
	}

	.cv-card ul {
		list-style: none;
	}

	.cv-card li {
		margin-bottom: 1rem;
	}

	.tags {
		display: flex;
		flex-wrap: wrap;
		gap: 0.5rem;
	}

	@media (max-width: 768px) {
		.about-content {
			flex-direction: column;
			text-align: center;
		}

		.cta-buttons {
			justify-content: center;
		}
	}

	.projects-section {
		padding: 6rem 0;
		background-color: #0f172a;
	}

	.section-title {
		text-align: center;
		font-size: 2.5rem;
		color: var(--text-color);
		margin-bottom: 3rem;
	}

	.projects-column {
		display: flex;
		flex-direction: column;
		gap: 4rem;
		max-width: 900px;
		margin: 0 auto;
	}

	.project-card {
		background: var(--card-bg);
		border-radius: 15px;
		overflow: hidden;
		box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
		border: 1px solid rgba(255, 255, 255, 0.05);
	}

	.carousel-master {
		position: relative;
		background: #050811;
		display: flex;
		align-items: center;
		justify-content: center;
		overflow: hidden;
		width: 100%;
	}

	.carousel-master.mobile {
		height: 500px;
	}

	.carousel-master.desktop {
		aspect-ratio: 16 / 9;
	}

	.image-container {
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.image-container img {
		max-width: 100%;
		max-height: 100%;
		object-fit: contain;
	}

	.nav-btn {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		background: rgba(0, 0, 0, 0.5);
		color: var(--accent);
		border: none;
		font-size: 1.5rem;
		width: 40px;
		height: 40px;
		cursor: pointer;
		z-index: 10;
		border-radius: 50%;
		transition: all 0.3s ease;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.nav-btn:hover {
		background: var(--accent);
		color: #000;
	}

	.prev {
		left: 15px;
	}
	.next {
		right: 15px;
	}

	.dots {
		position: absolute;
		bottom: 15px;
		display: flex;
		gap: 8px;
	}

	.dot {
		width: 8px;
		height: 8px;
		background: rgba(255, 255, 255, 0.3);
		border-radius: 50%;
		transition: 0.3s;
	}

	.dot.active {
		background: var(--accent);
		width: 18px;
		border-radius: 10px;
	}

	.project-info {
		padding: 2rem;
	}

	.project-info h3 {
		color: var(--accent);
		font-size: 1.5rem;
		margin-bottom: 1rem;
	}

	.project-info .tags span {
		font-size: 0.9rem;
		padding: 0.2rem 0.6rem;
		opacity: 0.9;
		border-color: rgba(243, 166, 0, 0.3);
	}

	.project-info p {
		color: #cbd5e1;
		margin-bottom: 2rem;
	}

	.btn-github {
		display: inline-block;
		background-color: transparent;
		color: var(--text-color);
		border: 2px solid #334155;
		padding: 0.6rem 1.2rem;
		border-radius: 5px;
		text-decoration: none;
		font-family: var(--font-mono);
		font-weight: bold;
		transition: all 0.3s ease;
	}

	.btn-github:hover {
		border-color: var(--accent);
		color: var(--accent);
	}
</style>
