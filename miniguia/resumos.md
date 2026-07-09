# Miniguia — Resumos Estruturados

Consolidação do estudo feito no NotebookLM. As respostas completas que embasam estes resumos estão em [`../prompts/respostas.md`](../prompts/respostas.md).

## Fundamentos

**Qubit e superposição.** O qubit é a unidade básica de informação quântica. Ao contrário do bit clássico, pode existir em **superposição** — uma combinação linear $|\psi\rangle = \alpha|0\rangle + \beta|1\rangle$ dos estados de base. Os coeficientes $\alpha$ e $\beta$ são amplitudes complexas, e pela **Regra de Born** a probabilidade de medir cada estado é $|\alpha|^2$ e $|\beta|^2$. No momento da **medição**, a superposição colapsa para um estado definido. A **Esfera de Bloch** dá a intuição geométrica: cada ponto na superfície é um estado puro possível.

**Emaranhamento.** É uma correlação sem análogo clássico: o estado conjunto de dois ou mais qubits **não pode ser fatorado** em estados individuais. O exemplo canônico é o estado de Bell $|\Phi^+\rangle = \tfrac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$, no qual medir o primeiro qubit determina imediatamente o segundo. Essa não-localidade é a base de protocolos como a teletransportação quântica e de códigos de correção de erros.

## Algoritmo em foco

**Grover vs. Deutsch-Jozsa.** Dois marcos que ilustram *tipos diferentes* de vantagem quântica:

- **Deutsch-Jozsa** resolve o problema de decidir se uma função é constante ou balanceada. É o primeiro exemplo histórico de vantagem quântica: onde o clássico precisaria de até $2^{n-1}+1$ consultas para ter certeza, o quântico resolve com **uma única consulta** — vantagem exponencial/determinística.
- **Grover** ataca a **busca não estruturada** em $N$ itens. Sua vantagem é **quadrática** ($\sqrt{N}$ vs. $N$ passos), obtida por amplificação de amplitude. Menos dramático que Deutsch-Jozsa em teoria, mas muito mais **genérico** na prática — pode acelerar uma ampla gama de problemas.

A lição: "vantagem quântica" não é uma coisa só. Deutsch-Jozsa mostra o ganho teórico máximo em um problema artificial; Grover mostra um ganho menor mas aplicável a problemas reais.

## Ponte para o Quantum Machine Learning

O elo entre computação quântica e ML é o **circuito variacional (parametrizado)**: um circuito cujos ângulos de rotação são parâmetros ajustáveis, otimizados por um computador clássico para minimizar uma função de custo — exatamente como pesos de uma rede neural.

Três peças tornam isso possível:

1. **QNode** (PennyLane): encapsula o circuito e o expõe como uma função diferenciável, integrável a PyTorch/TensorFlow/JAX.
2. **Diferenciação automática**: calcula os gradientes do circuito. Em hardware real usa-se a **regra de parameter-shift**; em simuladores, backpropagation.
3. **Codificação de dados (embedding)**: transforma dados clássicos em estados quânticos (Angle, Amplitude, Basis Embedding).

Com isso, as principais **abordagens de QML** se organizam assim: **quantum kernels** (para SVMs), **redes neurais quânticas (QNNs)**, **modelos híbridos** (camadas quânticas dentro de redes clássicas) e **VQAs** (algoritmos variacionais em geral).

**Desafios da era NISQ:** o hardware atual é ruidoso, o que dificulta a convergência; e há o problema teórico dos **barren plateaus**, em que o gradiente some e o treinamento trava. Por isso usam-se otimizadores robustos como SPSA, ADAM e COBYLA.