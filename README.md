<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Crédito para Investimento</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 20px;
            margin: 0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 90%;
            width: 400px;
            margin: auto;
        }
        .logo {
            width: 100%;
            max-width: 250px;
            margin-bottom: 20px;
        }
        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
            text-align: left;
        }
        select, input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #28a745;
            color: white;
            padding: 12px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 15px;
            width: 100%;
            font-size: 16px;
        }
        button:hover {
            background-color: #218838;
        }
    </style>
</head>
<body>
    <div class="container">
        <img src="https://www.mediafire.com/view/s7272qwig8gnp8h/20250319_122205.png/file" class="logo" alt="Rod Lider Logo">
        <h2>Crédito para Investimento</h2>
        <form onsubmit="enviarWhatsApp(event)">
            <label for="nome">Seu Nome</label>
            <input type="text" id="nome" name="nome" required>
            
            <label for="email">Seu E-mail</label>
            <input type="email" id="email" name="email" required>
            
            <label for="telefone">Seu Telefone</label>
            <input type="tel" id="telefone" name="telefone" required>
            
            <label for="cidade">Cidade</label>
            <input type="text" id="cidade" name="cidade" required>
            
            <label for="investimento">Área de Investimento</label>
            <select id="investimento" name="investimento">
                <option value="Área Rural">Área Rural</option>
                <option value="Veículo">Veículo</option>
                <option value="Imóvel">Imóvel</option>
                <option value="Construção">Construção</option>
                <option value="Reforma">Reforma</option>
                <option value="Loja/Ponto Comercial">Loja/Ponto Comercial</option>
            </select>
            
            <label for="valor">Valor do Investimento</label>
            <select id="valor" name="valor" onchange="atualizarParcelas()">
                <option value="100000">R$ 100.000</option>
                <option value="150000">R$ 150.000</option>
                <option value="250000">R$ 250.000</option>
                <option value="350000">R$ 350.000</option>
                <option value="500000">R$ 500.000</option>
                <option value="750000">R$ 750.000</option>
                <option value="1000000">R$ 1.000.000</option>
            </select>
            
            <label for="parcela">Valor da Parcela</label>
            <select id="parcela" name="parcela">
                <option value="">Selecione um valor de investimento primeiro</option>
            </select>
            
            <button type="submit">Tenho interesse!</button>
        </form>
    </div>

    <script>
        function atualizarParcelas() {
            var valorInvestimento = document.getElementById("valor").value;
            var parcelaSelect = document.getElementById("parcela");
            parcelaSelect.innerHTML = ""; // Limpa as opções anteriores

            var opcoesParcelas = {
                "100000": [590, 650, 700, 890, 950, 1000],
                "150000": [800, 900, 1000, 1200, 1500],
                "250000": [1500, 1900, 2000, 2500, 3000],
                "350000": [2500, 3000, 3500, 4000, 4500],
                "500000": [4000, 5000, 6000, 7000, 8000],
                "750000": [7000, 9000, 10000, 12000, 15000],
                "1000000": [12000, 15000, 20000, 30000, 50000]
            };

            if (opcoesParcelas[valorInvestimento]) {
                opcoesParcelas[valorInvestimento].forEach(function(valor) {
                    var option = document.createElement("option");
                    option.value = valor;
                    option.textContent = "R$ " + valor.toLocaleString('pt-BR');
                    parcelaSelect.appendChild(option);
                });
            } else {
                var option = document.createElement("option");
                option.textContent = "Selecione um valor de investimento primeiro";
                parcelaSelect.appendChild(option);
            }
        }

        function enviarWhatsApp(event) {
            event.preventDefault();

            var nome = document.getElementById("nome").value;
            var email = document.getElementById("email").value;
            var telefone = document.getElementById("telefone").value;
            var cidade = document.getElementById("cidade").value;
            var investimento = document.getElementById("investimento").value;
            var valor = document.getElementById("valor").value;
            var parcela = document.getElementById("parcela").value;

            var mensagem = `Oi, meu nome é *${nome}*. 
Tenho interesse em pegar um crédito para investimento.

📍 *Cidade:* ${cidade}  
📩 *E-mail:* ${email}  
📞 *Telefone:* ${telefone}  
🏡 *Área de Investimento:* ${investimento}  
💰 *Valor do Investimento:* R$ ${parseInt(valor).toLocaleString('pt-BR')}  
💳 *Valor da Parcela:* R$ ${parseInt(parcela).toLocaleString('pt-BR')}`;

            var url = `https://api.whatsapp.com/send?phone=5598984699652&text=${encodeURIComponent(mensagem)}`;
            
            window.open(url, "_blank");
        }
    </script>

</body>
</html>
