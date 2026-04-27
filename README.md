# cynthus
Programming language designed for agents.

# Prinary Thesis

Programming languages have always reflected their primary writers. 

Assembly was shaped by humans writing close to the metal,  C was shaped by humans wanting portability. Python was shaped by humans who wanted readability, so each language carries the cognitive constraints, error recovery patterns, and collaboration models of the writers who shaped it.

Today, agents are becoming primary writers of code (we are becoming more dependent on them). However, the languages they write today
were not designed for them. They inherited Python, JavaScript etc, with all the design practices that exist for human
readability. The languages were not designed with agents in mind.

The failure modes agents have right now in production systems such as confident misinterpertation, state degradation across long contexts, compounding recovery failures, implicit overconfidence are failures of the substrate. Agents are expensive, slow, probabilistic, and have side effects. The languages they run on are designed on the principle that code is fast, cheap, and deterministic. So every agent framework today is duct-taping around this mismatch.

Cynthus is a candidate design for what an agent-native language should look like. Inference is the special case requiring proof, instead of the default of trust. Confidence is earned through verification, not claimed by the model. The runtime owns orchestration; the agent contributes inference and nothing else.

# What this repository contains

A working prototype, in OCaml, of a small typed language with three load-bearing features:

* **Effect categories in the type signature:** Functions declare whether they call a model, the type checker refuses to mix inferential and pure
operations without explicit annotation.

* **Confidence as a propagating type-level property:** Values carry confidence levels, and combination takes the minimum. The only way to raise confidence is to pass a value through a verifier with a published accuracy.

* **Verifiers as first class constructs:** A verifier is a typed function with known accuracy on a held out set. The prototype ships one: JSON schema validation. The pattern extends to compilers, test runners, and structural checkers.

The prototype is a tree walking interpreter. The goal is to not have native compilation. The contribution is the design, demonstrated
through a runnable artifact.

# Status

Currently a prototype (WIP), with 3 of 11 concepts from the design implemented. The remaining eight are deferred until the prototype proves the basics compose. Check [DESIGN.md](DESIGN.md) for the full architecture, the load bearing version of the design, and what is intentionally not built yet.

# Project Goal
The goal of the project is to explore how an agent-native programming language would look like, building on a vision where in the future agents become the primary developers. The prototype tests whether the foundational claims about effects and confidence in the type system hold up against real inference. If they do, the rest of the architecture earns the right to be built. If they do not, the postmortem itself is a contribution to the design conversation.


