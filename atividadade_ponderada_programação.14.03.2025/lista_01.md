# Respostas e Justificativas - Exercícios de JavaScript

## 1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.

```javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```

**Alternativa correta:**
**a) A saída será `undefined` seguido de erro.**

**Justificativa:**
O `var` sofre hoisting, ou seja, é elevada ao topo do escopo com valor `undefined`, permitindo o primeiro `console.log(x)`, e o `let`, por outro lado, não é inicializado antes da execução, resultando em um erro ao acessar `y` antes da sua declaração.

---

## 2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema.

```javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```

**Alternativa correta:**
**a) Substituir `if (a || b === 0)` por `if (a === 0 || b === 0)`.**

**Justificativa:**
O `if (a || b === 0) é incorreto`, pois `a` sozinho pode ser qualquer valor não `0` e ainda tornar a condição verdadeira. A condição correta seria `if (a === 0 || b === 0)`, garantindo que qualquer um dos dois seja exatamente zero antes de retornar o erro.

---

## 3) Ao executar esse código, qual será a saída no console?

```javascript
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}
console.log(calcularPreco("eletrônico"));
```

**Alternativa correta:**
**b) O código imprime `200`.**

**Justificativa:**
Falta um `break` após `preco = 1000`, fazendo com que o código continue para `case "vestuário"`, onde `preco = 200`. O `break` só ocorre após `vestuário`, então o retorno final é `200`.

---

## 4) Qual será a saída no console?

```javascript
let numeros = [1, 2, 3, 4, 5];
let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);
console.log(resultado);
```

**Alternativa correta:**
**c) `18`**

**Justificativa:**
1. `map(x => x * 2)` → `[2, 4, 6, 8, 10]`
2. `filter(x => x > 5)` → `[6, 8, 10]`
3. `reduce((a, b) => a + b, 0)` → `6 + 8 + 10 = 18`

---

## 5) Qual será o conteúdo do array `lista` após a execução do código?

```javascript
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```

**Alternativa correta:**
**c) `["banana", "abacaxi", "manga", "laranja"]`**

**Justificativa:**
O código `splice(1, 2, "abacaxi", "manga")` remove 2 elementos a partir do índice 1 (`"maçã"` e `"uva"`) e substitui pelos novos valores `"abacaxi"` e `"manga"`, resultando na lista final.

---

## 6) Sobre herança em JavaScript

**Alternativa correta:**
**a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.**

**Justificativa:**
O `extends` permite que uma classe herde métodos e propriedades de outra, evitando repetição de código.

---

## 7) Sobre classes e herança em JavaScript

```javascript
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }
  apresentar() {
    console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
  }
}

class Funcionario extends Pessoa {
  constructor(nome, idade, salario) {
    super(nome, idade);
    this.salario = salario;
  }
  apresentar() {
    super.apresentar();
    console.log(`Meu salário é R$ ${this.salario}.`);
  }
}
```

**Alternativa correta:**
**a) I e II são verdadeiras.**

**Justificativa:**
A classe `Funcionario` herda de `Pessoa`, podendo acessar `nome` e `idade`, e o código `super.apresentar()` permite chamar o método da classe pai antes de sobrescrevê-lo.

---

## 8) Sobre polimorfismo

**Alternativa correta:**
**b) A asserção é verdadeira e a razão é falsa.**

**Justificativa:**
O polimorfismo permite que métodos sejam reimplementados em classes filhas. JavaScript não suporta sobrecarga de métodos nativamente.

---

## Questões dissertativas

### **9) Correção do código para soma de array**

```javascript
function somaArray(numeros) {
    let soma = 0; // Inicializa soma corretamente
    for (let i = 0; i < numeros.length; i++) { // Corrige `size` para `length`
        soma += 2 * numeros[i]; // Acumula a soma corretamente
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
```

**Explicação:**
- Erro 1: `size` deve ser `length`, pois `size` não existe para arrays em JavaScript.
- Erro 2: `soma` não estava sendo acumulada corretamente, pois era sobrescrita em cada iteração.
- Correção: Inicializei `soma = 0` e utilizei `+=` para acumular o resultado correto.

---

### **10) Exemplo de herança com desconto em produtos**

```javascript
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }
    calcularDesconto() {
        return this.preco * 0.9; // 10% de desconto
    }
}

class Livro extends Produto {
    calcularDesconto() {
        return this.preco * 0.8; // 20% de desconto
    }
}

const produto = new Produto("Cadeira", 100);
console.log(produto.calcularDesconto()); // 90

const livro = new Livro("JavaScript Avançado", 100);
console.log(livro.calcularDesconto()); // 80
```

**Explicação:**
- Herança: `Livro` herda de `Produto`, então `Livro` possui os mesmos atributos e métodos.
- Modificação: `Livro` sobrescreve o método `calcularDesconto()`, aplicando um desconto maior (20%) do que o padrão (10%).
- Benefício: Permite reutilizar código e modificar apenas o necessário, sem precisar reescrever toda a lógica.