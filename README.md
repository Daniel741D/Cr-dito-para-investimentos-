<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crédito para Investimento</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f7f6;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .container {
            background-color: white;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
            text-align: center;
        }

        h1 {
            font-size: 24px;
            color: #333;
            margin-bottom: 20px;
        }

        input, select, button {
            width: 100%;
            padding: 12px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ccc;
            font-size: 16px;
        }

        button {
            background-color: #28a745;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #218838;
        }

        select {
            background-color: #f8f9fa;
        }

        .form-section {
            margin-bottom: 20px;
        }

        .section-title {
            font-size: 18px;
            color: #555;
            margin-bottom: 8px;
        }

        .option-group {
            display: flex;
            justify-content: space-between;
            gap: 10px;
        }

        .option-group select {
            width: 48%;
        }
    </style>
</head>
<body>

    <div class="container">
        <h1>Crédito para Investimento</h1>
        <form id="form">
            <div class="form-section">
                <input type="text" name="nome" placeholder="Nome Completo" required>
            </div>
            <div class="form-section">
                <input type="email" name="email" placeholder="E-mail" required>
            </div>
            <div class="form-section">
                <input type="tel" name="telefone" placeholder="Telefone" required>
            </div>
            <div class="form-section">
                <input type="text" name="cidade" placeholder="Cidade" required>
            </div>
            <div class="form-section">
                <label class="section-title">Área de Investimento</label>
                <select name="area" required>
                    <option value="">Selecione a Área</option>
                    <option value="Imóvel">Imóvel</option>
                    <option value="Veículo">Veículo</option>
                    <option value="Construção">Construção</option>
                    <option value="Reforma">Reforma</option>
                    <option value="Loja/Ponto Comercial">Loja/Ponto Comercial</option>
                    <option value="Área Rural">Área Rural</option>
                </select>
            </div>
            <div class="form-section option-group">
                <div class="option">
                    <label class="section-title">Valor Desejado</label>
                    <select name="valor" required>
                        <option value="">Selecione o Valor</option>
                        <option value="100.000">R$ 100.000</option>
                        <option value="150.000">R$ 150.000</option>
                        <option value="200.000">R$ 200.000</option>
                        <option value="250.000">R$ 250.000</option>
                        <option value="300.000">R$ 300.000</option>
                        <option value="350.000">R$ 350.000</option>
                        <option value="500.000">R$ 500.000</option>
                        <option value="1.000.000">R$ 1.000.000</option>
                    </select>
                </div>
            </div>
            <button type="button" onclick="sendWhatsApp()">Solicitar Crédito via WhatsApp</button>
        </form>
    </div>

    <script>
        function sendWhatsApp() {
            const nome = document.querySelector('[name="nome"]').value;
            const email = document.querySelector('[name="email"]').value;
            const telefone = document.querySelector('[name="telefone"]').value;
            const cidade = document.querySelector('[name="cidade"]').value;
            const area = document.querySelector('[name="area"]').value;
            const valor = document.querySelector('[name="valor"]').value;

            const message = `Oi, tenho interesse em Crédito para Investimento.\n\n- Nome: ${nome}\n- E-mail: ${email}\n- Telefone: ${telefone}\n- Cidade: ${cidade}\n- Área de Investimento: ${area}\n- Valor Desejado: ${valor}`;
            const url = `https://wa.me/5598984699652?text=${encodeURIComponent(message)}`;
            window.open(url, "_blank");
        }
    </script>

</body>
</html>
-
