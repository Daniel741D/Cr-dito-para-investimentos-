
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Crédito para Investimento</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: url('https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTaNxe4-U4K6IoRpn3suhzqypIjc8LYXsom8xhF7uKM2JRfmKtlYK4nRgtU&s=10') no-repeat center center fixed;
            background-size: cover;
            text-align: center;
            padding: 20px;
            margin: 0;
        }
        .container {
            background: rgba(255, 255, 255, 0.9);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
            max-width: 500px;
            margin: auto;
        }
        label {
            font-weight: bold;
            display: block;
            margin-top: 10px;
        }
        select, input {
            width: 100%;
            padding: 10px;
            margin-top: 5px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 16px;
        }
        button {
            background-color: #28a745;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 15px;
            width: 100%;
            font-size: 18px;
        }
        button:hover {
            background-color: #218838;
        }
        @media (max-width: 600px) {
            .container {
                width: 90%;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Crédito para Investimento</h2>
        <form id="creditoForm">
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
                <option value="">Selecione o valor do investimento primeiro</option>
            </select>
            
            <button type="button" onclick="enviarWhatsApp()">Solicitar Crédito via WhatsApp</button>
        </form>
    </div>

    <script>
        function atualizarParcelas() {
            var valor = document.getElementById("valor").value;
            var parcela = document.getElementById("parcela");
            parcela.innerHTML = "";

            var opcoesParcelas = {
                "100000": [590, 690, 800, 900, 1000],
                "150000": [890, 950, 1200, 1500, 1900],
                "250000": [1500, 2000, 2500, 3000, 3500],
                "350000": [2000, 2500, 3000, 3500, 4000],
                "500000": [3000, 4000, 5000, 6000, 7000],
                "750000": [5000, 6000, 7000, 8000, 9000],
                "1000000": [7000, 10000, 15000, 20000, 25000]
            };

            if (valor in opcoesParcelas) {
                opcoesParcelas[valor].forEach(function(p) {
                    var option = document.createElement("option");
                    option.value = p;
                    option.text = "R$ " + p.toLocaleString();
                    parcela.appendChild(option);
                });
            } else {
                var option = document.createElement("option");
                option.value = "";
                option.text = "Selecione um valor válido";
                parcela.appendChild(option);
            }
        }

        function enviarWhatsApp() {
            var nome = document.getElementById("nome").value.trim();
            var email = document.getElementById("email").value.trim();
            var telefone = document.getElementById("telefone").value.trim();
            var cidade = document.getElementById("cidade").value.trim();
            var investimento = document.getElementById("investimento").value;
            var valor = document.getElementById("valor").value;
            var parcela = document.getElementById("parcela").value;

            if (!nome || !email || !telefone || !cidade || !investimento || !valor || !parcela) {
                alert("Por favor, preencha todos os campos antes de enviar.");
                return;
            }

            var mensagem = `Oi, meu nome é *${nome}*.  
Tenho interesse em pegar um crédito para investimento.  

📍 *Cidade:* ${cidade}  
📩 *E-mail:* ${email}  
📞 *Telefone:* ${telefone}  
🏡 *Área de Investimento:* ${investimento}  
💰 *Valor do Investimento:* R$ ${parseInt(valor).toLocaleString('pt-BR')}  
💳 *Valor da Parcela:* R$ ${parseInt(parcela).toLocaleString('pt-BR')}`;

            var url = `https://api.whatsapp.com/send?phone=5598981925728&text=${encodeURIComponent(mensagem)}`;
            window.open(url, "_blank");
        }
    </script>
</body>
</html>
