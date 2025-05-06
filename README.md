!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ju Mini Pizzas</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Pacifico&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(180deg, #ffffff, #f8f8f8);
            margin: 0;
            padding: 0;
            color: #333;
        }

        .container {
            max-width: 650px;
            margin: 70px auto;
            background: #fff;
            border-radius: 18px;
            padding: 50px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            text-align: center;
        }

        h1 {
            font-family: 'Pacifico', cursive;
            font-size: 3em;
            color: #e67e22;
            text-shadow: 2px 2px 5px rgba(0,0,0,0.1);
        }

        label {
            display: block;
            margin-top: 25px;
            font-weight: 700;
            color: #555;
            font-size: 1.2em;
        }

        input {
            width: 100%;
            padding: 14px;
            margin-top: 12px;
            border-radius: 10px;
            border: 1px solid #ddd;
            font-size: 1em;
            transition: 0.3s;
        }

        input:focus {
            outline: none;
            border-color: #e67e22;
            box-shadow: 0 0 8px rgba(230, 126, 34, 0.3);
        }

        .sabores-lista {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
            gap: 15px;
            margin-top: 25px;
        }

        .sabor {
            background: #fff;
            padding: 18px;
            text-align: center;
            border: 2px solid #eee;
            border-radius: 14px;
            font-weight: 600;
            font-size: 1.1em;
            color: #555;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
            cursor: pointer;
            transition: 0.3s ease;
        }

        .sabor:hover {
            border-color: #e67e22;
            transform: translateY(-3px);
            background: #fff7e6;
        }

        .preco {
            margin-top: 35px;
            font-size: 1.4em;
            font-weight: 700;
            color: #e67e22;
        }

        .informacao-entrega {
            text-align: center;
            color: #777;
            font-size: 1.1em;
            margin-top: 18px;
            line-height: 1.6;
        }

        button {
            width: 100%;
            padding: 16px;
            background: #2ecc71;
            color: white;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            border: none;
            border-radius: 10px;
            transition: 0.3s;
        }

        button:hover {
            background: #27ae60;
            transform: translateY(-3px);
        }

        .instagram-fixed {
            position: fixed;
            bottom: 25px;
            right: 25px;
        }

        .instagram-button {
            background: #e1306c;
            color: white;
            padding: 14px 22px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }

        .instagram-button:hover {
            transform: scale(1.05);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🍕 Ju Mini Pizzas</h1>
        <form id="pedidoForm">
            <label for="nome">Seu nome:</label>
            <input type="text" id="nome" required>

            <label for="endereco">Endereço de entrega:</label>
            <input type="text" id="endereco" required>

            <label>Escolha 10 sabores (pode repetir):</label>
            <div class="sabores-lista">
                <div class="sabor" data-sabor="Calabresa">Calabresa</div>
                <div class="sabor" data-sabor="Portuguesa">Portuguesa</div>
                <div class="sabor" data-sabor="Mussarela">Mussarela</div>
                <div class="sabor" data-sabor="Frango">Frango</div>
                <div class="sabor" data-sabor="Frango com Catupiry">Frango com Catupiry</div>
                <div class="sabor" data-sabor="Bacon">Bacon</div>
            </div>

            <div class="preco">Preço: R$50,00 (10 mini pizzas)</div>
            <div class="informacao-entrega">
                📍 Entrega das **10:00 às 18:00**  
                🚚 Taxa mínima de **R$5,00** conforme a região
            </div>

            <button type="submit">Fazer Pedido via WhatsApp</button>
        </form>
    </div>

    <div class="instagram-fixed">
        <a href="https://www.instagram.com/ju.meire34/" target="_blank" class="instagram-button">Siga @ju.meire34</a>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const sabores = document.querySelectorAll('.sabor');
            let selecionados = [];
            const limite = 10;

            sabores.forEach(sabor => {
                sabor.addEventListener('click', () => {
                    if (selecionados.length < limite) {
                        selecionados.push(sabor.getAttribute('data-sabor'));
                    } else {
                        alert("Você só pode escolher até 10 sabores!");
                    }
                });
            });

            document.getElementById('pedidoForm').addEventListener('submit', e => {
                e.preventDefault();
                const nome = document.getElementById('nome').value;
                const endereco = document.getElementById('endereco').value;

                if (selecionados.length === 0) {
                    alert("Por favor, escolha ao menos um sabor!");
                    return;
                }

                const url = `https://wa.me/+556186515632?text=Pedido%20de%20${encodeURIComponent(nome)},%20Endereço:%20${encodeURIComponent(endereco)},%20Sabores:%20${encodeURIComponent(selecionados.join(', '))}`;
                window.open(url, '_blank');
            });
        });

        
    </script>
</body>
</html>
