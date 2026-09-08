# Teoria das Linguagens e Autômatos
## Exercícios 1 a 11 — Material de Estudo

> **Objetivo:** revisar os fundamentos de Autômatos Finitos Determinísticos (AFDs), interpretação de tabelas e construção de autômatos para diferentes linguagens e sistemas.

---

# Sumário

1. [Parte 1 — Fundamentos](#parte-1--fundamentos)
   - [Exercício 1 — Entendendo um autômato finito](#exercício-1--entendendo-um-autômato-finito)
   - [Exercício 2 — Porta automática](#exercício-2--porta-automática)
2. [Parte 2 — Anatomia e definição formal](#parte-2--anatomia-e-definição-formal)
   - [Exercício 3 — Identificando os elementos](#exercício-3--identificando-os-elementos)
   - [Exercício 4 — A quíntupla do AFD](#exercício-4--a-quíntupla-do-afd)
3. [Parte 3 — Tabela de transições e cadeias](#parte-3--tabela-de-transições-e-cadeias)
   - [Exercício 5 — Interpretando uma tabela](#exercício-5--interpretando-uma-tabela)
   - [Exercício 6 — Aceita ou rejeita?](#exercício-6--aceita-ou-rejeita)
4. [Parte 4 — Construção de AFDs](#parte-4--construção-de-afds)
   - [Exercício 7 — Cadeias que terminam em 1](#exercício-7--cadeias-que-terminam-em-1)
   - [Exercício 8 — Número par de símbolos 1](#exercício-8--número-par-de-símbolos-1)
   - [Exercício 9 — Pelo menos dois zeros consecutivos](#exercício-9--pelo-menos-dois-zeros-consecutivos)
5. [Parte 5 — Desafios de modelagem](#parte-5--desafios-de-modelagem)
   - [Exercício 10 — Semáforo](#exercício-10--semáforo)
   - [Exercício 11 — Sistema de login](#exercício-11--sistema-de-login)
6. [Resumo para a prova](#resumo-para-a-prova)

---

# Parte 1 — Fundamentos

## Exercício 1 — Entendendo um autômato finito

Uma lâmpada controlada por um interruptor possui os estados **Desligado** e **Ligado**. Sempre que o botão é pressionado, ocorre a mudança:

```text
Desligado --pressionar--> Ligado
Ligado --pressionar--> Desligado
```

### 1. Quantos estados existem?

**2 estados:** Desligado e Ligado.

### 2. Qual é o estado inicial?

**Desligado**, pois a lâmpada começa apagada.

### 3. Qual entrada provoca uma transição?

A entrada é **pressionar o botão**.

### 4. Partindo de Desligado, qual será o estado após um acionamento?

**Ligado.**

```text
Desligado --pressionar--> Ligado
```

### 5. Partindo de Desligado, qual será o estado após dois acionamentos?

**Desligado.**

```text
Desligado --pressionar--> Ligado --pressionar--> Desligado
```

### 6. Explique o funcionamento

O sistema possui dois estados. Cada vez que o botão é pressionado, a lâmpada muda para o estado oposto: se estiver desligada, liga; se estiver ligada, desliga.

### 💡 Ideia principal

O estado atual determina o efeito da próxima entrada. Cada `pressionar` provoca uma mudança entre os dois estados.

---

## Exercício 2 — Porta automática

A regra do sistema é:

- Se houver pessoa → **Aberto**
- Se não houver pessoa → **Fechado**

### Tabela de transições

| Estado atual | Entrada | Próximo estado |
|:---|:---|:---|
| Fechado | `pessoa_detectada` | **Aberto** |
| Fechado | `nenhuma_pessoa` | **Fechado** |
| Aberto | `pessoa_detectada` | **Aberto** |
| Aberto | `nenhuma_pessoa` | **Fechado** |

### Diagrama

```text
                      pessoa_detectada
               ┌─────────────────────────┐
               │                         ▼
        ┌─────────────┐             ┌─────────────┐
        │   Fechado   │             │    Aberto   │
        └─────────────┘             └─────────────┘
               ▲                         │
               │                         │
               └────── nenhuma_pessoa ───┘
```

Também existem os laços:

```text
Fechado --nenhuma_pessoa--> Fechado
Aberto  --pessoa_detectada--> Aberto
```

**Estado inicial:** **Fechado**.

### 💡 Ideia principal

A porta sempre deve refletir a entrada atual: pessoa detectada mantém/coloca a porta aberta; ausência de pessoa mantém/coloca a porta fechada.

---

# Parte 2 — Anatomia e definição formal

## Exercício 3 — Identificando os elementos

Considere um AFD com:

- **Σ = {0,1}**
- **Q = {q0,q1}**
- estado inicial: **q0**
- estado final: **q1**

### Tabela de transições

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **q0** | q0 | q1 |
| **q1** | q0 | q1 |

### 1. O alfabeto Σ

**Σ = {0,1}**

São os símbolos que podem ser utilizados como entrada.

### 2. O conjunto de estados Q

**Q = {q0,q1}**

O autômato possui dois estados.

### 3. O estado inicial

**q0**

É o estado onde o processamento começa.

### 4. O conjunto de estados finais F

**F = {q1}**

O único estado de aceitação é `q1`.

### 5. Os símbolos que podem ser lidos

Os símbolos são:

**0 e 1**

### 6. O significado do círculo duplo

Um **círculo duplo representa um estado final/de aceitação**.

Se a cadeia terminar nesse estado, ela é aceita.

### 7. O significado da seta sem origem

A seta que vem de fora do diagrama aponta para o **estado inicial**.

Nesse caso:

```text
→ q0
```

significa que `q0` é o estado inicial.

### 📌 Conceitos importantes

| Símbolo | Significado |
|:---:|:---|
| `Σ` | Alfabeto |
| `Q` | Conjunto de estados |
| `q0` | Estado inicial |
| `F` | Estados finais |
| `δ` | Função de transição |

---

## Exercício 4 — A quíntupla do AFD

Um AFD é formalmente representado por:

```text
M = (Σ, Q, δ, q0, F)
```

### Elementos da quíntupla

| Elemento | Significado |
|:---:|:---|
| **Σ** | Alfabeto de entrada |
| **Q** | Conjunto de estados |
| **δ** | Função de transição |
| **q0** | Estado inicial |
| **F** | Conjunto de estados finais |

### Por que esses cinco elementos são suficientes?

Porque eles informam **quais símbolos podem ser lidos, quais estados existem, para onde o autômato vai a cada entrada, onde o processamento começa e quais estados representam aceitação**.

Assim, podemos determinar completamente o comportamento do AFD para qualquer cadeia de entrada.

### 💡 Para lembrar

A quíntupla responde às cinco perguntas:

1. **O que posso ler?** → `Σ`
2. **Quais estados existem?** → `Q`
3. **Para onde vou?** → `δ`
4. **Onde começo?** → `q0`
5. **Onde aceito?** → `F`

---

# Parte 3 — Tabela de transições e cadeias

## Exercício 5 — Interpretando uma tabela

Considere:

- **Σ = {0,1}**
- **Q = {q0,q1,q2}**
- estado inicial: **q0**
- **F = {q1}**

### Tabela

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **q0** | q0 | q1 |
| **q1** | q2 | q1 |
| **q2** | q1 | q1 |

### 1. Qual é o resultado de δ(q0,0)?

**q0**

### 2. Qual é o resultado de δ(q0,1)?

**q1**

### 3. Qual é o resultado de δ(q1,0)?

**q2**

### 4. Qual é o resultado de δ(q2,1)?

**q1**

### 5. Qual é o estado de aceitação?

**q1**

### 6. Diagrama correspondente

Todas as transições são:

```text
q0 --0--> q0
q0 --1--> q1

q1 --0--> q2
q1 --1--> q1

q2 --0--> q1
q2 --1--> q1
```

Representação simplificada:

```text
                 1
            ┌─────────┐
            │         ▼
        ┌──────┐    ╔══════╗
   ────►│  q0  │    ║  q1  ║
        └──────┘    ╚══════╝
           ▲            │
           │            │ 0
           │            ▼
           │         ┌──────┐
           └─────────│  q2  │
                     └──────┘
```

### 7. Por que o autômato é determinístico?

Porque **para cada estado e cada símbolo existe exatamente uma transição possível**.

Não existe situação em que uma mesma entrada possa levar a dois estados diferentes.

### 💡 Regra de um AFD

Para cada combinação:

```text
(estado atual, símbolo de entrada)
```

deve existir **uma única transição**.

---

## Exercício 6 — Aceita ou rejeita?

Utilizaremos o AFD do Exercício 5:

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **q0** | q0 | q1 |
| **q1** | q2 | q1 |
| **q2** | q1 | q1 |

Estado inicial: **q0**

Estado final: **q1**

### a) Cadeia `1`

```text
q0 --1--> q1
```

Estado final: **q1**

**Resultado: ACEITA**

### b) Cadeia `0011001`

```text
q0 --0--> q0
q0 --0--> q0
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --0--> q1
q1 --1--> q1
```

Estado final: **q1**

**Resultado: ACEITA**

### c) Cadeia `010010`

```text
q0 --0--> q0
q0 --1--> q1
q1 --0--> q2
q2 --0--> q1
q1 --1--> q1
q1 --0--> q2
```

Estado final: **q2**

**Resultado: REJEITA**

### d) Cadeia `1101`

```text
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --1--> q1
```

Estado final: **q1**

**Resultado: ACEITA**

### e) Cadeia `000011010`

```text
q0 --0--> q0
q0 --0--> q0
q0 --0--> q0
q0 --0--> q0
q0 --1--> q1
q1 --1--> q1
q1 --0--> q2
q2 --1--> q1
q1 --0--> q2
```

Estado final: **q2**

**Resultado: REJEITA**

### Resumo

| Cadeia | Estado final | Resultado |
|:---:|:---:|:---:|
| `1` | q1 | **ACEITA** |
| `0011001` | q1 | **ACEITA** |
| `010010` | q2 | **REJEITA** |
| `1101` | q1 | **ACEITA** |
| `000011010` | q2 | **REJEITA** |

### 💡 Como resolver qualquer cadeia

1. Comece no estado inicial.
2. Leia a cadeia da esquerda para a direita.
3. Para cada símbolo, consulte a tabela.
4. O estado onde você terminar determina o resultado.
5. Se o estado final estiver em `F` → **ACEITA**.
6. Caso contrário → **REJEITA**.

---

# Parte 4 — Construção de AFDs

## Exercício 7 — Cadeias que terminam em 1

Precisamos lembrar apenas **qual foi o último símbolo lido**.

Podemos usar dois estados:

- `q0` = cadeia vazia ou termina em `0`
- `q1` = cadeia termina em `1`

Como queremos cadeias que terminam em `1`, `q1` será final.

### Definição formal

- **Σ = {0,1}**
- **Q = {q0,q1}**
- **q0** = estado inicial
- **F = {q1}**

### Tabela

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **q0** | q0 | q1 |
| **q1** | q0 | q1 |

### Diagrama

```text
                     1
                ┌─────────┐
                │         ▼
            ┌──────┐    ╔══════╗
        ───►│  q0  │    ║  q1  ║
            └──────┘    ╚══════╝
                ▲            │
                │            │ 1
                └──── 0 ─────┘
```

Transições:

```text
q0 --0--> q0
q0 --1--> q1
q1 --0--> q0
q1 --1--> q1
```

### Testes

| Cadeia | Estado final | Resultado |
|:---:|:---:|:---:|
| `1` | q1 | **ACEITA** |
| `01` | q1 | **ACEITA** |
| `101` | q1 | **ACEITA** |
| `0001` | q1 | **ACEITA** |
| `1101` | q1 | **ACEITA** |
| `ε` | q0 | **REJEITA** |
| `0` | q0 | **REJEITA** |
| `10` | q0 | **REJEITA** |
| `100` | q0 | **REJEITA** |
| `1110` | q0 | **REJEITA** |

### 💡 Ideia para construir

A pergunta que o autômato precisa responder é:

> **"A cadeia termina em 1?"**

Por isso, basta lembrar o último símbolo.

---

## Exercício 8 — Número par de símbolos 1

Precisamos controlar apenas duas situações:

- **qPar** → quantidade de `1`s é par
- **qImpar** → quantidade de `1`s é ímpar

Sempre que aparece `1`, trocamos de estado.

Quando aparece `0`, nada muda.

### Definição formal

- **Σ = {0,1}**
- **Q = {qPar,qImpar}**
- **q0 = qPar**
- **F = {qPar}**

Portanto:

```text
M = ({0,1}, {qPar,qImpar}, δ, qPar, {qPar})
```

### Tabela

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **qPar** | qPar | qImpar |
| **qImpar** | qImpar | qPar |

### Diagrama

```text
                    1
             ┌───────────────┐
             │               ▼
          ╔═══════╗       ┌─────────┐
      ───►║ qPar  ║       │ qImpar  │
          ╚═══════╝       └─────────┘
             ▲               │
             │               │ 1
             └───────────────┘
```

Transições com `0`:

```text
qPar   --0--> qPar
qImpar --0--> qImpar
```

### Processamento das cadeias

#### `ε`

Nenhum `1`.

```text
qPar
```

Quantidade de `1`: 0 → par.

**ACEITA**

#### `0`

```text
qPar --0--> qPar
```

Quantidade de `1`: 0.

**ACEITA**

#### `1`

```text
qPar --1--> qImpar
```

Quantidade de `1`: 1.

**REJEITA**

#### `11`

```text
qPar --1--> qImpar
qImpar --1--> qPar
```

Quantidade de `1`: 2.

**ACEITA**

#### `101`

```text
qPar --1--> qImpar
qImpar --0--> qImpar
qImpar --1--> qPar
```

Quantidade de `1`: 2.

**ACEITA**

#### `1100`

```text
qPar --1--> qImpar
qImpar --1--> qPar
qPar --0--> qPar
qPar --0--> qPar
```

Quantidade de `1`: 2.

**ACEITA**

#### `10101`

Possui 3 símbolos `1`.

```text
qPar --1--> qImpar
qImpar --0--> qImpar
qImpar --1--> qPar
qPar --0--> qPar
qPar --1--> qImpar
```

Estado final: `qImpar`

**REJEITA**

### Resumo

| Cadeia | Nº de `1` | Resultado |
|:---:|---:|:---:|
| `ε` | 0 | **ACEITA** |
| `0` | 0 | **ACEITA** |
| `1` | 1 | **REJEITA** |
| `11` | 2 | **ACEITA** |
| `101` | 2 | **ACEITA** |
| `1100` | 2 | **ACEITA** |
| `10101` | 3 | **REJEITA** |

### 💡 Ideia para construir

A pergunta que o autômato precisa responder é:

> **"A quantidade de 1s é par ou ímpar?"**

Não precisamos contar exatamente quantos `1`s existem. Basta saber se a quantidade é **par ou ímpar**.

---

## Exercício 9 — Pelo menos dois zeros consecutivos

Precisamos detectar a ocorrência de:

```text
00
```

Podemos usar **3 estados**:

- `q0` → ainda não apareceu `0`
- `q1` → apareceu um `0`, mas ainda não apareceu `00`
- `q2` → já apareceu `00`

Depois que chegamos em `q2`, **não saímos mais dele**, porque a cadeia já possui `00` e continuará sendo aceita.

### 1. O que o estado inicial representa?

`q0` representa que **ainda não encontramos um zero que possa iniciar `00`**.

### 2. O que ocorre quando aparece o primeiro `0`?

Vamos para `q1`.

```text
q0 --0--> q1
```

### 3. O que ocorre quando outro `0` aparece imediatamente depois?

Chegamos em `q2`.

```text
q1 --0--> q2
```

Encontramos `00`.

### 4. Depois de encontrar `00`, a cadeia pode deixar de ser aceita?

**Não.**

Uma vez encontrado `00`, não importa quais símbolos apareçam depois. A cadeia continuará contendo `00`.

Por isso:

```text
q2 --0--> q2
q2 --1--> q2
```

### 5. Quantos estados são necessários?

**3 estados.**

### Quíntupla

- **Σ = {0,1}**
- **Q = {q0,q1,q2}**
- **q0** = estado inicial
- **F = {q2}**

Portanto:

```text
M = ({0,1}, {q0,q1,q2}, δ, q0, {q2})
```

### Tabela

| δ | `0` | `1` |
|:---:|:---:|:---:|
| **q0** | q1 | q0 |
| **q1** | q2 | q0 |
| **q2** | q2 | q2 |

### Diagrama

```text
                    0
               ┌──────────┐
               │          ▼
           ┌──────┐    ┌──────┐
       ───►│  q0  │    │  q1  │
           └──────┘    └──────┘
               ▲           │
               │           │ 0
               │           ▼
               │        ╔══════╗
               └─── 1 ──║  q2  ║
                         ╚══════╝
                           │ ▲
                           │ │
                         0,1 │
                           └─┘
```

Transições:

```text
q0 --0--> q1
q0 --1--> q0

q1 --0--> q2
q1 --1--> q0

q2 --0--> q2
q2 --1--> q2
```

### Testes

#### `00`

```text
q0 --0--> q1
q1 --0--> q2
```

Estado final: `q2`

**ACEITA**

#### `001`

```text
q0 --0--> q1
q1 --0--> q2
q2 --1--> q2
```

**ACEITA**

#### `100`

```text
q0 --1--> q0
q0 --0--> q1
q1 --0--> q2
```

**ACEITA**

#### `1001`

```text
q0 --1--> q0
q0 --0--> q1
q1 --0--> q2
q2 --1--> q2
```

**ACEITA**

#### `110011`

```text
q0 --1--> q0
q0 --1--> q0
q0 --0--> q1
q1 --0--> q2
q2 --1--> q2
q2 --1--> q2
```

**ACEITA**

#### `0000`

```text
q0 --0--> q1
q1 --0--> q2
q2 --0--> q2
q2 --0--> q2
```

**ACEITA**

#### `ε`

Nenhuma transição.

Estado final: `q0`

**REJEITA**

#### `0`

```text
q0 --0--> q1
```

**REJEITA**

#### `1`

```text
q0 --1--> q0
```

**REJEITA**

#### `01`

```text
q0 --0--> q1
q1 --1--> q0
```

**REJEITA**

#### `10`

```text
q0 --1--> q0
q0 --0--> q1
```

**REJEITA**

#### `10101`

```text
q0 --1--> q0
q0 --0--> q1
q1 --1--> q0
q0 --0--> q1
q1 --1--> q0
```

**REJEITA**

### Resumo

| Cadeia | Resultado |
|:---:|:---:|
| `00` | **ACEITA** |
| `001` | **ACEITA** |
| `100` | **ACEITA** |
| `1001` | **ACEITA** |
| `110011` | **ACEITA** |
| `0000` | **ACEITA** |
| `ε` | **REJEITA** |
| `0` | **REJEITA** |
| `1` | **REJEITA** |
| `01` | **REJEITA** |
| `10` | **REJEITA** |
| `10101` | **REJEITA** |

### 💡 Ideia para construir

A pergunta que o autômato precisa responder é:

> **"Já encontrei dois zeros consecutivos?"**

Por isso, precisamos distinguir:

```text
q0 → nenhum 0 relevante
q1 → encontrei um 0
q2 → encontrei 00
```

---

# Parte 5 — Desafios de modelagem

## Exercício 10 — Semáforo

Temos três estados:

- **Verde**
- **Amarelo**
- **Vermelho**

A entrada é `tempo`, que faz o semáforo avançar para o próximo estado.

### 1. Diagrama

```text
                     tempo
             ┌──────────────────┐
             │                  ▼
        ┌─────────┐         ┌──────────┐
        │  Verde  │         │ Amarelo  │
        └─────────┘         └──────────┘
             ▲                    │
             │                    │ tempo
             │                    ▼
             │              ┌──────────┐
             └──── tempo ───│ Vermelho │
                            └──────────┘
```

Ou, resumidamente:

```text
Verde --tempo--> Amarelo
Amarelo --tempo--> Vermelho
Vermelho --tempo--> Verde
```

### 2. Tabela de transições

| Estado atual | Entrada | Próximo estado |
|:---|:---:|:---|
| Verde | `tempo` | Amarelo |
| Amarelo | `tempo` | Vermelho |
| Vermelho | `tempo` | Verde |

### 3. Definição formal

Podemos definir:

- **Σ = {tempo}**
- **Q = {Verde, Amarelo, Vermelho}**
- **q0 = Verde**
- **F = ∅**

Então:

```text
M = ({tempo}, {Verde, Amarelo, Vermelho}, δ, Verde, ∅)
```

Onde:

```text
δ(Verde, tempo) = Amarelo
δ(Amarelo, tempo) = Vermelho
δ(Vermelho, tempo) = Verde
```

### 4. Explicação

O semáforo começa no estado **Verde**. Quando ocorre a entrada `tempo`, ele muda para **Amarelo**. Com outro `tempo`, passa para **Vermelho**. Com mais um `tempo`, volta para **Verde**.

Esse processo continua repetidamente:

```text
Verde → Amarelo → Vermelho → Verde → ...
```

### Estados de aceitação fazem sentido?

**Não necessariamente.**

Um semáforo é um sistema que representa um **processo contínuo**, e não um sistema que precisa dizer se uma cadeia de entradas foi aceita ou rejeitada.

Por isso, é adequado usar:

**F = ∅**

Ou seja, **nenhum estado é de aceitação**.

> Em um AFD usado para reconhecer uma linguagem, estados finais são fundamentais. Porém, quando estamos apenas modelando o comportamento de um sistema, como um semáforo, eles podem não ter utilidade.

### 💡 Ideia principal

O objetivo aqui não é reconhecer uma linguagem, mas representar o **ciclo de funcionamento** de um sistema.

---

## Exercício 11 — Sistema de login

O sistema precisa saber **quantas tentativas incorretas já aconteceram**.

Se usarmos somente:

```text
Aguardando
Autenticado
Bloqueado
```

não conseguimos saber se o usuário errou:

- 0 vezes;
- 1 vez;
- 2 vezes;
- ou 3 vezes.

Portanto, precisamos criar estados diferentes para representar cada quantidade de erros.

### 1. Todos os estados necessários

Podemos usar:

- **Aguardando_0** → nenhuma tentativa incorreta
- **Aguardando_1** → 1 tentativa incorreta
- **Aguardando_2** → 2 tentativas incorretas
- **Autenticado** → senha correta
- **Bloqueado** → 3 tentativas incorretas

Assim:

```text
Q = {
    Aguardando_0,
    Aguardando_1,
    Aguardando_2,
    Autenticado,
    Bloqueado
}
```

### 2. Alfabeto de entrada

As entradas são:

```text
Σ = {senha_correta, senha_incorreta}
```

### 3. Estado inicial

O usuário começa sem nenhuma tentativa incorreta:

**q0 = Aguardando_0**

### 4. Estados finais

Se considerarmos que o objetivo do sistema é reconhecer quando o usuário foi autenticado:

**F = {Autenticado}**

O estado `Bloqueado` **não é final**, pois o usuário não conseguiu autenticar.

### 5. Todas as transições

#### Aguardando_0

Se acertar:

```text
Aguardando_0 --senha_correta--> Autenticado
```

Se errar:

```text
Aguardando_0 --senha_incorreta--> Aguardando_1
```

#### Aguardando_1

Se acertar:

```text
Aguardando_1 --senha_correta--> Autenticado
```

Se errar novamente:

```text
Aguardando_1 --senha_incorreta--> Aguardando_2
```

#### Aguardando_2

Se acertar:

```text
Aguardando_2 --senha_correta--> Autenticado
```

Se errar pela terceira vez:

```text
Aguardando_2 --senha_incorreta--> Bloqueado
```

#### Autenticado

Depois de autenticado, podemos considerar que o sistema permanece autenticado independentemente da entrada:

```text
Autenticado --senha_correta--> Autenticado
Autenticado --senha_incorreta--> Autenticado
```

#### Bloqueado

Depois de bloqueado, não pode mais voltar a tentar:

```text
Bloqueado --senha_correta--> Bloqueado
Bloqueado --senha_incorreta--> Bloqueado
```

### 6. Tabela completa

| Estado atual | `senha_correta` | `senha_incorreta` |
|:---|:---:|:---:|
| **Aguardando_0** | Autenticado | Aguardando_1 |
| **Aguardando_1** | Autenticado | Aguardando_2 |
| **Aguardando_2** | Autenticado | Bloqueado |
| **Autenticado** | Autenticado | Autenticado |
| **Bloqueado** | Bloqueado | Bloqueado |

### 7. Diagrama

```text
                                      senha_correta
                                ┌─────────────────────┐
                                │                     ▼
                         ┌─────────────┐        ╔═════════════╗
                    ────►│ Aguardando_0│        ║ Autenticado ║
                         └─────────────┘        ╚═════════════╝
                                │                       ▲
                                │                       │
                         senha_incorreta               │
                                ▼                       │
                         ┌─────────────┐               │
                         │ Aguardando_1│───correta─────┤
                         └─────────────┘               │
                                │                       │
                         senha_incorreta               │
                                ▼                       │
                         ┌─────────────┐               │
                         │ Aguardando_2│───correta─────┘
                         └─────────────┘
                                │
                         senha_incorreta
                                ▼
                         ┌─────────────┐
                         │  Bloqueado  │
                         └─────────────┘
```

Para deixar claro o comportamento dos estados:

```text
Autenticado --qualquer entrada--> Autenticado

Bloqueado --qualquer entrada--> Bloqueado
```

### 8. Definição formal do AFD

A quíntupla é:

```text
M = (Σ, Q, δ, q0, F)
```

Onde:

```text
Σ = {senha_correta, senha_incorreta}

Q = {
    Aguardando_0,
    Aguardando_1,
    Aguardando_2,
    Autenticado,
    Bloqueado
}

q0 = Aguardando_0

F = {Autenticado}
```

E a função de transição é:

```text
δ(Aguardando_0, senha_correta)   = Autenticado
δ(Aguardando_0, senha_incorreta) = Aguardando_1

δ(Aguardando_1, senha_correta)   = Autenticado
δ(Aguardando_1, senha_incorreta) = Aguardando_2

δ(Aguardando_2, senha_correta)   = Autenticado
δ(Aguardando_2, senha_incorreta) = Bloqueado

δ(Autenticado, senha_correta)    = Autenticado
δ(Autenticado, senha_incorreta)  = Autenticado

δ(Bloqueado, senha_correta)      = Bloqueado
δ(Bloqueado, senha_incorreta)    = Bloqueado
```

### 9. Apenas Aguardando, Autenticado e Bloqueado são suficientes?

**Não.**

Porque o sistema precisa diferenciar:

```text
Aguardando + 0 erros
Aguardando + 1 erro
Aguardando + 2 erros
```

Se todos fossem representados pelo mesmo estado `Aguardando`, o autômato não saberia quando bloquear o usuário.

Por isso precisamos de **três estados de espera diferentes**, além de `Autenticado` e `Bloqueado`.

### 💡 Regra para lembrar

Esse exercício mostra uma técnica muito importante na construção de AFDs:

> **Se o autômato precisa "lembrar" alguma informação do passado, essa informação normalmente precisa ser representada pelos estados.**

Aqui, o que ele precisa lembrar é:

**quantas tentativas incorretas já ocorreram.**

Por isso:

```text
0 erros → Aguardando_0
1 erro  → Aguardando_1
2 erros → Aguardando_2
3 erros → Bloqueado
```

---

# Resumo para a prova

## Como pensar na construção de um AFD

Antes de criar os estados, pergunte:

> **"O que o autômato precisa lembrar daquilo que já leu?"**

### Exemplos dos exercícios

| Problema | O que precisa ser lembrado? | Estados |
|:---|:---|:---|
| Lâmpada | Se está ligada ou desligada | 2 |
| Porta automática | Se está aberta ou fechada | 2 |
| Termina em `1` | Último símbolo | 2 |
| Quantidade par de `1` | Paridade da quantidade de `1`s | 2 |
| Possui `00` | Se já apareceu nenhum, um ou dois `0`s consecutivos | 3 |
| Login | Quantidade de tentativas incorretas | 5 |
| Semáforo | Cor atual | 3 |

## Regras fundamentais

### 1. Estado inicial

É onde o processamento começa:

```text
q0
```

### 2. Estado final

Se, depois de processar toda a cadeia, o autômato estiver em um estado pertencente a `F`:

```text
ACEITA
```

Caso contrário:

```text
REJEITA
```

### 3. AFD

Em um AFD, para cada:

```text
estado + símbolo
```

deve existir **exatamente uma transição**.

### 4. Círculo duplo

Representa um **estado final/de aceitação**.

### 5. Seta sem origem

Indica o **estado inicial**.

### 6. Quíntupla

```text
M = (Σ, Q, δ, q0, F)
```

- `Σ` → alfabeto
- `Q` → estados
- `δ` → transições
- `q0` → estado inicial
- `F` → estados finais

---

> **Resumo da estratégia:** primeiro descubra o que precisa ser lembrado; depois transforme cada situação relevante em um estado; em seguida defina as transições para cada símbolo do alfabeto.
