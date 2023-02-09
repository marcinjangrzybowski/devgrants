# Open Grant Proposal: `Project Title`

**Name of Project: Agda formalization of Lurk**

**Proposal Category:** Choose one of `devtools-libraries`
**Proposer:** `fare`

**(Optional) Technical Sponsor:** `porcuquine`

**Do you agree to open source all work you do on behalf of this RFP and dual-license under MIT or APACHE2 licenses?:** Yes

## Project Description

We propose to develop an Agda Library to formally reason about the execution of Lurk programs. It may be used to prove the properties of particular Lurk programs or to investigate their properties in general.

This proposed formalization is one of several prerequisites to verify the correctness of the compiler directly. The other prerequisites will be a formalization of the underlying zk-SNARK execution model, and a bridge between this high-level semantics of Lurk and that low-level semantics of zk-SNARKs.

This library will embed Lurk code into Agda and allow the writing of formally verified Lurk programs using interactive Agda mode. This result will be easily translatable to other proof assistants based on similar foundations (Coq, Lean)

Our library will enable reasoning about arbitrary Lurk code. However, it will also provide a set of theorems that apply to programs that satisfy various optional restrictions. For instance, we will automatically prove basic properties of well-typed recursive functions that operate only on “data-type” like values, such as termination, absence of runtime errors, necessary predicates about arguments, and predicates about return value.

### Value

Formally verifying smart contracts can prevent dramatic security issues: most of the time, these issues entail the loss of assets entrusted to the smart contracts.

To assure that a smart contract is safe, the possible outcomes of the contract should be checked using mathematical methods to ascertain about two facts:

-   That no undesirable outcome can happen, even if you try to make it happen.
-   That desirable actions are indeed producing the desirable outcome.
   
When successfully implemented, this formal verification library for Lurk will help avoid whole classes of bugs, including among others:  
  
-   the accidental transfer of funds to the wrong wallet,    
-   the failure of a transfer depending on some precondition,
-   transfer of unfair or incorrect amounts between wallets


### Deliverables

The final deliverable, will be a library providing a formalization of Lurk by embedding Lurk into Agda.

The scope of this formalization will cover :
- a representation of Lurk source code.
- a decidable predicate of well scopedness and absence of syntax errors in Lurk programs.
- a representation for the execution traces of Lurk program.
- an evaluator for Lurk expressions.

The functionality of the formal verification library will also include:
- a tool for interactively construct Lurk programs using the Agda interactive mode
- a DSL to express properties of values produced by evaluation


## Development Roadmap

### Initial analysis (2 weeks)
  
We will produce the detailed design of the library, showcasing possible functionalities together with an assessment of the workload necessary to implement them.
    
We are confident that the proposed budget will be sufficient to implement a self contained formalization, but still, we can shift emphasis between features according to the priorities set by the Lurk team.
    
We will consult with the Lurk team and prepare one example of a Lurk program together with its properties that we want to later prove.
    

### Reasoning about the Lurk code (4 weeks)
  
The following tools will be developed to reason about Lurk values so as to express the desired properties of Lurk programs:

- The representation of Lurk Code as S-expressions.

- A DSL for Decidable Predicates over S-expressions.

- Basic predicates about atoms.

- Structural properties (ie. lengths of the list, shape of tree-like structures).

- A system to address subexpressions, allowing to apply predicates to particular subexpressions.

- The decidable property that a particular S-expression represents valid Lurk code - code that would be accepted by the compiler without compile-time errors. (We need to discuss what subset of compiler errors to consider at this stage.)
    
During translation from S-expression-based representation, witnesses of proofs will be embedded into AST, which is more fine-grained and have separate nodes for different Lurk control structures (something like [https://github.com/Glow-Lang/glow2-haskell/blob/9439e74ccf545ecd88b76dce110e30c73f128f14/glow/lib/Glow/Ast/Targets/Lurk.hs#L15](https://github.com/Glow-Lang/glow2-haskell/blob/9439e74ccf545ecd88b76dce110e30c73f128f14/glow/lib/Glow/Ast/Targets/Lurk.hs#L15), but with additional fields to allow decoration of AST with witnesses of desired properties)

### Reasoning about the execution of Lurk (4 weeks)

Representation for the Lurk environment

- Basic predicates about a context (is a symbol in scope? What are known predicates about its value?).

- The implementation of an evaluator for an expression in a given environment.

- The application of the above-developed tools to the example Lurk program specified in the first stage of the project.

- A short video demonstration of the library utility.


## Total Budget Requested
The above plan totals 11 weeks of work, at a cost of $97,500 ($88,000 development costs + $9,500).
Payment for each milestone would be expected half at the beginning and half at the end.

## Maintenance and Upgrade Plans

Maintenance will mainly focus on ensuring that the state of the library matches exactly the constantly evolving Lurk language and Filecoin ecosystem.

While the work proposed for this project will result in an Agda Library suitable for real world applications by experts, MuKn is interested in continuing work to ensure its wider adoption by:
expanding the toolset for writing formally verified proofs about Lurk programs.
creating more examples of verified Lurk programs.
creating a library of verified Lurk snippets
developing a framework to compose them into more complicated Lurk programs, and developing their proofs
producing high quality learning materials and tutorials introducing developers to an effective workflow to develop formally verified Lurk applications.


## Team

### Team Members

-   François-René Rideau, President & Chief Architect
-   Alex Hochberger, CTO
-   Marcin Grzybowski, Formal Methods Lead
-   Paweł Wolak, Junior Developer


### Team Member LinkedIn Profiles


### Team Website

-   [https://mukn.io](https://mukn.io/)

## Relevant Experience

Relevant previous work by our contributors are listed in our Wiki:  
[https://github.com/Glow-lang/glow/wiki/Bibliography-Glow](https://github.com/Glow-lang/glow/wiki/Bibliography-Glow)

Moreover, individual  _Glow_  contributors’ biographies can be found on  
our  [company website](https://mukn.io/our-team/).

## Team code repositories
[https://github.com/Glow-Lang/glow](https://github.com/Glow-Lang/glow)

https://github.com/MuKnIO/glow
Glow language for Safe Decentralized Applications
https://github.com/Glow-Lang/glow2-haskell
WIP retargetable/portable backend for glow, written in Haskell.
https://github.com/Glow-Lang/glow2-haskell/tree/glow-on-lurk-prototype/agda/Glow
WIP formalization of Glow in agda
