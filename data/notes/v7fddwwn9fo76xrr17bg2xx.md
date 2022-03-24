> QUESTIONS: 
> - [ ] adjancy $a_{ji}$?!
> - [ ] graph strong?
> - [ ] graph aperiodic?
> - [ ] all closed strong components are aperiodic?
> - [ ] expression (7) in 3.5. page 8 where is i and t?

## Points à retenir

- Modèles:
    - French DeGroot Opinion Pooling
        - discret et sans entrée
        - stochastique
    - Abelson's Models
        - extension continue de French DeGroot
-... #tbc


## Résumé

...

### 3. French DeGroot Opinion Pooling

- one of the first agent-based models of opinion formation

- binding together SNA and systems theory

- **“iterative opinion pooling”**

- it may also be considered as an algorithm of non-Bayesian learning [72, 73]

- goal: find a math model for social power

- _**social power**_:

    individual's ability to control the group's behaviour (notion of centrality)

- made the link between opinion formation and centrality measures

#### 3.1. French DeGroot Model

- **discrete-time process**

- **parameter**:

    _matrix of influence weights_ $W = (w_{ij})$ with  $w_{ij} \leq 0$

- the greater weight is assigned to agent $j$, the stronger is its influence on agent $i$

- **vector of opionion**:

    $x(k) = \big( x_1(k), ..., x_n(k) \big)^T\quad$ obeys the equations $\quad x(k+1) = W x(k)$

    Equivalently, $\quad x_i(k+1) = \sum_{j=1}^{n} w_{ij}x_j(k) \quad \forall i \in \{0,...,n\} \quad \forall k \in \mathbb{N} \quad$

- self-inlfuence = opnenness to assimilation of others' opinions

- agent with $w_{ii} = 0$ is _**open-minded**_ and completely relies on others' opinions

- agent with $w_{ii} = 1$ is _**stubborn**_ or _**zealot**_

    Equivalently, $x_i(k) \equiv x_i(0)$

- **opinion matrix**: $X = (x_{il}) \in \mathbb{R}^{n \times m}$ with the agent's opinions in rows $x^{i} = (x_{i1}, ..., x_{im})$

#### 3.2. Model's history

- first applied to a graph whose nodes correspond to agents with self-loop and arcs $(j, i)$ reprensenting _"$j$ has power over $i$"_

- after each iteration, an agent updates its opinion to the _mean value_ of the opinions

- exemple:
    ![](/assets/images/Model.FrenchDeGroot.Example-3-Agents.Dynamics.png)

    ![](/assets/images/Model.FrenchDeGroot.Example-3-Agents.Graph.png)

- **_"consensus"_** = convergence $x_i(k) \xrightarrow[ k \to \infty]{} x_{\star}$ of all opinions to a _common unanimous opinion_

- **_unique Nash equilibrium_** : a distribution which represents a consensus of individual distributions (in a special non-cooperative "Pari-Mutuel" game)
    
    -> see _Eisenberg-Gale convex program_ [79]
    later replace by simpler weighted averaging (i.e. _opinion pooling_)

#### 3.3. Algebraic convergence criteria

- **dynamics is _non-expensive_**

- system is always **Lyapunov stable**

    but stability not asymptotic since $W$ always has eigenvalue at 1

- Model convergen = W regular

> **Lemma 9** (Convergence Criterion)
> - Model is **convergent** $\iff$ $\lambda = 1$ is the **only eigenvlaue** of $W$ on the unit circle
> - Model reaches **consensus** $\iff$ **eigenvalue is simple** (i.e. eigenspace is spanned by vector $\mathbb{1}$)


> **Lemma 10** (for irreducible sotchastic $W$)
> - Model is **convergent** and **consensus** reached $\iff$ $W$ is **primitive** (i.e. $W^k$ positive for large $k$)
> - For imprimitive irreducible $W$, the solution **oscillates** for almost all initial conditions

#### 3.4. Graph-theoretic conditions

- limits on Lemma 9 for large scale social networks !

- convergence in French DeGroot model does not depend on the weights but only on the graph !

> **Lemma 11** (when graph $\mathscr{G} = \mathscr{G}[W]$ **strong**)
> - Model reaches **consensus** $\iff$ $\mathscr{G}$ is **aperiodic** (otherwise **oscillations**)

> **Theorem 12**
> 1. Model is **convergent** $\iff$ all closed strong components in $\mathscr{G}[W]$ are **aperiodic** 
> 2. Model reaches **consensus** $\iff$ $\mathscr{G}[W]$ is **quasi-strongly connected** and the only closed strong component is **aperiodic**

> **Corrally 13**
> - Agent's self-weights positive $\implies$ Model is **convergent**
> - Model reaches **consensus** $\iff$ $\mathscr{G}[W]$ is **quasi-strongly connected** (i.e. has a directed spanning tree)

- when $W$ has **zero diagonal entries** a directed spanning tree is a sufficient condition

#### 3.5. Dual Markov Chain

> link to [markov chain](https://en.wikipedia.org/wiki/Markov_chain)'s definition

- row vector: $p(k+1)^T = p(k)^T W$

- $W$ regular $\implies$ $p(\infty)^T = lim_{\,k\to\infty}p(k)^T = p(0)^T W^\infty$

- _regular chain_ (or _ergodic_) : a markov chain that forgets its history and converges to the unique stationary distribution

- _essential classes of states_ = closed strong components

- _inessential (or non-recurrent) states_ = remaining nodes

> **Theorem 12** (with Markov Chains)
> 1. Markov Chain always converges to a stationary distribution $\iff$ all essential classes are **aperiodic**
> 2. **standard ergodicity condition** $:\iff$ essential class is **unique** and **aperiodic**

- $W$ fully-regular $\implies$ $x(k+1) = W^k x(0) \xrightarrow[ k \to \infty]{} ( p_{\infty}^T x(0) ) \mathbb{1}_n$

- $p_{\infty i}$ = measure of _social power_ of agent $i$

    Equivalently, $p_{\infty i}$ is the **weight of its initial opinion** $x_i(0)$ in the **final opinion** of the group.

- _social power_ can be considered as a **centrality measure** (similar to the _eigenvector centrality_)

#### 3.6. Stubborness

- **source node** = stubborn agent = nodes no other **incoming** arcs than itslef

- if source = root and only source in closed strong component then model reaches a consensus

- No consensus if several stubborn agents !!! (there can still be convergences)

> Corollary 14
> Group with several stubborn agent influencing all other individuals $\implies$ model is **convergent**

### 4. Abelson's Models

- continuous counterpart of DeGroot's model (**nonlinear extension**)
- introduced the _community cleavage_ problem (a.k.a. _Abelson's diversity puzzle_)

#### 4.1. Abelson’s models of opinion dynamics

- Alternative interpretation of French-DeGroot model:

    (9): $\quad 1 - w_{ii} = \sum_{j \neq i} w_{ij} \implies x_i(k+1) - x_i(k) = \sum_{j \neq i} w_{ij}[x_j(k) - x_i(k)] \quad \forall i$

- These $n=2$ [dyadic interactions](https://en.wikipedia.org/wiki/Dyad_(sociology)) show that “the attitude positions of two discussants [...] move toward each other”

- Still true for simultaneous interactions of multiple agents:

    Agent $i$ shifts its opinion $x_i(k)$ towards $x_j(k)$ when adjusting it by $\delta_{(j)}x_i(k)$

    $x'_i = x_i + \delta_{(j)}x_i \implies |x_j - x'_i| = (1-w_{ij}) |x_j - x_i|$

- $\delta_{(j)}x_i(k)$ is called the _resultant_ of these simultaneous adjustements

- Continuous-time dynamics (10): $\quad  \dot x_i(t) = \sum_{j \neq i} a_{ij} (x_j(t) - x_i(t) \quad 1 \leq i \leq n$

    with $A = (a_{ij})$ matrix of _infinitesimal influence weights_ (a.k.a. **_contact rates_**)
    
    A is **non-negative** but **not** necessarily **stochastic**

- (10) also reads as:

    The infinitesimal shift of the $i^th$ opinion $dx_i(t) = \dot x_i(t)dt$ is the **superposition of the infinitesimal’s shifts** $a_{ij}(x_j(t)−x_i(t))dt$ of agent $i$’s towards the influencers.


- More generally (11):

    $\dot x_i(t) = \sum_{j \neq i} a_{ij} g(x_i, x_j)(x_j(t) − x_i(t)) \quad \forall i$

    with $g : \mathbb{R}\times\mathbb{R} \to (0;1]$ a **coupling function** (describes the _opinion assimilation_)

- This section focuses on **linear Abelson's model**: 
    
    (12): $\quad \dot x(t) = -L[A] x(t)$
    
    with $L[A]$ _Laplacian natrix_

- Dynamics like (12) are being studied in control theory as a continuous-time consensus algorithm

#### 4.2. Convergence and consensus conditions

- Corollary 6 applies to $L[A]$ and $\lambda_0 = 0$

- Thus (12) is **Lyapunov stable** (yet not asympotically stable)

- **Main difference** with French-DeGroot: (12) **always convergent**

> **Corollary 15** (convergence)
>
> $A$ non-negative $\quad \wedge \quad \exist \;\; P^\infty = lim_{\,t\to\infty} \; e^{-L[A]t} \implies x(t) \xrightarrow[ k \to \infty]{} x^\infty = P^\infty x(0)$

- $P\infty$ is a **projection operator onto the Laplacian’s null space** $ker L[A] = {v | L[A]v = 0}$ and is closely **related to the graph’s structure**

- (12) reaches a _consensus_ $\iff$ final opinions coincide $x_1^\infty = ... = x_n^\infty \quad \forall x(0)$ (initial condition)

- consensus $\implies$ $P^\infty = \mathbb{1}_n \; p_\infty^T$

> **Theorem 16** (consensus vs graph connectivity)
>
> (12) reaches _consensus_ $\iff$
> 
> $\quad \quad \quad \mathscr{G}[A]$ **quasi-strongly connected** (i.e. has a directed spanning tree)
>
> $\quad\wedge\quad$ $lim_{\,t\to\infty} \; x_1(t) = ... = lim_{\,t\to\infty} \; x_n(t) = p_\infty^T x(0)$
> 
> $\quad\wedge\quad$ $p_\infty \in \mathbb{R}^n$ **non-negative** vector and uniquely defined by $\;\; p_\infty^T L[A] = 0 \;\;$ and $\;\; p_\infty^T \mathbb{1}_n = 1$

- $p_\infty$ may be treated as a vector of agents' _social power_ or a centrality measure on the nodes of $\mathscr{G}[A]$

- Discretization Method (from Abelson's model to French-DeGroot's model):

> **Lemma 17** (discretization)
>
> $\forall A$ non-negative $\quad\wedge\quad$ $\tau \geq 0$, $\quad W_\tau = e^{-\tau L[A]}$ **stochastic matrix** $\quad\wedge\quad$ $P^\infty = lim_{\,\tau\to\infty} W_\tau$ also **stochastic**
>
> Moreover, matrices $W_\tau$ have positive diagonal entries

- this lemma can also be used for analysis of time-varying extensions of Abelson’s model

- for more info on:
    - consensus algorithms over time-varying graphs see [56, 100, 101, 103-108]
    - general dunamic agents see [56,57, 109-111]
    - nonlinear consensus algorithms [105, 112, 113]

#### 4.3. The community cleavage problem

> “Since universal ultimate agreement is an ubiquitous outcome of a very broad class of mathematical models, we are naturally led to inquire what on earth one must assume in order to generate the bimodal
outcome of community cleavage studies.”

- **_social cleavage_** = persistent disagreement among agents' opinions (e.g. _clustering_)

- clsutering linked to the presence of _stubborn agents_ (i.e. _source nodes in the graph_)

### 5. Cleavage and Prejudices: Taylor’s model

...#tbc

## Liens de téléchargement

- [IRP.Projet6.Bib1.ProskurnikovTempo.TutorialModelingAnalysisDSN.Part1](https://www.dropbox.com/s/b0ia61x4pdlpbu0/IRP.Projet6.Bib1.ProskurnikovTempo.TutorialModelingAnalysisDSN.Part1.pdf?dl=0)
