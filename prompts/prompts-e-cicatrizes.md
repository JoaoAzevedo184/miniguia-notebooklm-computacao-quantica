# 3. Engenharia de Prompts e "Cicatrizes"

Esta seção documenta o raciocínio por trás dos resultados: as perguntas estratégicas, as variações testadas, e principalmente as **dificuldades** encontradas para extrair a melhor resposta.

## 3.1 Prompts estratégicos testados

| Prompt | Objetivo | Resultado / Observação |
|--------|----------|------------------------|
| "Explique superposição e emaranhamento usando uma analogia, e depois de forma técnica com base nas fontes." | Forçar dupla camada (intuição + rigor) | *(preencher com o resumo da resposta e as fontes citadas)* |
| "Compare Grover e Deutsch-Jozsa: que tipo de vantagem cada um demonstra e sobre qual problema?" | Entender vantagem quântica na prática | *(preencher)* |
| "O que torna um circuito quântico 'treinável'? Explique o papel dos QNodes e da diferenciação automática." | Conectar quantum com ML | *(preencher)* |
| "Liste as principais abordagens de QML citadas nas fontes e diga em uma frase o que diferencia cada uma." | Mapear o campo | *(preencher)* |
| "Quais pré-requisitos matemáticos as fontes assumem? Faça uma lista mínima." | Descobrir lacunas de base | *(preencher)* |

## 3.2 Variações de prompt (o que mudou o resultado)

Pares de "antes/depois" que mostraram diferença de qualidade.

### Exemplo

- **Prompt vago:** "Fale sobre quantum machine learning."
- **Prompt refinado:** "Com base nas fontes 2 e 3, resuma em até 5 bullets como o machine learning quântico difere do clássico, citando o mecanismo (kernel, circuito variacional, etc.)."
- **Diferença observada:** *(preencher — normalmente o refinado reduz alucinação e melhora a citação de fonte)*

## 3.3 Cicatrizes / Troubleshooting

Registro honesto das dificuldades — a parte que o mercado mais valoriza.

- **Dificuldade 1:** *(ex.: NotebookLM misturava conceitos de fontes diferentes sem citar qual. Solução: pedir explicitamente "cite a fonte de cada afirmação".)*
- **Dificuldade 2:** *(ex.: respostas longas e genéricas. Solução: impor limite de bullets e foco em um subtema.)*
- **Dificuldade 3:** *(ex.: pergunta de matemática pesada retornava vaga porque as fontes eram introdutórias. Aprendizado: reconhecer o limite do material carregado.)*