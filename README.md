# Qiskit notes
## Introduction and contents
In this repo, I would like to collect some personal notes about quantum information and computing. 
The contents will be divided into notebooks with different topics or levels of difficulty. However, some basic information will be in written form in this readme file. 

## Concept in quantum computing
### Irrelevance of global phases
The global phase of a state in quantum mechanics is irrelevant because it has no measurable impact on physical observations or operations. Therefore, two quantum states ($\ket{\psi}$, $\ket{\phi}$) that differ only by a global phase ($\ket{\psi} = e^{i\theta}\ket{\phi}$) represent the same physical state and are indistinguishable in any measurement or operation.

### No cloning theorem 
This theorem states that it is impossible to create an independent and identical copy of an arbitrary unknown quantum state, in formulas:
```math 
\text{Does not exist a unitary operation } U \text{ such that:} \quad U(\ket{\psi}\otimes\ket{0}) = \ket{\psi}\otimes\ket{\psi} \quad \forall \ket{\psi} \in \mathcal{H}
```
This fundamental principle prevents the perfect replication of quantum information, making it a crucial aspect of quantum mechanics and a cornerstone in quantum computing's security protocols, such as quantum key distribution.

### Query gates
Query gates, also known as oracle gates, are an essential component in quantum algorithms. They allow quantum computers to obtain information from an external function without explicitly evaluating it for all possible inputs. Implementing a query gate involves encoding the function's classical truth table into the quantum state, enabling the algorithm to access the function's results in superposition, achieving a speedup over classical approaches. More precisely: 
```math
\text{The query gate } U_f \text{ for any function } f:\Sigma^n \to \Sigma^m \text{ is defined as } U_f(\ket{y}\ket{x}) = \ket{y \oplus f(x)}\ket{x} \quad \forall \ket{x} \in \Sigma^n, \ket{y} \in \Sigma^m 
```
Typically you can think at $\Sigma$ as the state $`\{ 0, 1 \}`$. The string $y \oplus f(x)$ is the bitwise XOR of $y$ and $f(x)$.

### Phase kickback
A standard situation in query gates is when $\ket{y}$ is equal to $\ket{-}$. In this case:
```math
U_f(\ket{-}\ket{x}) = (-1)^{f(x)}\ket{-}\ket{x}
```

### Boolean Gates
The necessity of unitary operation might be a problem to reproduce boolean gates (such as classical AND or OR) in quantum circuits. You can simulate them with an architecture similar to query gates. The classical function $f:\Sigma^n \to \Sigma^m$ could be implement by a quantum gate $R$ such that
```math
R(\ket{y}\ket{x}) = \ket{g(x)}\ket{f(x)}
```
where $g(x)$ is the _garbage_ of the operation and can be ignored or reset for further operations. 

