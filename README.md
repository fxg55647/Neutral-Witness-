NEUTRAL WITNESS & AI FLIGHT RECORDER -
An Accountability Infrastructure for Claims in Agent and Human Systems
================

PROBLEM
-------
Autonomous AI agents and AI-assisted decision systems increasingly participate 
in economically and legally meaningful processes. However, current 
infrastructures lack a reliable mechanism to establish accountability for 
claims: it is often unclear what was claimed, on what evidence, under which 
constraints, and why the claim was considered acceptable at the time.

Existing approaches emphasize reliability, observability, or post-hoc 
explanation, but they do not provide a shared, auditable basis for attributing 
responsibility. As a result, high-value processes remain slow, manual, or 
confined to sandboxed automation, and failures are frequently dismissed as 
"AI errors" without clear attribution.


CORE CONCEPT
------------
This work introduces a claim-centric accountability layer composed of two 
inseparable components:

  - Neutral Witness
  - AI Flight Recorder

Together, they enable systems to evaluate and persistently record claim 
admissibility: whether a claim exceeded the evidence available under declared 
constraints at a specific moment in time.

The framework applies equally to:
  - agent-to-agent interactions
  - human-initiated evaluations via user interfaces
  - hybrid workflows combining both


NEUTRAL WITNESS
---------------

Definition:
  The Neutral Witness is an independent evaluation process that assesses 
  whether a claim is admissible relative to available evidence, uncertainty, 
  and declared constraints, without determining objective truth.

Key Properties:
  - Claim-first evaluation (not action- or model-centric)
  - External to the claiming agent or user
  - Supports multi-model evaluation and disagreement analysis
  - Produces bounded, non-leaking outputs
  - Can evaluate claims derived from confidential evidence

Role:
  - Prevents overclaiming
  - Converts uncertainty into an explicit signal
  - Enables trust in process rather than in agents or parties
  - Helps disrupt the underlying mechanism that produces hallucinations

Evaluation Model: Triple Stateless Claim Evaluation
The Neutral Witness evaluates claim admissibility using a triple-stage, stateless evaluation model. The same bounded inputs (claim, evidence boundary, constraints) are assessed from an affirmative frame (does the claim hold?), a negating frame (where does it exceed evidence?), and a final consistency comparison that measures epistemic stability rather than correctness.
Each stage is memoryless and isolated, preventing narrative coherence bias and silent assumption propagation. Disagreement between stages is treated as a first-class signal of epistemic weakness and is recorded as part of the accountability trail.

Confidential Evaluation and Dual-Party Inputs:
  A key capability of the Neutral Witness is the ability to evaluate claims 
  using multiple sets of confidential inputs simultaneously, supplied by 
  mutually distrustful parties.

  Examples:
  - due diligence between companies
  - IP or patent comparisons  
  - financial compatibility assessments
  - compliance checks

  Each party provides private data to the witness. The witness evaluates 
  compatibility or admissibility and returns only an allowed conclusion 
  (e.g. compatible / incompatible / uncertain), without revealing either 
  party's underlying information.

  This enables proof without disclosure and removes the need for full 
  transparency or document exchange.

  The availability of an easily accessible, neutral, and auditable intermediary would alter fundamental assumptions in game-theoretic interactions, enabling classes of cooperation and market structures that are currently impractical.

Trusted Execution Environment (Optional but Natural Extension):
  The Neutral Witness can operate inside a Trusted Execution Environment (TEE), 
  providing hardware-backed guarantees that:
  - confidential inputs are not accessible to operators or other processes
  - evaluation logic is fixed and attestable
  - outputs are constrained and verifiable

  TEE execution strengthens institutional trust and enables deployment in 
  contexts requiring high assurance (finance, government, IP-sensitive 
  negotiations).


AI FLIGHT RECORDER
------------------

Definition:
  The AI Flight Recorder is a persistent, append-only, tamper-evident record 
  that captures why a claim or decision was considered admissible at a 
  specific time.

Recorded Elements May Include:
  - the claim
  - evidence boundaries
  - applied constraints and policies
  - model disagreement signals
  - review steps (self or external)
  - cryptographic hashes of underlying inputs
  - timestamps and attestations (including TEE attestation, if used)
  - links to other claims (dependencies and supporting evidence)
  - witness evaluation result OR explicit bypass decision

Purpose:
  - Enables post-hoc responsibility attribution
  - Distinguishes negligence, falsified input, and good-faith error
  - Prevents plausible deniability ("AI did it")
  - Supports forensic, audit, and legal analysis
  - Traces reasoning chains across multiple claims


CLAIM CHAINS AND DEPENDENCIES
------------------------------
The AI Flight Recorder not only stores individual claims but links claims 
together, forming auditable reasoning chains.

Key Capabilities:
  - Claims can reference other claims as supporting evidence
  - Dependency graphs show how conclusions build on prior assessments
  - When a foundational claim is disputed, all dependent claims are 
    automatically flagged
  - Enables tracing failures back to their epistemic root cause
  - Supports composite agents that build on each other's work

Example Chain:
  Claim A: "Supplier X is financially stable"
  
    -> links to evidence 
           E1, E2
           
    -> evaluated by Neutral Witness at T1

  Claim B: "Contract with X is low-risk"
  
    -> depends on Claim A
           
    -> links to additional evidence E3
           
    -> evaluated at T2

  Claim C: "Approve $5M purchase from X"
  
    -> depends on Claim B
           
    -> links to policy P1
           
    -> evaluated at T3


FLEXIBLE ENFORCEMENT AND ECONOMIC BYPASS
-----------------------------------------
The framework does not require that every claim pass through the Neutral 
Witness.

In practice:
  - trusted agents or users may bypass witness evaluation
  - claims can be accepted with economic stake or collateral
  - witness evaluation can occur:
      - periodically
      - randomly
      - or conditionally (e.g. on dispute)

Accountability Through Choice:
  Crucially, choosing not to use the Neutral Witness is itself an explicit 
  assumption of responsibility, and this decision is recorded in the 
  flight recorder.

  The record captures:
  - that witness evaluation was available but not used
  - who made the bypass decision (agent or human)
  - timestamp and context of the decision
  - any stated justification

  In effect: you can choose speed over verification, but you cannot 
  choose speed over accountability.


NETWORK EFFECTS AND CROSS-VERIFICATION
---------------------------------------
As adoption grows, the system enables emergent network effects:
  - claims and attestations accumulate across organizations
  - repeated interactions form cross-verifiable histories
  - claim chains can span organizational boundaries
  - especially valuable in environments with weak institutions


REPUTATION AS A LAYER, NOT A PREREQUISITE
------------------------------------------
The framework deliberately separates accountability from reputation.

However, the flight recorder enables reputation systems to be built on top:
  - reputation derives from historical admissibility
  - based on documented behavior, not assertions
  - can incorporate claim chain quality (not just individual claims)
  - can factor in bypass patterns and outcomes


WHAT IS NEW
-----------
This work introduces, in combination:
  - Claims as first-class accountability objects
  - Admissibility instead of pursuing perfect correctness
  - Confidential multi-party evaluation
  - External, multi-model reality checking with triple stateless claim evaluation 
  - Epistemic flight recording with claim linking
  - Auditable reasoning chains across agents and time
  - Optional hardware-backed trust (TEE)
  - Economic enforcement without mandatory verification
  - Accountability for the choice not to verify


PRACTICAL IMPACT
----------------

Enables:
  - production deployment of autonomous agents in accountability-critical environments
  - significant reduction of operationally harmful hallucinations and overclaims
  - continuous and confidential due diligence
  - faster debugging and safer iteration
  - agent-to-agent and human-agent commerce
  - accountable AI use in weak-institution contexts
  - composite agent systems with traceable reasoning
  - systematic root cause analysis of failures
  - deliberate risk-taking with clear attribution

Does Not:
  - guarantee correctness
  - prevent all fraud
  - replace law or human judgment
  - impose a single source of truth


ONE-SENTENCE SUMMARY
--------------------
An infrastructure that mitigates AI hallucinations by subjecting every claim to independent evidence-based verification and capturing the entire reasoning chain into a tamper-evident flight recorder.

CONTACT
--------------------
Author: Teemu Lantta

Email: teemun.geemeili@gmail.com 

X: @TeemuLantta

