<script>
	import favicon from '$lib/assets/ProfileMePablo.png';
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
	<title>About Pablo</title>
</svelte:head>

<nav class="navbar">
	<a href="/" class="logo">Pablo_Maldonado</a>

	<ul class="nav-links">
		<li><a href="/">Inicio</a></li>
		<li><a href="#proyectos">Proyectos</a></li>
		<li><a href="#experiencia">Experiencia</a></li>
		<li><a href="#contacto">Contacto</a></li>
	</ul>
</nav>

<main class="container">
	{@render children()}
</main>

<footer class="main-footer">
    <div class="footer-grid">
        <div class="footer-section">
            <h3 class="footer-logo">Pablo_Maldonado</h3>
            <p>Me gusta programar y aprender cosas nuevas.</p>
        </div>

        <div class="footer-section">
            <h4>Navegación</h4>
            <ul>
                <li><a href="/">Inicio</a></li>
                <li><a href="#proyectos">Proyectos</a></li>
                <li><a href="#experiencia">Experiencia</a></li>
            </ul>
        </div>

        <div class="footer-section">
            <h4>Contacto</h4>
            <div class="social-links">
                <a href="https://github.com/pablo-mald03" target="_blank">GitHub</a>
            </div>
        </div>
    </div>

    <div class="footer-bottom">
        <p>© {new Date().getFullYear()} - Creado por Pablo</p>
    </div>
</footer>
