<!DOCTYPE html>
<html lang="ro">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Caesar Cipher Custom Element</title>
</head>
<body>
    <!-- Custom element Caesar Cipher -->
    <caesar-cipher shift="3"></caesar-cipher>

    <!-- JavaScript pentru custom element -->
    <script>
        class CaesarCipherElement extends HTMLElement {
            constructor() {
                super();
                this.attachShadow({ mode: 'open' });
            }

            connectedCallback() {
                // Preluăm valoarea shift
                const shift = parseInt(this.getAttribute('shift')) || 0;

                // Structura HTML pentru input și output
                this.shadowRoot.innerHTML = `
                    <style>
                        input {
                            margin-bottom: 10px;
                            padding: 5px;
                            font-size: 16px;
                        }
                        button {
                            padding: 5px 10px;
                            font-size: 16px;
                            cursor: pointer;
                        }
                        p {
                            margin-top: 10px;
                            font-weight: bold;
                        }
                    </style>
                    <input type="text" id="caesar-input" placeholder="Introdu textul aici">
                    <button id="encrypt-btn">Criptează</button>
                    <p id="output"></p>
                `;

                // Referințe către elementele din shadow DOM
                const inputField = this.shadowRoot.querySelector('#caesar-input');
                const encryptButton = this.shadowRoot.querySelector('#encrypt-btn');
                const outputParagraph = this.shadowRoot.querySelector('#output');

                // Funcție pentru criptare la apăsarea butonului
                encryptButton.addEventListener('click', () => {
                    const text = inputField.value;
                    const encryptedText = this.encryptCaesar(text, shift);
                    outputParagraph.textContent = encryptedText;
                });
            }

            // Metodă pentru criptare folosind Caesar Cipher
            encryptCaesar(text, shift) {
                return text.split('').map(char => {
                    if (char.match(/[a-z]/i)) {
                        let code = char.charCodeAt(0);
                        if (code >= 65 && code <= 90) {
                            return String.fromCharCode(((code - 65 + shift) % 26) + 65);
                        } else if (code >= 97 && code <= 122) {
                            return String.fromCharCode(((code - 97 + shift) % 26) + 97);
                        }
                    }
                    return char;
                }).join('');
            }
        }

        // Înregistrăm noul custom element
        customElements.define('caesar-cipher', CaesarCipherElement);
    </script>
</body>
</html>
