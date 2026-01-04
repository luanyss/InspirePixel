<template>
    <footer>
        <div class="footer-grid">
            <div class="col">
                <h3>Contato</h3>
                <p>contato@inspirelens.com</p>
                <p>Central de ajuda</p>
                <p>Rio de Janeiro - Brasil</p>
            </div>

            <div class="col">
                <h3>Sobre</h3>
                <p>Políticas</p>
                <p>Privacidade</p>
                <p>Blog</p>
            </div>

            <div class="col assine">
                <h3>Assine nossa newsletter</h3>
                <div class="newsletter-box">
                    <input type="email" placeholder="Seu email">
                    <button>Inscrever-se</button>
                </div>
            </div>
        </div>

        <div class="social-icons">
            <span>f</span> <span>in</span> <span>📸</span> <span>𝕏</span>
        </div>
    </footer>
</template>

<style scoped lang="scss">
footer {
    background-color: var(--footer-bg);
    padding: 4rem 2rem 2rem;
    border-top: 1px solid #eee;

    .footer-grid {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: 1fr 1fr 1.5fr; // Newsletter é um pouco maior
        gap: 40px;
        /* ABAIXO ESTÁ A PARTE MOBILE */
    @media (max-width: 768px) { //Se a tela for menor que um tablet, aplique estas regras novas".
        grid-template-columns: 1fr; /* Celular: Tudo vira 1 coluna só */
        text-align: center; /* Centraliza o texto para ficar mais bonito no celular */
        
        .assine {
            margin-top: 20px; /* Dá um espaço extra para a newsletter */
        }
    }
}
    }

    h3 {
        margin-bottom: 1.5rem;
        font-size: 1.1rem;
    }

    p {
        margin-bottom: 0.8rem;
        color: #666;
        font-size: 0.9rem;
    }

    .newsletter-box {
        display: flex;
        flex-direction: column;
        gap: 10px;

        input {
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 4px;
            background: #f9f9f9;
        }

        button {
            background-color: var(--pink-primary);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
        }
    }

    .social-icons {
        margin-top: 4rem;
        text-align: center;
        display: flex;
        justify-content: center;
        gap: 20px;
        font-size: 1.5rem;
        opacity: 0.7;
    }
</style>