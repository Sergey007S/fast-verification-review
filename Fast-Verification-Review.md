# Fast Verification Review
## Independent Reproducibility Assessment of the Fast Ecosystem

- **Author:** 0xSergey Research (@Sergey007S)
- **Project:** Fast / FastSet / AllSet (Pi² Labs / @fastxyz)
- **Evaluation Window:** April 2026 – September 2026
- **Scope:** Fast Mainnet (real-funds testing), Fast Explorer, Fast Wallet, Fast App, Fast Sign, public documentation, public repositories, project communications.

---

## Executive Summary

Fast positions itself as a verifiable settlement infrastructure for payments, AI agents, and real-world financial systems.

This review evaluates a narrower question:

Can an independent third party reproduce and verify the system's public verification claims using currently available public artifacts?

During real-funds testing, the system's publicly exposed verification path repeatedly surfaced Verifier Quorum = 0, including inside execution payloads signed by users.

Over five months of testing, explorer analysis, wallet analysis, documentation review, and direct interaction with the system, several verification assumptions were found to be non-reproducible through publicly available evidence.

This review does not claim:
- protocol failure;
- security vulnerabilities;
- fraud;
- inaccurate internal proofs.

Instead, it documents the gap between:
- publicly stated verification claims;
- publicly reproducible verification evidence.

---

## Verification Path Observation

A verification-first system should provide a reproducible path:

`Claim → Evidence → Independent Verification`

Current public state:
- **Claim** → publicly available
- **Evidence** → partially observable
- **Independent Verification** → not publicly reproducible through currently available artifacts

---

## Public Claims in Scope

Observed across official project materials:
- "verifiable by design"
- "cryptographically verified"
- "verifiable finality"
- "Sign a document. Anyone can verify it."

UNTOLD / Rhuna settlement metrics:
- 160,589 operations
- peak 481 TPS
- ~3 ms finality

---

## 1. Verifier Quorum = 0

### Claim
Fast promotes cryptographic verification and verifiable finality.

### Observation
Verifier Quorum = 0 appears:
- in Fast Explorer;
- in Fast Wallet transaction flows;
- inside execution payloads signed by users.

During the seed-phrase wallet flow, transaction authorization occurs in two steps:
1. claim authorization;
2. execution authorization.

The execution payload explicitly displays:
`Verifier Quorum = 0`

#### Screenshot 01
`01-explorer-quorum-zero.png`  
Explorer displaying Verifier Quorum = 0 on External Claims.

#### Screenshot 02
`02-wallet-quorum-zero.png`  
Wallet execution payload displaying Verifier Quorum = 0 before authorization.

### Public Statement
Fast CTO Xiaohong Chen stated:
"Quorum = 0 simply means that no verifier signature is required."

#### Screenshot 11
`11-cto-quorum-zero.png`  
Public CTO explanation of Quorum = 0.

### Open Question
How can an independent observer verify verifier participation when no verifier signatures are required?

---

## 2. Blind Signing

### Observation
The seed-phrase wallet asks users to authorize execution payloads that are not fully presented as human-readable settlement instructions.

Critical settlement details are not consistently exposed in a form that allows independent validation before signing.

#### Screenshot 03
`03-wallet-execution-payload.png`  
Raw execution payload shown during authorization.

### Open Question
How should users independently verify what they are authorizing prior to execution?

---

## 3. Verification Surface Consistency

### Observation
Fast currently exposes two production transaction paths.

#### Fast Wallet (seed phrase)
User can observe:
- execution payloads;
- claim requests;
- verifier quorum information.

#### Screenshot 04
`04-seed-wallet-flow.png`  
Fast wallet recovery flow showing import via recovery phrase or private key.

#### Fast App (Google login)
User can observe:
- simplified transaction actions;
- confirmation interfaces.

Equivalent verification artifacts are not exposed.

#### Screenshot 05
`05-google-app-flow.png`  
Fast App onboarding flow offering passkey and Google-based authentication.

### Assessment
Verification transparency currently depends on the client used rather than on a protocol-level verification interface.

### Open Question
Why do two production clients expose different verification surfaces for the same settlement network?

---

## 4. Private Production Wallet

### Observation
Public GitHub documentation associated with Fast wallet audit assets states that production wallet repositories are private.

The referenced documentation explicitly mentions:
`fast-wallet (production)`  
as a private repository.

#### Screenshot 06
`06-private-wallet-repo.png`  
README referencing private production wallet repositories.

### Open Question
What public artifacts allow independent review of:
- signing logic;
- transaction construction;
- key handling;
- claim generation?

---

## 5. Fast Sign

### Claim
"Sign a document. Anyone can verify it."

### Observation
Fast Sign successfully proves:
- a document hash existed;
- before a given block.

That establishes proof of existence.

It does not independently establish:
- settlement validity;
- consensus validity;
- verifier participation;
- protocol correctness.

#### Screenshot 07
`07-fast-sign-anyone-can-verify.png`  
Fast Sign interface and verification workflow.

### Assessment
Proof of existence and proof of system verification are distinct properties.

### Open Question
Where does proof of existence end and system verification begin?

---

## 6. Explorer Telemetry

### Observation

#### External Claims
Repeated claims where:  
`sender = recipient`  
were observable in the public transaction stream.

#### Screenshot 08
`08-external-claim-from-to.png`  
External Claims with identical sender and recipient.

#### Volume Metrics
The explorer simultaneously displayed:
- Total Transactions = 25.8M
- TXs 24H = 25.8M

#### Throughput Metrics
Peak TPS = 481 was displayed on the explorer and independently referenced in the UNTOLD announcement.

#### Screenshot 09
`09-total-vs-24h.png`  
Explorer metrics showing Total Transactions, TXs 24H and Peak TPS.

### Open Question
What public methodology allows independent reproduction of:
- volume metrics;
- TPS metrics;
- finality metrics?

---

## 7. AllSet Asset Parity and Settlement Claims
Claim

Fast publicly describes AllSet as:

a universal liquidity hub;
bridgeless settlement;
true asset parity;
a unified USDC balance across supported chains;
approximately 0.25 ms settlement.
Observation

The public announcement does not provide:

settlement datasets;
asset parity validation datasets;
reproducible settlement procedures;
independent verification instructions;
benchmark artifacts supporting the reported figures.

As a result, an external researcher cannot independently reproduce or validate:

bridgeless settlement behavior;
asset parity guarantees;
cross-chain balance consistency;
reported settlement latency.

Screenshot 12

12-allset-asset-parity-claims.png

AllSet announcement describing bridgeless settlement, asset parity, and cross-chain USDC balance functionality.

Open Question

What public artifacts allow an external researcher to independently verify:

bridgeless settlement;
true asset parity;
cross-chain balance consistency;
the reported ~0.25 ms settlement claim?

---

## 8. UNTOLD / Rhuna Settlement Pilot

### Claim
Fast reported:
- 160,589 operations;
- peak 481 TPS;
- ~3 ms finality;
- zero failures.

### Observation
The public announcement does not provide:
- transaction datasets;
- claim datasets;
- verification procedures;
- reproducible benchmark artifacts

allowing independent validation of the published figures.

#### Screenshot 10
`10-untold-announcement.png`  
UNTOLD / Rhuna settlement announcement and CLI graphic.

### Open Question
What public artifacts allow an external researcher to independently reproduce the reported settlement metrics?

---

## Real-Funds Testing Scope

The following activities were performed directly on Fast Mainnet using real assets:
- Base → Fast deposits;
- internal asset transfers;
- wallet authorization flows;
- execution payload inspection;
- Fast App transaction flows;
- withdrawal testing.

Protocol correctness itself is outside the scope of this review.

The scope is public reproducibility.

---

## Timeline of Engagement

- **21 May 2026:** Initial contact established with Roberto Rosmaninho.
- **26 May 2026:** Observation #1 regarding signing transparency submitted.
- **June–July 2026:** Follow-up questions regarding Quorum = 0 and verification reproducibility.
- **August 2026:** Production wallet repository disclosures reviewed.
- **September 2026:** Fast Sign and UNTOLD verification claims evaluated against publicly available artifacts.

---

## Required Public Artifacts

### 1. Quorum Specification
Formal explanation of the security model when:  
`Verifier Quorum = 0`

### 2. Independent Verification Path
A reproducible method allowing any third party to verify an accepted claim without relying on Fast-operated interfaces.

### 3. Production Wallet Auditability
Public source code or equivalent audit artifacts for production wallet behavior.

### 4. Explorer Methodology
Public definitions for:
- TPS
- finality
- transaction counters
- volume metrics

### 5. Settlement Reproduction
A reproducible verification dataset for the UNTOLD / Rhuna settlement figures.

---

## Conclusion

This review does not evaluate whether Fast is internally correct.

Internal correctness is outside the scope.

Instead, it evaluates whether public verification claims can be independently reproduced by external parties.

The central observation remains:

Fast publicly promotes verification-first infrastructure while several critical verification assumptions remain unavailable for independent reproduction through currently available public artifacts.

Verification claims become significantly stronger when they can be independently reproduced by parties outside the operator trust boundary.
