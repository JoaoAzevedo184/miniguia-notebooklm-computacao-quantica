# 3. Engenharia de Prompts e "Cicatrizes"

Esta seção documenta o raciocínio por trás dos resultados: as perguntas estratégicas, as variações testadas, e principalmente as **dificuldades** encontradas para extrair a melhor resposta.

> As respostas na íntegra do NotebookLM estão em [`respostas.md`](respostas.md). Aqui ficam o resumo, a análise e as cicatrizes.

## 3.1 Prompts estratégicos testados

| Prompt | Objetivo | Resultado / Observação | Resposta |
|--------|----------|------------------------|----------|
| "Explique superposição e emaranhamento usando uma analogia, e depois de forma técnica com base nas fontes." | Forçar dupla camada (intuição + rigor) | A estrutura "analogia → técnico" funcionou muito bem: trouxe a moeda girando / dados mágicos e depois a formulação com $\|\psi\rangle = \alpha\|0\rangle + \beta\|1\rangle$, Regra de Born e estados de Bell. | [R1](respostas.md#r1--superposição-e-emaranhamento-analogia--técnico) |
| "Compare Grover e Deutsch-Jozsa: que tipo de vantagem cada um demonstra e sobre qual problema?" | Entender vantagem quântica na prática | Pedir comparação explícita gerou uma tabela clara distinguindo vantagem **quadrática** (Grover) de **exponencial/determinística** (Deutsch-Jozsa). O formato comparativo evitou respostas soltas. | [R2](respostas.md#r2--grover-vs-deutsch-jozsa) |
| "O que torna um circuito quântico 'treinável'? Explique o papel dos QNodes e da diferenciação automática." | Conectar quantum com ML | Resposta conectou circuito variacional → QNode → diferenciação automática (parameter-shift, backprop, diferenças finitas). Nomear os dois conceitos no prompt manteve o foco. | [R3](respostas.md#r3--o-que-torna-um-circuito-treinável-qnodes--diferenciação-automática) |
| "Liste as principais abordagens de QML citadas nas fontes e diga em uma frase o que diferencia cada uma." | Mapear o campo | O limite "uma frase por item" produziu uma lista enxuta e comparável (kernels, QNNs, híbridos, VQAs, inferência bayesiana). | [R4](respostas.md#r4--principais-abordagens-de-qml) |
| "Quais pré-requisitos matemáticos as fontes assumem? Faça uma lista mínima." | Descobrir lacunas de base | Boa resposta de meta-estudo: álgebra linear, números complexos, probabilidade, cálculo, trigonometria e notação de Dirac. Útil para planejar o que revisar antes. | [R5](respostas.md#r5--pré-requisitos-matemáticos) |

## 3.2 Variações de prompt (o que mudou o resultado)

Par "antes/depois" que evidencia o impacto da engenharia de prompt.

- **Prompt vago (baseline):** "Fale sobre quantum machine learning." — ver [R6](respostas.md#r6--prompt-vago-baseline-para-comparação)
- **Prompt refinado:** "Com base nas fontes 2 e 3, resuma em até 5 bullets como o machine learning quântico difere do clássico, citando o mecanismo (kernel, circuito variacional, etc.)." — ver [R7](respostas.md#r7--prompt-refinado-versão-melhorada-de-r6)

**Diferença observada:**

| Aspecto | Prompt vago (R6) | Prompt refinado (R7) |
|---------|------------------|----------------------|
| Escopo | Amplo demais — 5 seções cobrindo história, ferramentas, desafios | Focado na pergunta real: o que *difere* do clássico |
| Tamanho | Longo, difícil de revisar depois | 5 bullets, direto ao ponto |
| Ancoragem em fonte | Genérico, sem apontar de onde veio cada afirmação | Restrito às fontes 2 e 3, forçando a IA a se ancorar |
| Utilidade para estudo | Bom panorama inicial | Melhor para revisão e para o glossário |

**Aprendizado:** delimitar (a) o escopo, (b) o formato/tamanho e (c) as fontes específicas melhora drasticamente a qualidade e reduz respostas genéricas. O prompt vago serve como bom *ponto de partida exploratório*; o refinado serve para *consolidar conhecimento*.

## 3.3 Cicatrizes / Troubleshooting

Registro honesto das dificuldades encontradas ao longo do processo.

- **Respostas boas mas longas demais no prompt aberto:** o prompt "Fale sobre QML" retornou um texto extenso e genérico. **Solução:** impor limite de bullets e restringir a fontes específicas (fontes 2 e 3), como feito em R7 — a resposta ficou muito mais aproveitável.
- **Necessidade de forçar a dupla camada intuição+técnica:** perguntar só "explique superposição" tende a devolver ou algo raso ou algo denso demais. **Solução:** pedir explicitamente "analogia, e depois de forma técnica com base nas fontes" garantiu os dois níveis numa resposta só (R1).
- **Comparações exigem formato explícito:** ao pedir para comparar Grover e Deutsch-Jozsa, foi útil pedir a comparação diretamente — a IA respondeu com tabela, o que facilitou distinguir os tipos de vantagem. Sem isso, o risco é receber dois blocos separados sem contraste claro.
- **Limite das fontes em matemática pesada:** as fontes são majoritariamente introdutórias/aplicadas, então perguntas muito profundas de formalismo matemático tendem a ficar em nível de "lista de pré-requisitos" (R5) em vez de demonstração formal. **Aprendizado:** reconhecer o escopo do material carregado e não cobrar da IA o que não está nas fontes.