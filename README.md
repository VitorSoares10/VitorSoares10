<!DOCTYPE html>
<html>
<head>
    <title>Lista de Compras</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
        }
        h1 {
            text-align: center;
        }
        #lista {
            list-style-type: none;
            padding: 0;
        }
        #lista li {
            margin-bottom: 5px;
        }
        input[type="text"],
        input[type="number"],
        button {
            margin-bottom: 10px;
        }
        button {
            padding: 8px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>Minha Lista de Compras</h1>
    <ul id="lista"></ul>

    <label for="item">Novo item:</label>
    <input type="text" id="item">
    <label for="preco">Preço:</label>
    <input type="number" id="preco">
    <button onclick="adicionarItem()">Adicionar</button>

    <p>Total: R$<span id="total">0.00</span></p>

    <script>
        let total = 0;

        function adicionarItem() {
            const item = document.getElementById("item").value;
            const preco = parseFloat(document.getElementById("preco").value);
            
            if (item !== "" && !isNaN(preco)) {
                const lista = document.getElementById("lista");
                const novoItem = document.createElement("li");
                novoItem.textContent = item + " - R$" + preco.toFixed(2);
                lista.appendChild(novoItem);

                total += preco;
                document.getElementById("total").textContent = total.toFixed(2);
            }

            // Limpa os campos após adicionar o item
            document.getElementById("item").value = "";
            document.getElementById("preco").value = "";
        }
    </script>
</body>
</html>
