# 5. Aprendizados e Próximos Passos

## O que ficou mais claro

- **"Vantagem quântica" não é um conceito único.** A comparação entre Deutsch-Jozsa (vantagem exponencial/determinística, mas sobre um problema artificial) e Grover (vantagem apenas quadrática, porém genérica e aplicável) deixou claro que o valor prático de um algoritmo não se mede só pelo tamanho do speedup teórico.
- **O que torna um circuito "treinável" tem nome e mecanismo.** O elo entre computação quântica e machine learning é o circuito variacional: parâmetros ajustáveis (ângulos de rotação) + QNode (encapsulamento diferenciável) + diferenciação automática (parameter-shift no hardware, backprop no simulador). Antes eu tinha a intuição de "circuito que aprende"; agora entendo as três peças que o sustentam.
- **A codificação de dados (embedding) é uma etapa crítica e não trivial.** Transformar dados clássicos em estados quânticos (Angle, Amplitude, Basis Embedding) é uma decisão de projeto em QML, não um detalhe — e afeta diretamente o que o modelo consegue representar.
- **Engenharia de prompt muda o resultado de forma mensurável.** O contraste entre o prompt vago e o refinado (seção 3.2) mostrou na prática que delimitar escopo, formato e fontes reduz respostas genéricas e melhora a ancoragem no material.

## O que ficou em aberto

- **A matemática formal por trás dos algoritmos.** As fontes cobrem bem a intuição e a aplicação, mas o formalismo (produto tensorial, matrizes unitárias, demonstração do speedup de Grover) merece um estudo dedicado com material mais teórico.
- **Barren plateaus na prática.** Entendi o conceito (o gradiente desaparece e o treino trava), mas não como diagnosticar ou mitigar isso num circuito real — é um tema para aprofundar.
- **Quando o QML realmente compensa.** Na era NISQ, com hardware ruidoso, ainda não me ficou claro em quais problemas concretos o ganho quântico supera o custo e o ruído. É a pergunta mais honesta que sobrou.

## Próximos passos práticos

- **Reproduzir um circuito variacional em PennyLane** no meu homelab, começando por um classificador simples com Angle Embedding — sair da teoria para o código.
- **Rodar um quantum kernel com Qiskit Machine Learning** e compará-lo com um SVM clássico no mesmo dataset, para sentir na prática a diferença de abordagem.
- **Revisitar os pré-requisitos matemáticos** listados na R5 (álgebra linear e números complexos primeiro), fechando as lacunas antes de encarar material mais teórico.
- **Criar um segundo caderno no NotebookLM** focado só em algoritmos variacionais (VQE, QAOA), usando este projeto como modelo de processo.

## Reflexão sobre o método

Usar o NotebookLM como ferramenta de estudo ativo — em vez de só ler as fontes — mudou a dinâmica: as perguntas estratégicas me forçaram a pensar no que eu realmente queria entender antes de buscar a resposta. O registro das cicatrizes (seção 3.3) foi o que mais consolidou o aprendizado, porque me obrigou a perceber *como* a IA respondia melhor, não apenas *o que* ela respondia.