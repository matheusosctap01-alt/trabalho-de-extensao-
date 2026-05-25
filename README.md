# trabalho-de-extensao-
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sistema para Pequenos Negócios</title>

<style>
    body{
        font-family: Arial, sans-serif;
        background:#f4f4f4;
        margin:0;
        padding:20px;
    }

    .container{
        max-width:700px;
        margin:auto;
        background:white;
        padding:20px;
        border-radius:10px;
        box-shadow:0 0 10px rgba(0,0,0,0.1);
    }

    h1{
        text-align:center;
        color:#333;
    }

    input{
        width:100%;
        padding:10px;
        margin:8px 0;
        border:1px solid #ccc;
        border-radius:5px;
    }

    button{
        width:100%;
        padding:10px;
        background:#007bff;
        color:white;
        border:none;
        border-radius:5px;
        cursor:pointer;
        font-size:16px;
    }

    button:hover{
        background:#0056b3;
    }

    table{
        width:100%;
        margin-top:20px;
        border-collapse:collapse;
    }

    table, th, td{
        border:1px solid #ddd;
    }

    th{
        background:#007bff;
        color:white;
    }

    th, td{
        padding:10px;
        text-align:center;
    }

    .delete-btn{
        background:red;
        padding:5px 10px;
        border:none;
        color:white;
        border-radius:5px;
        cursor:pointer;
    }
</style>
</head>

<body>

<div class="container">

    <h1>Sistema para Pequenos Negócios</h1>

    <input type="text" id="nome" placeholder="Nome do cliente">
    <input type="text" id="telefone" placeholder="Telefone">
    <input type="text" id="produto" placeholder="Produto comprado">

    <button onclick="adicionarCliente()">Cadastrar Cliente</button>

    <table>
        <thead>
            <tr>
                <th>Nome</th>
                <th>Telefone</th>
                <th>Produto</th>
                <th>Ação</th>
            </tr>
        </thead>

        <tbody id="tabelaClientes">

        </tbody>
    </table>

</div>

<script>

let clientes = [];

function adicionarCliente(){

    let nome = document.getElementById("nome").value;
    let telefone = document.getElementById("telefone").value;
    let produto = document.getElementById("produto").value;

    if(nome === "" || telefone === "" || produto === ""){
        alert("Preencha todos os campos!");
        return;
    }

    let cliente = {
        nome,
        telefone,
        produto
    };

    clientes.push(cliente);

    atualizarTabela();

    document.getElementById("nome").value = "";
    document.getElementById("telefone").value = "";
    document.getElementById("produto").value = "";
}

function atualizarTabela(){

    let tabela = document.getElementById("tabelaClientes");

    tabela.innerHTML = "";

    clientes.forEach((cliente, index) => {

        tabela.innerHTML += `
            <tr>
                <td>${cliente.nome}</td>
                <td>${cliente.telefone}</td>
                <td>${cliente.produto}</td>
                <td>
                    <button class="delete-btn" onclick="removerCliente(${index})">
                        Excluir
                    </button>
                </td>
            </tr>
        `;
    });
}

function removerCliente(index){
    clientes.splice(index,1);
    atualizarTabela();
}

</script>

</body>
</html> 
