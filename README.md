# Knowledge-Engineering

[中文](./README_CN.md)

Some projects about knowledge engineering, including 3-SAT phase transition, TransE-Pytorch, self defined GPT-2, and so on.

Due to the long time since these projects were written, they are only organized during my leisure time.

## Projects Details

### Proj. One: 3-SAT phase transition

#### What is 3-SAT phase transition?

SAT (Satisfiability), the Boolean satisfiability problem, is the problem of determining whether there exists a solution that satisfies a given Boolean formula. That is, whether there exists a set of truth assignments (each variable assigned to true or false) such that the entire formula is true. It is the first known NP-Complete problem.

Example: Given a Boolean formula $F=(p\vee q)\wedge \neg q$, it is clear that when $p=True, q=False$, F=True. That is, there exists a set of truth assignments ( $p=True, q=False$ ) that make the entire expression true. In this case, the expression $F=(p\vee q)\wedge \neg q$ is satisfiable.

3-SAT (3-Satisfiability) is a special case of the Boolean satisfiability problem, where the entire expression is a conjunction of disjunctive normal forms (3-CNF), with each disjunctive clause containing exactly three literals. (A literal can be understood as the smallest indivisible atomic logical proposition or its negation)

Specifically, the 3-SAT problem can be represented as follows:
$$
F = (l_{1,1}\vee l_{1,2}\vee l_{1,3}) \wedge (l_{2,1}\vee l_{2,2}\vee l_{2,3}) \wedge \cdots \wedge (l_{m,1}\vee l_{m,2}\vee l_{m,3})
$$

Where $l$ is a literal, which can be a propositional variable (e.g., $p$) or its negation (e.g., $\neg p$).

It can be proven that all SAT problems can be reduced to 3-SAT, meaning that 3-SAT is also an NP-Complete problem. This will not be elaborated here.

**Phase Transition Effect**:
For randomly generated $\omega$ CNF samples, when $\omega$ is sufficiently large, there exists a critical clause density (the ratio of the number of clauses to the number of variables) $r^*$ such that when $r\le r^*$, the probability that a 3-CNF expression with n variables and nr clauses is satisfiable approaches 1. When $r>r^*$, the probability of satisfiability approaches 0. This critical value $r^*$ is called the "phase transition point", and this phenomenon is known as the phase transition effect of the SAT problem.

In this project, I directly used pysat to solve SAT expressions and presented a phase transition effect graph. Due to performance and time constraints, I did not perform extensive sampling, and the resulting curve does not clearly show $r^*\approx4.26$. With a sufficient number of clauses and sampling times, a better presentation can be observed, as shown in the figure below.
![3-sat](.\imgs\3-sat.png)