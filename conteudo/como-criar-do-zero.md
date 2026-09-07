# Como criar estes sistemas do zero (para quem não programa)

> Guia prático. Sem teoria. Você escolhe um problema, cola um prompt, recebe um programa que roda no navegador, testa, pede ajuste. Em 30 minutos tem a primeira ferramenta sua.

---

## 1. O que você precisa ter (nada de instalar servidor)

| Camada | O que é | Opções (escolha UMA para começar) |
|---|---|---|
| **Conversar e criar** | onde você descreve o problema e recebe o software | ChatGPT (GPT-6 Astra), Claude.ai, Gemini |
| **Criar e rodar sozinho** | a IA escreve, executa, testa e corrige no seu computador | Claude Code, Codex, Cursor |
| **Operar o computador** | a IA usa programas e sites por você | Claude in Chrome, ChatGPT Agent/Operator, Codex Computer Use |
| **Publicar** | colocar a ferramenta num link para usar no celular ou compartilhar | GitHub Pages, Vercel, Netlify (todos grátis) |
| **Guardar dados** | quando a ferramenta precisa lembrar coisas | primeiro: o próprio navegador (localStorage); depois: Google Sheets, Supabase |

**Regra para leigo:** comece só com a primeira linha (ChatGPT ou Claude no navegador). O resto entra quando o problema pedir.

---

## 2. O formato mágico: "um arquivo HTML só"

Quase tudo do vídeo (dashboards, simuladores, jogos, página de decisão de cidade, todo-list com coach) é **uma página HTML única** com o código dentro. Por quê:

- roda em qualquer navegador, sem instalar nada;
- você salva como `minha-ferramenta.html`, dá dois cliques e abre;
- publica em um link em 2 minutos;
- a IA gera inteira de uma vez e corrige inteira de uma vez.

Sempre inclua no prompt: **"Entregue como um único arquivo HTML, com CSS e JavaScript dentro, sem dependências externas, funcionando offline."**

---

## 3. Passo a passo da primeira ferramenta (30 minutos)

### Passo 1 — Escolha um incômodo (5 min)
Não escolha "algo legal". Escolha algo que **te irrita toda semana**: controlar gastos, decidir fornecedor, acompanhar pendências, comparar opções, calcular alguma coisa repetida.

### Passo 2 — Descreva no formato IC-RAV (5 min)
Preencha em português normal:

```
INTENÇÃO:    O que quero conseguir? (uma frase)
CONTEXTO:    Quem usa, que dados tenho, onde estão, o que não pode mudar.
RESULTADO:   O que deve existir no final e como saberei que ficou bom.
AUTONOMIA:   O que a IA decide sozinha, o que me pergunta antes.
VERIFICAÇÃO: O que vou testar antes de confiar.
```

### Passo 3 — Cole o prompt de primeira ferramenta (2 min)

```text
Quero uma ferramenta pessoal, não uma resposta em texto.

INTENÇÃO: [ex.: acompanhar meus gastos do mês por categoria e ver onde estou estourando]
CONTEXTO: [ex.: sou leigo, uso no celular e no notebook, lanço os gastos à mão, não quero cadastro nem senha]
RESULTADO: [ex.: página onde lanço valor + categoria + data, vejo total por categoria em gráfico, alerta quando passar do limite que eu definir]
AUTONOMIA: decida o visual e a organização; me pergunte só se algo do resultado ficar ambíguo.
VERIFICAÇÃO: quero testar lançando 5 gastos e ver o gráfico e o alerta funcionando.

Regras:
- Entregue como UM ÚNICO arquivo HTML com CSS e JavaScript dentro, sem dependências externas, funcionando offline.
- Guarde os dados no próprio navegador (localStorage) para eu não perder ao fechar.
- Não invente funcionalidades além do resultado pedido.
- Depois do código, me diga em 3 linhas como salvar e abrir o arquivo.
```

### Passo 4 — Salve e abra (3 min)
1. Copie o código inteiro.
2. Abra o Bloco de Notas (ou TextEdit), cole, salve como `ferramenta.html` (tipo "todos os arquivos").
3. Dê dois cliques. Abre no navegador. Pronto, é seu.

### Passo 5 — Teste e corrija (10 min)
Use de verdade. Quando algo estiver errado, **não explique o código, descreva o comportamento**:

```text
Testei. Problema: ao lançar um gasto sem data, ele some da lista.
Quero: se eu não preencher data, usar a data de hoje.
Me devolva o arquivo HTML completo corrigido.
```

Repita 2 ou 3 vezes. Isso é o "loop" que todo mundo do vídeo faz.

### Passo 6 — Publique (5 min, opcional)
- **Netlify Drop**: arraste o arquivo no site e ganha um link.
- **GitHub Pages**: crie repo, suba o `index.html`, ative Pages. A IA te guia se pedir.

---

## 4. Como as pessoas do vídeo estão criando (padrões, não mágica)

| Quem / o quê | Como fez, na prática | Padrão reutilizável |
|---|---|---|
| Todo-list com aba "Coach" (o próprio apresentador) | Pediu app pessoal; depois pediu uma aba onde a IA analisa como ele usa o app e aponta tarefas paradas | **Ferramenta + uma aba onde a IA comenta seu uso** |
| Dashboard patrimonial | Juntou extratos de bancos e corretoras, pediu consolidação + sugestões + lista de tarefas com "posso fazer sozinho / preciso de você" | **Dados dispersos → um painel → tarefas classificadas por autonomia** |
| Escolher cidade na Europa para 1 mês de dança | Em vez de "pesquise", pediu: pesquise, mostre fontes, compare custos, dê nota por critério e monte uma página de decisão | **Pesquisa → critérios → pesos → página comparativa** (prompt 04) |
| Laboratório que cancelou licenças de software científico | Descreveu o que o software caro fazia com os dados dele e pediu uma versão específica só para o seu caso | **"Refaça só a parte que eu uso do software X"** |
| Astra operando DaVinci Resolve, KiCad, Blender | Deu o objetivo final (vídeo editado, placa roteada) e deixou o agente clicar no programa | **Descreva o resultado, não os cliques** (computer use) |
| Simulador de enchente em cidade costeira | Pediu modelo de cenários com calculadoras para comparar abordagens | **Decisão difícil → simulador com variáveis ajustáveis** |
| Riley Brown: emulador de jogo numa manhã / Leon Lin: floresta 3D em 5 h | Iteração longa: pedido inicial simples, dezenas de rodadas "melhore X, corrija Y" | **Começa simples, itera muito** |
| Matt Shumer: agentes conversando num mundo 3D | Encadeou várias ferramentas (Blender/Unreal + agentes) — nível avançado | **Sistemas de agentes** (nível 5 da trilha) |

O que todos têm em comum:
1. Começam pelo **problema**, não pela ferramenta.
2. Pedem **resultado concreto** (arquivo, painel, placa pronta), não explicação.
3. **Iteram** descrevendo comportamento errado, não código.
4. Aceitam que a IA erra e **conferem** (OSWorld: 72,6% de acerto em computer use).

---

## 5. Escada de evolução para o aluno leigo

| Degrau | Você já consegue | Ferramenta | Prompt base |
|---|---|---|---|
| 1 | Uma página HTML que resolve um incômodo | ChatGPT / Claude no navegador | seção 3 |
| 2 | Ferramenta que guarda dados e tem gráfico | idem + localStorage | prompt 02 |
| 3 | Pesquisa que vira página de decisão com pesos | idem + pesquisa web ligada | prompt 04 |
| 4 | A IA cria, testa e corrige sozinha no seu PC | Claude Code / Codex | prompt 01 |
| 5 | A IA usa um site/programa por você (preencher, baixar, copiar) | Claude in Chrome / Agent / Computer Use | prompt 03 |
| 6 | Mapear uma área da empresa e escolher 3 automações | qualquer um | prompt 05 |
| 7 | Vários agentes com verificação cruzada | Claude Code + subagentes / Codex | nível 5 da trilha |

Cada degrau é uma aula. Cada aula termina com o aluno **abrindo algo que ele mesmo criou**.

---

## 6. Prompts de bolso (copiar e usar)

**Pedir que a IA decida o formato**
```text
Tenho este problema: [PROBLEMA]. Antes de responder, decida: isso se resolve melhor com texto, planilha, página interativa, simulador ou agente que executa? Justifique em 2 linhas e depois construa a opção escolhida.
```

**Transformar uma planilha em painel**
```text
Vou colar dados de uma planilha. Crie um único arquivo HTML onde eu possa colar esses dados (ou carregar um CSV) e ver: totais, gráfico por [CAMPO], os 5 piores/melhores e anomalias explicadas em português. Sem dependências externas.
```

**Pedir que a IA use um site por mim (computer use)**
```text
Objetivo: [ex.: cadastrar o fornecedor X no sistema Y com os dados do PDF anexo]. Faça o passo a passo no navegador. Antes de qualquer ação que salve, envie ou pague, pare e me mostre o que vai fazer. No final, me entregue um resumo do que foi feito e o que não conseguiu.
```

**Pedir "coach" sobre a minha própria ferramenta**
```text
Aqui está a ferramenta que uso [cole o HTML ou descreva]. Analise como eu venho usando (dados abaixo) e aponte: o que está parado há muito tempo, onde estou me sobrecarregando, e uma melhoria de uso por semana.
```

**Corrigir sem saber programar**
```text
Não sei programar. Vou descrever só o que vejo: [comportamento errado]. Quero que aconteça: [comportamento certo]. Devolva o arquivo completo corrigido e diga em 1 linha o que mudou.
```

---

## 7. O que falar para o aluno sobre limites

- A IA **vai errar**. O trabalho dele é conferir, não confiar.
- Dados sensíveis (senhas, financeiro de terceiros, saúde) **não entram em ferramenta improvisada** sem pensar em onde ficam guardados.
- Computer use em sistema real: **sempre com "pare antes de salvar/enviar/pagar"**.
- Software descartável é ótimo; software que virou essencial precisa de backup dos dados.

---

## 8. Como isso vira conteúdo INEMA

- **Reels/Shorts:** "1 incômodo → 1 ferramenta em 10 minutos", gravando a tela do passo a passo da seção 3.
- **Aula:** cada degrau da seção 5.
- **Desafio 30 dias:** um prompt de bolso por dia, com o aluno postando o print da ferramenta.
- **Turma empresarial:** seção 4 (padrões) + prompt 05 aplicado na área do participante.
