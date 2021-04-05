# aula-9-alura-Super-Trunfo-
 Super Trunfo 
https://codepen.io/chritianegozza/pen/dyNRvmq?editors=0110

![image](https://user-images.githubusercontent.com/72118415/113537099-1723c380-95ae-11eb-8883-4c5d4085cf0d.png)



HTML

<html>

<head>
    <title>
        Imersão Dev - Aula 09
    </title>
</head>

<body>
    <div class="container">
        <img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/logo-imersao-super-trunfo.png" class="page-logo"
            alt="">
        <h1 class="page-title">Super Trunfo</h1>

        <button onclick="sortearCarta()" id="btnSortear">Sortear carta</button>

        <form id="form">
            <h2>Escolha o seu atributo</h2>
            <div class="wrapper">
                <div id="placar"></div>
                <div id="quantidade-cartas"></div>
                <div id="cartas">
                    <div id="carta-jogador" class="carta"></div>
                    <div id="carta-maquina" class="carta"></div>
                </div>
                <button class="button-jogar" type="button" id="btnJogar" onclick="jogar()"
                    disabled="false">Jogar</button>
            </div>
            <div id="resultado"></div>
            <button type="button" id="btnProximaRodada" onclick="proximaRodada()" disabled="true">Proxima
                rodada</button>
        </form>
    </div>
</body>

</html>



CSS

body {
    font-family: 'Roboto Mono', monospace;
    min-height: 280px;
    background-image: url('https://aventurasnahistoria.uol.com.br/media/_versions/capa_avengers_end_game_widelg.png');
    background-color: #000000;
    background-size: cover;
    background-position: center top;
    background-repeat: no-repeat;
    padding-bottom: 20vh;
}

.container {
    text-align: center;
    padding: 20px;
}

.page-title {
    color: #ffffff;
    margin: 5px 0;
}

button {
    width: 10rem;
    max-width: 10rem;
    padding: .8rem 1.5rem;
    margin: 2rem auto;
    border-radius: 5px;
    border: none;
    font-size: 1rem;
}

h2 {
    color: white;
}

#carta-jogador, #carta-maquina {
    width: 360px;
    height: 500px;
    overflow: auto;
    border-radius: 10px;
    margin-bottom: 20px;
    margin: 0 auto;
    display: flex;
    align-items: flex-end;
    position: relative;
    background-size: 350px 300px;
    background-repeat: no-repeat;
    background-position-x: 10px;
    background-position-y: 5px;
    border-radius: 33px;
}

#carta-jogador h3 {
    text-align: center;
}

.carta-imagem {
    border: 1px solid black;
    height: 100px;
    margin: 10px;
}

.carta-imagem img {
    width: 100%;
    height: 100%;
}

.carta-status {
    height: 160px;
    margin: 2rem;
    color: white;
    z-index: 2;
}

.carta-status input {
    margin: 20px 10px;
}

.carta-status p {
    margin-bottom: 2rem;
}

.resultado-final {
    color: white;
    font-size: 2rem;
    text-transform: uppercase;
    font-weigth: bolder;
    padding: 1rem;
    border: 2px solid black;
    background-color: black;
}

.--spacing {
    margin-left: 2.5rem;
}

form {
    display: flex;
    flex-direction: column;
}

.wrapper {
    display: flex;
    flex-direction: column;
}

.carta-subtitle {
    z-index: 2;
    position: absolute;
    top: 16px;
    left: 37px;
    font-weight: 800;
    text-transform: uppercase;
}

#cartas {
    width: 100%;
    display: flex;
    justify-content: space-between;
}

#placar, #quantidade-cartas {
    color: white;
}




js

var cartaChristiane = {
  nome: "Thor",
  imagem:"https://cdn.ome.lt/pfIcbIk870YITAzNsEQ2Tx8kdlA=/1200x630/smart/extras/conteudos/thor-love-5.jpg",
  atributos:{ 
  ataque:80,
  defesa:60,
  magia:90
  }
}

var cartaArthur = {
  nome: "Homem Aranha",
  imagem:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTPOZ3Jd6cPfwq-kv9jnB8LEg95WhRHDVtcgg&usqp=CAU",
  atributos: {
  ataque:80, 
  defesa:65,
  magia:60
}
   }

var cartaAlex = {
  nome: "Homem de Ferro",
  imagem:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSGKJaG94gKfqvjaeYebES0loDS_uImMaru1Q&usqp=CAU",
   atributos: {
  ataque:90, 
  defesa:65,
  magia:68
}
   }

var cartaIsabella = {
  nome: "Viuva negra",
  imagem:"https://files.nsctotal.com.br/s3fs-public/styles/itapema_blog_post_header/public/2019-07/VN003.jpg?2u4baFQ6jFSzBsibg3hCB5Ce3us8vNbK&itok=8Ie-DBXO",
  atributos:{ 
  ataque:88,
  defesa:70,
  magia:90
  }
}

var cartaYasmin = {
  nome: "capitã Marvel",
  imagem:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQGO-NcF2g0EKppmElNs4Exrsg4JOLmmxKTdw&usqp=CAU",
  atributos: {
  ataque:88, 
  defesa:75,
  magia:80
}
   }

var cartaMarcela = {
  nome: "Feiticeira Escarlate",
  imagem:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQS3cPMwzgeB3j_66vFOcf4BWKQxV6YWIW2cg&usqp=CAU",
  atributos: {
  ataque:90, 
  defesa:80,
  magia:90
}
   }

var cartaRosana = {
    nome: "Hulk",
    imagem: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQzcvu6kdrV-Pp81CZ_113v2J83RjiPDmHVXg&usqp=CAU",
    atributos: {
        ataque: 95,
        defesa: 70,
        magia: 0
    }
}

var cartaLucas = {
    nome: "Dr EStranho",
    imagem: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS5jnWN7BtCYecm2HjtgIsCMbcI4jkg5xhHVw&usqp=CAU",
    atributos: {
        ataque: 90,
        defesa: 80,
        magia: 100
    }
}

var cartaMaquina 
var cartaJogador 
var cartas = [cartaChristiane, cartaArthur, cartaAlex, cartaIsabella, cartaYasmin, cartaMarcela, cartaRosana, cartaLucas]
              // 0              1             2            3             4               5           6           7            

var pontosJogador = 0
var pontosMaquina = 0

atualizaPlacar()
atualizaQuantidadeDeCartas()

function atualizaQuantidadeDeCartas() {
    var divQuantidadeCartas = document.getElementById('quantidade-cartas')
    var html = "Quantidade de cartas no jogo: " + cartas.length

    divQuantidadeCartas.innerHTML = html
}

function atualizaPlacar() {
    var divPlacar = document.getElementById('placar')
    var html = "Jogador " + pontosJogador + "/" + pontosMaquina + " Máquina"

    divPlacar.innerHTML = html
}

function sortearCarta() {
    var numeroCartaMaquina = parseInt(Math.random() * cartas.length)
    cartaMaquina = cartas[numeroCartaMaquina]
    cartas.splice(numeroCartaMaquina, 1)

    var numeroCartaJogador = parseInt(Math.random() * cartas.length)
    cartaJogador = cartas[numeroCartaJogador]
    cartas.splice(numeroCartaJogador, 1)

    document.getElementById('btnSortear').disabled = true
    document.getElementById('btnJogar').disabled = false

    exibeCartaJogador()
}

function exibeCartaJogador() {
    var divCartaJogador = document.getElementById("carta-jogador")
    var moldura = '<img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent.png" style=" width: inherit; height: inherit; position: absolute;">';
    divCartaJogador.style.backgroundImage = `url(${cartaJogador.imagem})`
    var nome = `<p class="carta-subtitle">${cartaJogador.nome}</p>`
    var opcoesTexto = ""

    for (var atributo in cartaJogador.atributos) {
        opcoesTexto += "<input type='radio' name='atributo' value='" + atributo + "'>" + atributo + " " + cartaJogador.atributos[atributo] + "<br>"
    }

    var html = "<div id='opcoes' class='carta-status'>"

    divCartaJogador.innerHTML = moldura + nome + html + opcoesTexto + '</div>'
}

function obtemAtributoSelecionado() {
    var radioAtributo = document.getElementsByName('atributo')
    for (var i = 0; i < radioAtributo.length; i++) {
        if (radioAtributo[i].checked) {
            return radioAtributo[i].value
        }
    }
}

function jogar() {
    var divResultado = document.getElementById("resultado")
    var atributoSelecionado = obtemAtributoSelecionado()

    if (cartaJogador.atributos[atributoSelecionado] > cartaMaquina.atributos[atributoSelecionado]) {
        htmlResultado = '<p class="resultado-final">Venceu</p>'
        pontosJogador++
    } else if (cartaJogador.atributos[atributoSelecionado] < cartaMaquina.atributos[atributoSelecionado]) {
        htmlResultado = '<p class="resultado-final">Perdeu</p>'
        pontosMaquina++
    } else {
        htmlResultado = '<p class="resultado-final">Empatou</p>'
    }

    if (cartas.length == 0) {
        alert("Fim de jogo")
        if (pontosJogador > pontosMaquina) {
            htmlResultado = '<p class="resultado-final">Venceu</p>'
        } else if (pontosMaquina > pontosJogador) {
            htmlResultado = '<p class="resultado-final">Perdeu</p>'
        } else {
            htmlResultado = '<p class="resultado-final">Empatou</p>'
        }
    } else {
        document.getElementById('btnProximaRodada').disabled = false
    }

    divResultado.innerHTML = htmlResultado
    document.getElementById('btnJogar').disabled = true

    atualizaPlacar()
    exibeCartaMaquina()
    atualizaQuantidadeDeCartas()
}

function exibeCartaMaquina() {
    var divCartaMaquina = document.getElementById("carta-maquina")
    var moldura = '<img src="https://www.alura.com.br/assets/img/imersoes/dev-2021/card-super-trunfo-transparent.png" style=" width: inherit; height: inherit; position: absolute;">';
    divCartaMaquina.style.backgroundImage = `url(${cartaMaquina.imagem})`
    var nome = `<p class="carta-subtitle">${cartaMaquina.nome}</p>`
    var opcoesTexto = ""

    for (var atributo in cartaMaquina.atributos) {
        console.log(atributo)
        opcoesTexto += "<p type='text' name='atributo' value='" + atributo + "'>" + atributo + " " + cartaMaquina.atributos[atributo] + "<br>"
    }

    var html = "<div id='opcoes' class='carta-status --spacing'>"

    divCartaMaquina.innerHTML = moldura + nome + html + opcoesTexto + '</div>'
}

function proximaRodada() {
    var divCartas = document.getElementById('cartas')

    divCartas.innerHTML = `<div id="carta-jogador" class="carta"></div> <div id="carta-maquina" class="carta"></div>`

    document.getElementById('btnSortear').disabled = false
    document.getElementById('btnJogar').disabled = true
    document.getElementById('btnProximaRodada').disabled = true

    var divResultado = document.getElementById('resultado')
    divResultado.innerHTML = ""
}
