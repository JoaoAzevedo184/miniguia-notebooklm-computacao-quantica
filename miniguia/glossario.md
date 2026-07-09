# Miniguia — Glossário

Conceitos-chave consolidados a partir do estudo no NotebookLM. Revise e ajuste com suas próprias palavras conforme aprofundar.

| Termo | Definição |
|-------|-----------|
| **Qubit** | Unidade básica de informação quântica. Diferente do bit clássico (0 ou 1), pode existir em superposição dos estados $\|0\rangle$ e $\|1\rangle$. |
| **Superposição** | Propriedade que permite a um qubit existir numa combinação linear $\|\psi\rangle = \alpha\|0\rangle + \beta\|1\rangle$ dos estados de base, até ser medido. |
| **Amplitude de probabilidade** | Coeficientes complexos $\alpha$ e $\beta$ de um estado. Pela **Regra de Born**, $\|\alpha\|^2$ e $\|\beta\|^2$ dão a probabilidade de medir $\|0\rangle$ ou $\|1\rangle$. |
| **Medição / Colapso** | Ato de observar o qubit, que força a superposição a "colapsar" para um dos estados de base de forma probabilística. |
| **Esfera de Bloch** | Representação geométrica de um estado puro de um qubit; qualquer ponto na superfície corresponde a um estado em superposição. |
| **Emaranhamento** | Correlação quântica em que o estado de múltiplos qubits não pode ser descrito de forma independente para cada um. |
| **Estado de Bell** | Estado emaranhado máximo de dois qubits, ex.: $\|\Phi^+\rangle = \tfrac{1}{\sqrt{2}}(\|00\rangle + \|11\rangle)$. |
| **Porta quântica** | Operação unitária que transforma o estado de um ou mais qubits (análoga às portas lógicas clássicas). |
| **Notação de Dirac (bra-ket)** | Notação para vetores de estado: ket $\|\psi\rangle$ (vetor) e bra $\langle\psi\|$ (seu adjunto). |
| **Algoritmo de Deutsch-Jozsa** | Determina se uma função é constante ou balanceada; demonstra vantagem exponencial/determinística (1 consulta vs. $2^{n-1}+1$). |
| **Algoritmo de Grover** | Busca não estruturada em $N$ itens; demonstra vantagem quadrática ($\sqrt{N}$ vs. $N$ passos) via amplificação de amplitude. |
| **Vantagem quântica** | Situação em que um algoritmo quântico supera o melhor algoritmo clássico conhecido para um problema. |
| **Circuito variacional (parametrizado)** | Circuito com parâmetros ajustáveis (ângulos de rotação) otimizados por um computador clássico; é o que torna o circuito "treinável". |
| **QNode** | Abstração do PennyLane (`@qml.qnode`) que encapsula um circuito quântico e o expõe como função diferenciável para frameworks clássicos (PyTorch, TF, JAX). |
| **Diferenciação automática** | Cálculo eficiente de gradientes de circuitos quânticos, base da otimização por gradiente. |
| **Regra de Parameter-shift** | Método de gradiente exato executável em hardware quântico real, deslocando parâmetros do circuito. |
| **Quantum kernel** | Mapa de características quântico que codifica dados em estados de alta dimensão para calcular matrizes de kernel (ex.: para SVM). |
| **Rede Neural Quântica (QNN)** | Circuito parametrizado que funciona de forma análoga a neurônios clássicos para classificação/regressão. |
| **Modelo híbrido quântico-clássico** | Arquitetura que integra camadas quânticas variacionais dentro de redes neurais clássicas. |
| **Embedding / Codificação de dados** | Transformação de dados clássicos em estados quânticos: **Angle**, **Amplitude** e **Basis Embedding**. |
| **NISQ** | "Noisy Intermediate-Scale Quantum": era atual de hardware quântico ruidoso e de escala limitada. |
| **Barren plateaus** | Fenômeno em que o gradiente da função de custo desaparece, dificultando o treinamento de QNNs. |