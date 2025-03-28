# Lista 02 - Respostas

## Questões Objetivas

1) **Resposta:** A  
O código avalia a expressão booleana, imprime "true", calcula o produto dos números na lista e imprime o resultado no console.

2) **Resposta:** A  
Ambas as funções exibirão:  
"Seu crédito foi aprovado. Saldo disponível: 400."

3) **Resposta:** B  
O código verifica se a idade pertence à faixa adulta. Se for, exibe "Você é um adulto!". Caso contrário, verifica se é menor de idade e exibe "Você é menor de idade!". Se nenhuma das condições anteriores for verdadeira, exibe "Você está na melhor idade!".

4) **Resposta:** D  
O processamento dos dispositivos resulta em:  
- Dispositivo 1 ligado. Energia restante: 900  
- Dispositivo 2 ligado. Energia restante: 300  
- Dispositivo 3 ligado com bateria extra. Energia restante: 200  
- Dispositivo 4 não pode ser ligado. Energia insuficiente.  
- Dispositivo 5 não pode ser ligado. Energia insuficiente.

5) **Resposta:** B  
O método "update()" é chamado continuamente a cada quadro (frame) do jogo, sendo usado para atualizar a lógica, movimentação e interações dos objetos na cena.

6) **Resposta:** A  
O módulo Matter.js Physics em Phaser.js tem como principal objetivo simular física avançada, incluindo corpos rígidos, colisões complexas e interação entre objetos com gravidade e forças.

## Questões Dissertativas

### 7) Classificação de Pedidos - Pseudocódigo

Algoritmo ClassificarFrete
    Ler valorTotal
    Se valorTotal < 50 então
        Escrever "Frete não disponível!"
    Senão se (valorTotal >= 50) e (valorTotal <= 199.99) então
        Escrever "Frete com custo adicional!"
    Senão
        Escrever "Frete grátis!"
    FimSe
FimAlgoritmo

### 8) Implementação das classes Carro e Moto (herdando de Veiculo)

Classe base Veiculo
Classe Veiculo:
    Atributos:
        modelo
        ano
    Método Construtor(modelo, ano):
        this.modelo <- modelo
        this.ano <- ano
    Método CalcularConsumo():
        // Método genérico a ser sobrescrito
        Retornar "Consumo não definido para o veículo"

Classe derivada Carro
Classe Carro herda de Veiculo:
    Atributos:
        quilometragem
        eficiencia  // em km por litro
    Método Construtor(modelo, ano, quilometragem, eficiencia):
        Chamar Construtor de Veiculo(modelo, ano)
        this.quilometragem <- quilometragem
        this.eficiencia <- eficiencia
    Método CalcularConsumo():
        consumo <- quilometragem / eficiencia
        Retornar consumo

Classe derivada Moto
Classe Moto herda de Veiculo:
    Atributos:
        quilometragem
        eficiencia  // em km por litro
    Método Construtor(modelo, ano, quilometragem, eficiencia):
        Chamar Construtor de Veiculo(modelo, ano)
        this.quilometragem <- quilometragem
        this.eficiencia <- eficiencia
    Método CalcularConsumo():
        consumo <- quilometragem / eficiencia
        Retornar consumo

### 9) Simulação do Sistema de Pouso

Algoritmo SimularPouso
    Ler velocidadeInicial, velocidadeSegura, desaceleracao, tempoMaximo
    tempoNecessario <- (velocidadeInicial - velocidadeSegura) / desaceleracao
    
    Se tempoNecessario <= tempoMaximo então
        Escrever "Tempo necessário para pouso seguro: " + tempoNecessario + " segundos."
    Senão
        Escrever "Não é possível atingir a velocidade segura dentro do tempo máximo permitido."
    FimSe
FimAlgoritmo

### 10) Multiplicação de Matrizes de Investimento - Pseudocódigo

Função MultiplicarMatrizesInvestimento(matrizA, matrizB):
    // Verifica se o número de colunas de matrizA é igual ao número de linhas de matrizB
    Se (número de colunas de matrizA ≠ número de linhas de matrizB) então:
        Retornar "As matrizes não podem ser multiplicadas. Dimensões incompatíveis."
    Senão:
        linhas <- número de linhas de matrizA
        colunas <- número de colunas de matrizB
        matrizResultado <- novaMatriz(linhas, colunas) com valores iniciais zero
        
        Para i de 0 até linhas-1 faça:
            Para j de 0 até colunas-1 faça:
                soma <- 0
                Para k de 0 até (número de colunas de matrizA - 1) faça:
                    soma <- soma + (matrizA[i][k] * matrizB[k][j])
                FimPara
                matrizResultado[i][j] <- soma
            FimPara
        FimPara
        
        Retornar matrizResultado
