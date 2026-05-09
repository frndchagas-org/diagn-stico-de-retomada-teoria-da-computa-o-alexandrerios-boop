# Diagnóstico de retomada - Teoria da Computação

Esta atividade serve para mapear o que você já domina sobre linguagens formais, autômatos, gramáticas e computabilidade.

Responda individualmente. Use suas palavras. Se usar IA depois da primeira tentativa, registre o uso na seção 7.

## 1. Mapa do que eu lembro

Marque cada tópico como: lembro bem, lembro parcialmente, não lembro, nunca vi ou não tenho certeza.

- alfabeto:  lembro bem
- cadeia  lembro bem
- linguagem: lembro bem
- gramática: lembro bem
- autômato finito: lembro bem
- linguagem regular:lembro parcialmente,
- linguagem livre de contexto:lembro parcialmente,
- linguagem sensível ao contexto:lembro parcialmente,
- linguagem irrestrita:não lembro
- hierarquia de Chomsky:não lembro
- computabilidade: lembro bem
- máquina de Turing: lembro bem

## 2. Definições com exemplo

Explique, com suas palavras e com um exemplo simples, usando o alfabeto `Sigma = {a, b}`.

1. O que é um alfabeto? É o conjunto básico de símbolos que a gente tem disponível para construir qualquer coisa no sistema. É finito e não pode ser vazio. No nosso caso, as "peças" permitidas são apenas a e b.
2. O que é uma cadeia? É basicamente uma sequência formada combinando os símbolos do alfabeto. Pode ser curta, longa ou até vazia ($\epsilon$). Exemplos: $ab, aaaa, bab$.
3. O que é uma linguagem? É um conjunto de cadeias que seguem uma determinada regra. Nem toda combinação de $a$ e $b$ precisa estar na linguagem. Por exemplo: "todas as cadeias que começam com $a$".
4. O que é uma gramática? É o conjunto de regras que diz como a gente "monta" as cadeias válidas de uma linguagem. Ela define a estrutura, partindo de um símbolo inicial e substituindo até chegar nos símbolos finais do alfabeto.

## 3. Linguagens

Considere as linguagens:

```text
L1 = { w em {0,1}* | w termina com 01 }
L2 = { a^n b^n | n >= 0 }
L3 = { a^n b^n c^n | n >= 0 }
```

Para cada linguagem:

1. escreva três palavras que pertencem à linguagem; 
2. escreva duas palavras que não pertencem;
3. diga, se souber, em qual classe ela provavelmente se encaixa;
4. explique o motivo em linguagem simples.
Não há problema em dizer "não sei". Nesse caso, escreva o que te deixou em dúvida.

Minha Resposta:
L1
Pertencem: 01, 101, 11101.
Não pertencem: 00, 110.
Classe: Linguagem Regular.
Motivo: É uma regra simples de busca de padrão no final da string. Dá para resolver com um autômato finito fácil, já que ele só precisa "lembrar" dos últimos dois bits.

L2
Pertencem: ab, aabb, aaabbb (e a cadeia vazia).
Não pertencem: aba, aabbb.
Classe: Livre de Contexto.
Motivo: Aqui o autômato finito já não serve porque ele precisaria "contar" quantos $a$'s apareceram para garantir que venha a mesma quantidade de $b$'s depois, e autômato não tem memória infinita pra contar.

L3
Pertencem: abc, aabbcc, aaabbbccc.
Não pertencem: abbc, abcc.
Classe: Sensível ao Contexto (ou superior).
Motivo: Essa é mais chata porque tem que sincronizar três contagens ao mesmo tempo ($a$, $b$ e $c$). Uma pilha comum não daria conta, precisaria de algo mais potente como uma Máquina de Turing ou duas pilhas.

## 4. Autômato finito

Considere o autômato abaixo, sobre o alfabeto `{0,1}`:

```text 
Estados: q0, q1, q2
Estado inicial: q0
Estado final: q2

Transições:
q0 --0--> q1
q0 --1--> q0
q1 --0--> q1
q1 --1--> q2
q2 --0--> q1
q2 --1--> q0
```

Responda:

1. Qual linguagem esse autômato parece reconhecer? O autômato aceita cadeias que terminam especificamente na sequência 01.

3. Execute manualmente as cadeias abaixo e diga se aceita ou rejeita:
   - `01`  - Aceita
   - `101` - Aceita
   - `100` - Rejeita
   - `1101` - Aceita
   - `111`  - Rejeita
4. Monte uma tabela curta mostrando o caminho dos estados para pelo menos duas cadeias.

Cadeia         Caminho de Estados              Resultado
01             q0---->q1---->q2                  Aceita
100             q0---->q0---->q1---->q1         Rejeita

## 5. Gramática

Considere a gramática:

```text
S -> aS
S -> b
```

Responda:

1. Gere cinco cadeias produzidas por essa gramática.
3. Descreva a linguagem em palavras.
4. Essa gramática parece regular, livre de contexto ou outra classe? Justifique de forma simples.

Minha resposta: 
Cinco cadeias: b, ab, aab, aaab, aaaab.
Descrição: É a linguagem de todas as cadeias que têm qualquer quantidade de letras a (inclusive nenhuma) e terminam obrigatoriamente com um único b.
Classe: É uma Gramática Regular.
Justificativa: Ela segue aquele padrão de ter apenas um não-terminal à direita e sempre no final da regra (linear à direita), o que caracteriza as linguagens regulares.

## 6. Ponto de dificuldade

Escolha um tópico da lista inicial e escreva:

1. o que você entende dele; 
2. onde você se confunde;
3. que tipo de explicação ajudaria: desenho, exemplo, exercício guiado, analogia, prova passo a passo ou lista curta.
   
Minha resposta:
O que entendo: Entendo que a Hierarquia de Chomsky organiza as linguagens em níveis de complexidade, das mais simples (regulares) até as mais complexas (irrestritas).

Onde me confundo: Me perco um pouco na transição da "Livre de Contexto" para a "Sensível ao Contexto". Às vezes é difícil bater o olho em uma regra e saber se ela precisa de uma pilha ou de algo mais.

Ajuda: Um exemplo comparativo (tipo uma tabela) mostrando a mesma lógica em classes diferentes ajudaria a clarear as limitações de cada uma.

## 7. Uso de IA, se houver

Se você usou IA depois da primeira tentativa, registre:

```text
Pergunta feita: Pode me explicar/relembrar de forma resumida esses topicos: alfabeto,cadeia,linguagem,gramatica,automato finito,linguagem regular:lembro parcialmente,
linguagem livre de contexto,linguagem sensível ao contexto,linguagem irrestrita,hierarquia de Chomsky,computabilidade.máquina de Turing 

Como eu verifiquei: Comparei as definições com os materiais que eu já tinha e com as anotações que lembrava de ter visto. Também testei os exemplos práticos de cadeias no autômato para ver se a lógica estava batendo.

O que eu alterei na minha resposta:Eu simplifiquei os textos que a IA gerou para usar minhas próprias palavras e foquei mais nos itens que eu marquei que lembrava bem ou parcialmente, deixando de fora detalhes muito teóricos que não eram necessários agora.

O que ainda não entendi: Ainda sinto um pouco de dificuldade em diferenciar na prática a aplicação de Linguagens Sensíveis ao Contexto e Irrestritas, já que parecem conceitos bem mais abstratos que os primeiros.
```

## Submissão no Moodle

Depois de finalizar, copie no Moodle:

```text
Repositório:
Commit final:
Autoavaliação: nível atual, maior dificuldade e tópico que precisa ser retomado.
```
