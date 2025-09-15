# ChatBoot-Projeto6-Koru_Desesnvolve_Boticario-
<!DOCTYPE html>
<html lang="pt-BR">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ChatBotNDSP</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

    <style>
        :root {
            --primary-color: hwb(246 9% 2%);
            --primary-hover: lab(80% -79.23 76.55);
            --error-color: hwb(0 3% 1%);
            --error-bg: #f8d7da;
            --error-text: oklab(90.877% -0.03891 0.18134);
            --border-color: #e0e0e0;
            --background-light: #f0f2f5;
        }

        body {
            font-family: 'Roboto', Arial, sans-serif;
            background-color: var(--background-light);
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            box-sizing: border-box;
        }

        .container {
            background-color: #ffffff;
            border-radius: 12px;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 700px;
            padding: 30px;
            box-sizing: border-box;
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

        header h1 {
            color: #333;
            font-size: 2.5rem;
            margin: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        header i {
            color: var(--primary-color);
        }

        section {
            margin-bottom: 25px;
            padding-bottom: 25px;
            border-bottom: 1px solid var(--border-color);
        }

        section:last-of-type {
            border-bottom: none;
        }

        label {
            display: block;
            font-weight: bold;
            margin-bottom: 8px;
            color: #555;
            font-size: 1.1rem;
        }

        .input-group {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        input[type="text"] {
            flex: 1;
            padding: 12px;
            border: 1px solid #ccc;
            border-radius: 8px;
            box-sizing: border-box;
            font-size: 1rem;
            transition: border-color 0.3s, box-shadow 0.3s;
        }

        input[type="text"]:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 5px rgba(76, 175, 80, 0.5);
        }



        button {
            padding: 12px 20px;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1rem;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: var(--primary-hover);
        }

        #respostaBot {
            padding: 12px;
            background-color: #f1f1f1;
            border-radius: 8px;
            font-size: 1rem;
            color: #333;
            margin-top: 15px;
        }

        .chat-historico {
            max-height: 300px;
            overflow-y: auto;
            padding: 12px;
            background-color: #f9f9f9;
            border-radius: 8px;
            border: 1px solid var(--border-color);
            margin-top: 15px;
        }

        .mensagem {
            margin-bottom: 10px;
            padding: 10px;
            border-radius: 6px;
        }

        .usuario {
            background-color: #e0f7fa;
            text-align: right;
        }

        .bot {
            background-color: #e8f5e9;
            text-align: left;
        }
    </style>
</head>

<body>
    <div class="container">
        <header>
            <h1><i class="fas fa-robot"></i> ChatBot</h1>
        </header>

        <section>
            <label for="entradaUsuario">Digite sua mensagem:</label>
            <div class="input-group">
                <input type="text" id="entradaUsuario" placeholder="Escreva algo...">
                <button id="botaoEnviar" type="button">Enviar</button>
                <button type="submit">Enviar</button>
                <button type="reset">Limpar</button>
            </div>
        </section>

        <section>
            <label>Resposta:</label>
            <div id="respostaBot">Aguardando sua mensagem...</div>
            <div id="chatHistorico" class="chat-historico"></div>
        </section>
    </div>

    <script>
        document.getElementById('botaoEnviar').addEventListener('click', function () {
            const entrada = document.getElementById('entradaUsuario').value.trim();
            const resposta = document.getElementById('respostaBot');
            const chat = document.getElementById('chatHistorico');

            if (entrada === "") {
                resposta.innerText = "Por favor, digite uma mensagem.";
                resposta.style.backgroundColor = "var(--error-bg)";
                resposta.style.color = "var(--error-text)";
                return;
            }

            // Adiciona mensagem do usuário
            const msgUsuario = document.createElement('div');
            msgUsuario.className = 'mensagem usuario';
            msgUsuario.innerText = entrada;
            chat.appendChild(msgUsuario);

            // Gera resposta do bot
            const respostaTexto = gerarResposta(entrada);
            resposta.innerText = respostaTexto;
            resposta.style.backgroundColor = "#f1f1f1";
            resposta.style.color = "#333";

            const msgBot = document.createElement('div');
            msgBot.className = 'mensagem bot';
            msgBot.innerText = respostaTexto;
            chat.appendChild(msgBot);

            // Limpa campo
            document.getElementById('entradaUsuario').value = '';
            chat.scrollTop = chat.scrollHeight;
        });

        function gerarResposta(texto) {
            const msg = texto.toLowerCase();
            if (msg.includes("olá")) return "Olá! Como posso te ajudar?";
            if (msg.includes("tempo")) return "Não tenho acesso ao clima agora, mas posso te ajudar com outras coisas!";
            if (msg.includes("nome")) return "Meu nome é ChatBotNDSP, prazer!";
            return "Interessante! Me conte mais.";
        }
    </script>
</body>

</html>
