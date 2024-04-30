# Desenvolvendo-um-Jogo-da-Mem-ria

Vou detalhar o desenvolvimento de um Jogo da Memória em módulos, explicando cada parte do processo:

### Módulo 1: Estrutura Básica
**HTML (HyperText Markup Language)**
- **Estrutura**: Crie um arquivo `index.html` e estruture o jogo com `<div>` para cartas, `<section>` para o tabuleiro do jogo, e `<button>` para iniciar o jogo.
- **Semântica**: Use elementos semânticos para melhor acessibilidade e SEO.

**CSS (Cascading Style Sheets)**
- **Layout**: Utilize Flexbox ou Grid para organizar as cartas.
- **Estilos**: Adicione cores, bordas e sombras para tornar as cartas visíveis e atraentes.

**JavaScript**
- **Inicialização**: Crie um script `game.js` para iniciar o jogo e definir variáveis globais.

### Módulo 2: Lógica do Jogo
- **Embaralhar Cartas**: Implemente uma função para embaralhar as cartas usando o algoritmo Fisher-Yates.
- **Virar Carta**: Adicione um evento de clique para virar a carta e mostre o verso dela.
- **Verificar Par**: Crie uma função para verificar se duas cartas viradas são um par.

### Módulo 3: Efeitos 3D no CSS
- **Perspectiva**: Use a propriedade `perspective` para dar profundidade ao tabuleiro.
- **Transformação**: Aplique `transform: rotateY(180deg)` para virar as cartas.

### Módulo 4: Condicionais e IIFE
- **Condicionais**: Use `if` para verificar condições como fim do jogo ou correspondência de cartas.
- **IIFE (Immediately Invoked Function Expression)**: Encapsule o código de inicialização em uma IIFE para evitar poluir o escopo global.

### Módulo 5: Manipulação de Array
- **Array de Cartas**: Crie um array para armazenar objetos de cartas com propriedades como `id`, `imagem`, e `virada`.
- **Métodos de Array**: Use métodos como `map`, `filter`, e `forEach` para manipular o array de cartas.

### Exemplo Prático: Inicialização do Jogo
```javascript
(function() {
  let cartas = [];
  // Código para criar cartas e adicionar ao array
  // Código para embaralhar cartas
  // Código para adicionar evento de clique nas cartas
})();
```

Este é um esboço geral de como você pode dividir e organizar o seu projeto de Jogo da Memória. Lembre-se de testar cada módulo individualmente antes de prosseguir para o próximo. 

Aqui estão mais alguns exemplos práticos para cada módulo do seu Jogo da Memória:

### Módulo 1: Estrutura Básica
**HTML**
```html
<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <title>Jogo da Memória</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <section class="tabuleiro">
        <!-- Cartas serão inseridas aqui -->
    </section>
    <button id="iniciar-jogo">Iniciar Jogo</button>
    <script src="game.js"></script>
</body>
</html>
```

**CSS**
```css
.tabuleiro {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    perspective: 1000px;
}

.carta {
    width: 100px;
    height: 150px;
    margin: 10px;
    border: 1px solid #ccc;
    box-shadow: 3px 3px 5px rgba(0,0,0,0.3);
    cursor: pointer;
    transform-style: preserve-3d;
    transition: transform 0.5s;
}

.carta.virada {
    transform: rotateY(180deg);
}
```

**JavaScript**
```javascript
document.getElementById('iniciar-jogo').addEventListener('click', iniciarJogo);

function iniciarJogo() {
    // Código para iniciar o jogo
}
```

### Módulo 2: Lógica do Jogo
**JavaScript**
```javascript
function embaralharCartas(cartas) {
    for (let i = cartas.length - 1; i > 0; i--) {
        let j = Math.floor(Math.random() * (i + 1));
        [cartas[i], cartas[j]] = [cartas[j], cartas[i]];
    }
}

function virarCarta(carta) {
    carta.classList.add('virada');
    // Código para verificar se formou um par
}

function verificarPar(carta1, carta2) {
    if (carta1.dataset.imagem === carta2.dataset.imagem) {
        // É um par!
    } else {
        // Não é um par, desvirar as cartas
    }
}
```

### Módulo 3: Efeitos 3D no CSS
**CSS**
```css
.carta .frente, .carta .verso {
    position: absolute;
    backface-visibility: hidden;
}

.carta .verso {
    transform: rotateY(180deg);
}
```

### Módulo 4: Condicionais e IIFE
**JavaScript**
```javascript
(function() {
    const cartas = [];
    // Código para criar cartas e adicionar ao array
    embaralharCartas(cartas);
    // Código para adicionar evento de clique nas cartas
})();
```

### Módulo 5: Manipulação de Array
**JavaScript**
```javascript
let cartas = [
    { id: 1, imagem: 'imagem1.png', virada: false },
    { id: 2, imagem: 'imagem2.png', virada: false },
    // Adicione todas as cartas
];

cartas.forEach(carta => {
    // Código para criar elemento da carta e adicionar ao tabuleiro
});
```

Esses exemplos devem ajudá-lo a começar a codificar cada parte do seu jogo. Lembre-se de adaptar o código conforme necessário para atender às especificidades do seu projeto.
