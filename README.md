# HACS 2021 IETF Discussion Topics

## General

- How can or should the CFRG and dependent working groups in the IETF (TLS, Privacy Pass, QUIC, MASQUE) change process for better alignment and transparency with researchers?
- Do you think providing APIs in standards is important and why? If so, what Syntax/DSL/Language could be used in informal specifications such as an IETF standard?
- What are the benefits/issues with having APIs hiding random number generation internally? What about masking? (those ones might have a clearer answer).
- How can protocols or standards be developed to maximize reuse of existing analysis efforts? (Reuse the TLS key schedule everywhere? Build on a common HPKE interface for public key encryption?)
- How do we account for divergence between formal analysis efforts and technical specifications? (e.g. TLS 1.3 and OPTLS)
- Emerging primitives and protocols that need assurance: CPace/OPAQUE, VOPRF, (RSA) blind signatures, TLS Encrypted ClientHello, MASQUE (QUIC/HTTP proxying), QUIC, Oblivious DoH/HTTP, Privacy Pass, Key-committing AEADs

## CFRG specific protocols

Emerging specifications include: HPKE, CPace/OPAQUE, VOPRF, RSA Blind Signatures, hashing to elliptic curves, ristretto255/decaf448

Topics:
- How can we best specify APIs for algorithms and protocols to balance application safety and future extensibility? For example, the VOPRF and VRF standards both depend on hash-to-curve as an internal function, but some (expert) applications may wish to also call these hash-to-curve directly. How do we balance these often-times conflicting concerns?

BB. Both questions cannot be answered, simply because APIs are a question of taste and use-cases.
-- Do you think providing APIs in standards is important and why? If so, what Syntax/DSL/Language
could be used in informal specifications such as an IETF standard?
-- What are the benefits/issues with having APIs hiding random number generation internally?
What about masking? (those ones might have a clearer answer). 

- Is there a more rigorous way by which we can specify domain separation in algorithms and protocols? TLS 1.3, QUIC, and HPKE all account for domain separation _within_ their respective standards, and algorithms like EdDSA and hash-to-curve accommodate external context or domain separation strings. Criteria for these external domain separation strings, and how they're exposed in APIs, is something we're actively working through.

BB. This is not very interesting and the answer is obvious: since there is a need for a global
naming scheme, who should dictate rules? Answer: the standardization body!

- Some emerging standards like HPKE had parallel analysis that supported various design decisions. In contrast, other protocols like CPace, OPAQUE, and VOPRF emerged _after_ security analysis, and the specifications (as currently described) differ in some ways from the original protocol. Often, these specification decisions are made for pragmatic reasons, e.g., to improve performance or admit application extensibility. How can we best plug the gap between security analyses and security specifications? Can we derive models from the specifications directly?

BB. Nothing to be answered here, it has been known by all people from formal methods
for several decades: use a formal language. Can we derive models? The answer is also no
because of the informal specifications.
-- This loops back to the syntax/DSL/Language question but for formal descriptions
instead of APIs.

BB. The main problem is that most people in academia either don't know about CFRG or
think CFRG is garbage because of the way it handles new primitives.
-- It would be more helpful to find out how people think CFRG should change its process
and what would be useful for academia to be more involved.

## IETF specific protocols

Ongoing standardization efforts include: TLS Encrypted ClientHello, MASQUE (QUIC/HTTP proxying), MLS, QUIC Version Negotiation, Oblivious DoH/HTTP, Privacy Pass

Topics:
- Unlike TLS 1.3, analysis of privacy-preserving protocols like ECH, MASQUE, OHTTP, and Privacy Pass is challenging. We need to account for active, malicious attackers and non-cryptographic properties of protocols that might leak sensitive information. Tools like ProVerif provide some useful constructs here, such as indistinguishability between execution traces, but some properties such as unlinkability are difficult to capture. How can we adapt tools to the needs for new analyses?

BB. This question asks for specific questions, about specific tools, to model specific properties that
only the tool owners are able to answer. I don't think those protocols are more challenging to model,
they are just less studied. People are more oriented towards primitives in this group, so I think focusing
on process and primitives is a better idea than focusing on protocols which can have its own sessions.
