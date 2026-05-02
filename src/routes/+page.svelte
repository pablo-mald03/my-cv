
<script>

    import miFoto from '$lib/assets/ProfileMePablo.png';

    let name = "Pablo";
    let role = "Estudiante de Ingenieria en Ciencias y Sistemas";
    let location = "Guatemala";

</script>

<section id="sobre-mi" class="hero">
    <div class="hero-content">
        <div class="profile-pic">
            <img src={miFoto} alt="Foto de {name}" />
        </div>
        <div class="hero-text">
            <h1>Hola, soy <span class="highlight">{name}</span></h1>
            <h2>{role}</h2>
            <p>
                Soy alguien que siguió ingeniería y el desarrollo de software. 
                Me gusta mucho programar y todo lo hago con cariño hacia mi carrera,
                actualmente soy estudiante y me dedico a hacer proyectos en una gran variedad
                de lenguajes de programación. Me gusta explorar y aprender por mi cuenta :)
            </p>
            <div class="cta-buttons">
                <a href="#contacto" class="btn-primary">Contáctame</a>
                <a href="/cv-pablo.pdf" download class="btn-secondary">Descargar CV</a>
            </div>
        </div>
    </div>
</section>


<section id="experiencia" class="cv-info">
    <div class="cv-grid">
        <div class="cv-card">
            <h3>Educación</h3>
            <ul>
                <li>
                    <strong>Ingeniería en Ciencias y Sistemas</strong><br>
                    Universidad San Carlos de Guatemala 
                </li>
                <li>
                    <strong>Semestres completados</strong><br>
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
</section>

<style>

:global(body) {
        background-color: var(--bg-color);
        color: var(--text-color);
    }

    .hero {
        padding: 4rem 0;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 80vh;
        background: radial-gradient(circle at top right, rgba(243, 166, 0, 0.05), transparent),
                    linear-gradient(135deg, #0f172a 0%, #1e293b 100%);
    }

    .hero-text p {
        max-width: 600px;
        margin: 1.5rem 0;
        font-size: 1.1rem;
        color: #cbd5e1;
    }

    .cv-info {
        padding: 4rem 0;
        background-color: #0b1120; 
        margin: 0 -2rem; 
        padding: 4rem 2rem;
    }

    .cv-card {
        background: var(--card-bg); 
        color: var(--text-color);
        padding: 2rem;
        border-radius: 15px;
        box-shadow: 0 10px 25px rgba(0,0,0,0.2);
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

    .hero-content {
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
        box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    }

    .hero-text h1 {
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
        .hero-content {
            flex-direction: column;
            text-align: center;
        }
        
        .cta-buttons {
            justify-content: center;
        }
    }
</style>