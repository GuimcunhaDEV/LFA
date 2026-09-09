# Exercício Guiado — Linguagens Formais e Autômatos (Regex)

## 1. Sobre {0,1}: palavras que terminam em 00

**Linguagem:** L = { w ∈ {0,1}* : w termina em "00" }

**Raciocínio:** a condição é só sobre o final da palavra. O que vem antes é livre (qualquer sequência de 0s e 1s, inclusive vazia). O sufixo "00" é fixo e obrigatório.

- Parte livre: `(0|1)*`
- Sufixo fixo: `00`

**Regex:** `(0|1)*00`

| Aceitas | Rejeitadas |
|---|---|
| 00 | 0 |
| 100 | 1 |
| 1100 | 10 |
| 000 | 101 |

---

## 2. Sobre {a,b}: palavras com exatamente dois a

**Linguagem:** L = { w ∈ {a,b}* : w contém exatamente dois a's }

**Raciocínio:** a palavra é uma sequência de blocos de b's intercalados com exatamente dois a's fixos:

`bloco b's` → `a` → `bloco b's` → `a` → `bloco b's`

Cada bloco de b's é `b*` (zero ou mais). O número de `a`'s literais escritos na regex tem que bater exatamente com o "exatamente dois" do enunciado.

**Regex:** `b*ab*ab*`

| Aceitas | Rejeitadas |
|---|---|
| aa | a |
| aba | aaa |
| baab | b |
| bbabab | ababa |

> Observação: se fosse "pelo menos dois a's", a regex mudaria para `b*ab*ab*(ab*)*`.

---

## 3. Identificador: duas maiúsculas + três algarismos + minúscula opcional

**Estrutura fixa, bloco por bloco:**

| Bloco | Regra | Regex |
|---|---|---|
| Duas maiúsculas | `[A-Z]` com quantidade exata `{2}` | `[A-Z]{2}` |
| Três algarismos | `[0-9]` com quantidade exata `{3}` | `[0-9]{3}` |
| Minúscula opcional | `[a-z]` com `?` (zero ou uma vez) | `[a-z]?` |

**Regex:** `[A-Z]{2}[0-9]{3}[a-z]?`

| Aceitas | Rejeitadas |
|---|---|
| AB123 | ab123 |
| AB123x | A123x |
| — | AB12 |
| — | AB1234 |

---

## Desafio: Matrícula Acadêmica (somente curso CCO)

**Formato:** `CURSO-ANO-NÚMERO-TURNO`

**Regex final:** `^CCO-(202[4-9])-\d{4}-(M|T|N)$`

### Justificativa por bloco

| Bloco | Regra do enunciado | Trecho da regex | Por quê |
|---|---|---|---|
| `^` | início da string | âncora | impede lixo antes da matrícula |
| CURSO | apenas CCO | `CCO` | literal fixo, sem alternância |
| `-` | separador | `-` | hífen literal entre blocos |
| ANO | 2024 a 2029 | `(202[4-9])` | prefixo fixo "202" + classe `[4-9]` no último dígito |
| `-` | separador | `-` | hífen literal |
| NÚMERO | exatamente 4 algarismos | `\d{4}` | quantificador exato, nem mais nem menos |
| `-` | separador | `-` | hífen literal |
| TURNO | M, T ou N | `(M|T|N)` | alternância de caractere único |
| `$` | fim da string | âncora | impede lixo depois da matrícula |

### Casos de teste

**Aceitos:**
- `CCO-2024-0001-M`
- `CCO-2029-9999-N`
- `CCO-2027-1234-T`

**Rejeitados:**
- `ESW-2024-0001-M` — curso inválido (só CCO é permitido)
- `cco-2024-0001-M` — minúsculo
- `CCO-2030-0001-M` — ano fora do intervalo
- `CCO-2024-001-M` — só três dígitos no número
- `CCO-2024-00011-M` — cinco dígitos
- `CCO-2024-0001-X` — turno inválido
- `CCO20240001M` — sem hífens
