<script>
    import { fade, scale } from 'svelte/transition';

    /* Usamos Svelte 5 $props */
    let { show = false, email = "example@gmail.com", onAceptar } = $props();
</script>

{#if show}
    <!-- svelte-ignore a11y_click_events_have_key_events -->
    <!-- svelte-ignore a11y_no_static_element_interactions -->
    <div
        class="modal-overlay"
        transition:fade={{ duration: 150 }}
        onclick={onAceptar}
    >
        <!-- svelte-ignore a11y_interactive_supports_focus -->
        <div
            class="custom-modal-card"
            transition:scale={{ duration: 250, start: 0.9, opacity: 0 }}
            onclick={(e) => e.stopPropagation()}
            role="dialog"
        >
            <div class="modal-header-custom">
                <span class="header-title">Contacto</span>
            </div>

            <div class="modal-body-custom">
                <p class="greeting">¡Hola! Puedes contactarme por mi correo:</p>
                <div class="email-badge">
                    <code>{email}</code>
                </div>
                <p class="sub-text">Estare emocionado por aprender cosas nuevas. Gracias por visitar mi portfolio</p>
            </div>

            <div class="modal-footer-custom">
                <button 
                    class="btn-modal-action" 
                    onclick={onAceptar}
                >
                    CONTINUAR
                </button>
            </div>
        </div>
    </div>
{/if}

<style>
    .modal-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.85);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 9999;
        backdrop-filter: blur(4px);
    }

    .custom-modal-card {
        background: #1e293b;
        border: 1px solid var(--accent);
        border-radius: 12px;
        width: 90%;
        max-width: 400px;
        overflow: hidden;
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
    }

    .modal-header-custom {
        padding: 1rem;
        background: rgba(243, 166, 0, 0.1);
        border-bottom: 1px solid rgba(243, 166, 0, 0.2);
        text-align: center;
    }

    .header-title {
        color: var(--accent);
        font-family: var(--font-mono);
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 2px;
    }

    .modal-body-custom {
        padding: 2.5rem 1.5rem;
        text-align: center;
    }

    .greeting {
        color: #f8fafc;
        margin-bottom: 1rem;
    }

    .email-badge {
        background: #0f172a;
        padding: 0.8rem;
        border-radius: 6px;
        border: 1px dashed var(--accent);
        margin: 1.5rem 0;
    }

    .email-badge code {
        color: var(--accent);
        font-size: 1.1rem;
        font-family: var(--font-mono);
    }

    .sub-text {
        font-size: 0.9rem;
        color: #94a3b8;
        line-height: 1.5;
    }

    .modal-footer-custom {
        padding: 1.5rem;
        display: flex;
        justify-content: center;
    }

    .btn-modal-action {
        background: var(--accent);
        color: #000;
        border: none;
        padding: 0.7rem 2rem;
        border-radius: 4px;
        font-weight: bold;
        font-family: var(--font-mono);
        cursor: pointer;
        transition: transform 0.2s ease;
    }

    .btn-modal-action:hover {
        transform: scale(1.05);
        filter: brightness(1.1);
    }
</style>