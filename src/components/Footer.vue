<script setup>
// 1. Importando os ícones como constantes (lembre de salvar os SVGs na pasta assets)
import iconeFace from "../assets/facebook.svg"
import iconeLinkedin from "../assets/linkedin.svg"
import iconeInsta from "../assets/instagram.svg"
import iconeX from "../assets/twitter.svg"
</script>

<template>
    <footer>
        <section class="footer-container">
            <div class="footer-column">
                <h3>Contato</h3>
                <ul>
                    <li>contato@inspirelens.com</li>
                    <li>Central de ajuda</li>
                    <li>Rio de Janeiro - Brasil</li>
                </ul>
            </div>

            <div class="footer-column">
                <h3>Sobre</h3>
                <ul>
                    <li>Políticas</li>
                    <li>Políticas de privacidade</li>
                    <li>Blog</li>
                </ul>
            </div>

            <div class="footer-column assine">
                <h3>Assine nossa newsletter</h3>
                <div class="newsletter-input">
                    <input type="email" placeholder="Seu e-mail">
                    <button type="button">Enviar</button>
                </div>
            </div>
        </section>

        <section class="social-section">
            <div class="social-icons">
                <a href="#"><img :src="iconeFace" alt="Facebook"></a>
                <a href="#"><img :src="iconeLinkedin" alt="LinkedIn"></a>
                <a href="#"><img :src="iconeInsta" alt="Instagram"></a>
                <a href="#"><img :src="iconeX" alt="Twitter"></a>
            </div>
        </section>
    </footer>
</template>

<style scoped lang="scss">
footer {
    background-color: var(--footer-bg);
    padding: 3rem 2rem;
    color: var(--text-color);
    border-top: 1px solid #eee;

    .footer-container {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr; // 3 colunas no PC
        gap: 40px;

        @media (max-width: 768px) {
            grid-template-columns: 1fr; // 1 coluna no celular
            text-align: center;
        }
    }

    .footer-column {
        text-align: left; // Garante o alinhamento à esquerda

        h3 {
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
            color: var(--text-color);
        }

        ul {
            list-style: none; // Remove as bolinhas
            padding: 0; // Remove o recuo padrão do navegador
            margin: 0;

            li {
                margin-bottom: 0.8rem;
                font-size: 0.9rem;
                color: var(--text-color);
                opacity: 0.8;
                line-height: 1.4; // Melhora o espaçamento entre as linhas
            }
        }
    }

    .newsletter-input {
        display: flex;
        gap: 10px;

        input {
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            flex: 1;
        }

        button {
            background-color: #E1306C;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: bold;
        }

        @media (max-width: 480px) {
            flex-direction: column; // Botão fica embaixo do input em telas bem pequenas
        }
    }

    .social-section {
        margin-top: 3rem;
        border-top: 1px solid #eee;
        padding-top: 2rem;

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 25px;

            img {
                width: 20px;
                height: 20px;
                transition: transform 0.3s;

                &:hover {
                    transform: translateY(-5px);
                }
            }
        }
    }
}
</style>