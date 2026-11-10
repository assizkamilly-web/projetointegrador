
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sensores de Luz e Radiação Solar</title>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    scroll-behavior: smooth;
}

body {
    font-family: 'Segoe UI', sans-serif;
    background: #f9f5ff;
    color: #45445a;
    line-height: 1.7;
}

header {
    background: linear-gradient(135deg, #d9eaff, #eadfff, #ffe2ec);
    text-align: center;
    padding: 65px 20px;
}

header h1 {
    font-size: 36px;
    color: #555477;
    margin-bottom: 15px;
}

header p {
    font-size: 17px;
    color: #68677e;
}

nav {
    background: #dcd5f5;
    padding: 15px;
    text-align: center;
    position: sticky;
    top: 0;
    z-index: 10;
}

nav a {
    color: #555477;
    text-decoration: none;
    margin: 10px;
    font-weight: bold;
}

nav a:hover {
    color: #b06e9e;
}

.container {
    max-width: 1050px;
    margin: auto;
    padding: 30px 20px;
}

section {
    background: white;
    padding: 30px;
    margin: 25px 0;
    border-radius: 20px;
    box-shadow: 0 5px 18px #dcd5e855;
}

h2 {
    color: #8d79b5;
    margin-bottom: 15px;
}

h3 {
    color: #b17eaa;
    margin: 15px 0 8px;
}

.cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 20px;
    margin-top: 20px;
}

.card {
    padding: 22px;
    border-radius: 16px;
    background: #e9f2ff;
}

.card:nth-child(2) {
    background: #f5e9ff;
}

.card:nth-child(3) {
    background: #e4f5eb;
}

.card h3 {
    margin-top: 0;
}

.icon {
    font-size: 35px;
    margin-bottom: 10px;
}

.highlight {
    background: #fff0f5;
    padding: 18px;
    border-left: 5px solid #e6a9c5;
    border-radius: 10px;
    margin-top: 15px;
}

.simulator {
    background: #edf3ff;
    padding: 25px;
    border-radius: 15px;
    margin-top: 20px;
    text-align: center;
}

input[type="range"] {
    width: 90%;
    margin: 20px;
    accent-color: #a58acb;
}

button {
    background: #c9b8eb;
    border: none;
    padding: 12px 22px;
    border-radius: 25px;
    color: #45445a;
    font-weight: bold;
    cursor: pointer;
    margin: 8px;
}

button:hover {
    background: #b5a0dc;
}

.resultado {
    font-size: 24px;
    color: #8067aa;
    font-weight: bold;
    margin-top: 15px;
}

.bar {
    height: 22px;
    border-radius: 20px;
    background: #ddd;
    margin: 12px 0;
    overflow: hidden;
}

.fill {
    height: 100%;
    width: 0%;
    background: linear-gradient(90deg, #a8d8c0, #a8b9ec);
    transition: width 0.4s;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 15px;
}

td, th {
    border: 1px solid #e4dced;
    padding: 12px;
    text-align: left;
}

th {
    background: #e9e2f8;
}

footer {
    background: #e5dcf5;
    text-align: center;
    padding: 25px;
    margin-top: 40px;
    color: #625c7d;
}

@media(max-width: 600px) {
    header h1 {
        font-size: 27px;
    }

    nav a {
        display: inline-block;
        font-size: 13px;
        margin: 5px;
    }

    section {
        padding: 20px;
    }
}
</style>
</head>

<body>

<header>
    <h1>☀️ Sensores de Luz e Radiação Solar</h1>
    <p>Entendendo como a luz solar pode ser medida e aproveitada.</p>
</header>

<nav>
    <a href="#introducao">Introdução</a>
    <a href="#sensores">Sensores</a>
    <a href="#intensidade">Intensidade</a>
    <a href="#coletor">Coletor Solar</a>
    <a href="#limitacoes">Limitações</a>
</nav>

<div class="container">

<section id="introducao">
    <h2>☀️ O que é radiação solar?</h2>

    <p>
        A radiação solar é a energia emitida pelo Sol na forma de
        ondas eletromagnéticas. Ela chega até a Terra e pode ser
        aproveitada para produzir eletricidade e calor.
    </p>

    <p>
        Os sensores de luz são dispositivos que detectam a presença
        e a intensidade da iluminação. Eles ajudam a acompanhar
        a quantidade de luz solar recebida em diferentes locais.
    </p>

    <div class="highlight">
        <strong>Você sabia?</strong>
        A posição do Sol muda durante o dia. Por isso, a intensidade
        da luz recebida por um painel solar também pode variar.
    </div>
</section>

<section id="sensores">
    <h2>🔬 Como funcionam os sensores?</h2>

    <div class="cards">

        <div class="card">
            <div class="icon">💡</div>
            <h3>LDR</h3>
            <p>
                O LDR é um resistor dependente de luz.
                Quando recebe mais iluminação, sua resistência elétrica
                geralmente diminui. Quando recebe menos luz,
                sua resistência aumenta.
            </p>
        </div>

        <div class="card">
            <div class="icon">📡</div>
            <h3>Fotodiodo</h3>
            <p>
                O fotodiodo transforma a luz recebida em uma corrente
                elétrica. Quanto maior a quantidade de luz,
                maior tende a ser a corrente produzida,
                dentro da faixa de funcionamento do sensor.
            </p>
        </div>

    </div>

    <div class="highlight">
        <strong>Diferença principal:</strong>
        O LDR varia sua resistência elétrica, enquanto o fotodiodo
        produz uma corrente elétrica relacionada à luz recebida.
    </div>
</section>

<section id="intensidade">
    <h2>📊 Como comparar a intensidade luminosa?</h2>

    <p>
        Podemos colocar sensores em diferentes posições e observar
        a quantidade de luz que cada um recebe.
        Assim, conseguimos identificar os locais mais iluminados.
    </p>

    <table>
        <tr>
            <th>Posição</th>
            <th>Iluminação</th>
            <th>Intensidade relativa</th>
        </tr>
        <tr>
            <td>Sol direto</td>
            <td>Alta</td>
            <td>100%</td>
        </tr>
        <tr>
            <td>Sombra parcial</td>
            <td>Média</td>
            <td>50%</td>
        </tr>
        <tr>
            <td>Ambiente fechado</td>
            <td>Baixa</td>
            <td>20%</td>
        </tr>
    </table>

    <p style="margin-top:15px">
        Os valores são exemplos ilustrativos, não medições reais.
    </p>
</section>

<section id="coletor">
    <h2>🌞 Simulador de intensidade solar</h2>

    <p>
        Movimente a barra para simular diferentes níveis de
        iluminação recebidos por um coletor solar.
    </p>

    <div class="simulator">

        <label for="luz">
            Intensidade da iluminação:
        </label>

        <input type="range" id="luz"
        min="0" max="100" value="50">

        <div class="resultado" id="valor">
            50%
        </div>

        <div class="bar">
            <div class="fill" id="barra"></div>
        </div>

        <h3 id="situacao">Iluminação moderada</h3>

        <p id="descricao">
            O coletor recebe uma quantidade intermediária de luz.
        </p>

    </div>

    <h3>Qual é o melhor posicionamento?</h3>

    <p>
        O melhor posicionamento para um coletor solar é aquele
        que permite receber a maior quantidade possível de
        radiação solar durante o período de utilização.
    </p>

    <p>
        Para descobrir esse local, podemos comparar medições
        feitas em diferentes ângulos e posições, durante
        vários horários do dia.
    </p>

    <div class="highlight">
        <strong>Conclusão:</strong>
        O posicionamento com maior incidência de radiação solar
        tende a favorecer o aproveitamento da energia solar.
    </div>
</section>

<section id="limitacoes">
    <h2>⚠️ Quais são as limitações dos sensores?</h2>

    <div class="cards">

        <div class="card">
            <h3>🌥️ Condições climáticas</h3>
            <p>
                Nuvens, chuva e neblina alteram a quantidade
                de radiação solar recebida.
            </p>
        </div>

        <div class="card">
            <h3>📏 Precisão</h3>
            <p>
                Sensores simples podem não fornecer medições
                muito precisas e precisam de calibração.
            </p>
        </div>

        <div class="card">
            <h3>🌈 Tipo de luz</h3>
            <p>
                Alguns sensores respondem melhor a determinadas
                faixas do espectro eletromagnético.
            </p>
        </div>

        <div class="card">
            <h3>🌡️ Temperatura</h3>
            <p>
                A temperatura pode alterar o funcionamento
                e as medições de alguns sensores.
            </p>
        </div>

    </div>

    <div class="highlight">
        <strong>Importante:</strong>
        Medir a intensidade da luz não é o mesmo que medir
        diretamente a energia solar recebida.
        Para medir a irradiância solar com precisão, é indicado
        utilizar instrumentos apropriados, como um piranômetro.
    </div>
</section>

<section>
    <h2>📚 Conclusão</h2>

    <p>
        Os sensores LDR e fotodiodos permitem acompanhar a
        iluminação e comparar diferentes posições em relação
        à incidência solar. Com essas informações, podemos
        investigar qual é o melhor posicionamento para um
        coletor solar.
    </p>

    <p>
        Entretanto, é importante considerar as limitações
        dos sensores e lembrar que a medição da luz não
        representa necessariamente toda a energia solar
        disponível.
    </p>

    <div class="highlight">
        <strong>Objetivo alcançado:</strong>
        Com o uso de sensores, podemos compreender melhor
        a radiação solar e como aproveitá-la de maneira eficiente.
    </div>
</section>

</div>

<footer>
    ☀️ Projeto de Ciências e Tecnologia
    <p>Sensores de Luz e Acompanhamento da Radiação Solar</p>
</footer>

<script>
const luz = document.getElementById("luz");
const valor = document.getElementById("valor");
const barra = document.getElementById("barra");
const situacao = document.getElementById("situacao");
const descricao = document.getElementById("descricao");

function atualizarSimulador() {

    let intensidade = Number(luz.value);

    valor.textContent = intensidade + "%";
    barra.style.width = intensidade + "%";

    if (intensidade >= 70) {
        situacao.textContent = "☀️ Iluminação alta";
        descricao.textContent =
        "O coletor recebe bastante luz solar e apresenta maior potencial de aproveitamento.";
    }

    else if (intensidade >= 30) {
        situacao.textContent = "🌤️ Iluminação moderada";
        descricao.textContent =
        "O coletor recebe uma quantidade intermediária de luz.";
    }

    else {
        situacao.textContent = "☁️ Iluminação baixa";
        descricao.textContent =
        "O coletor recebe pouca luz e pode apresentar menor aproveitamento solar.";
    }
}

luz.addEventListener("input", atualizarSimulador);

atualizarSimulador();
</script>

</body>
</html>
