# HACS 2021 IETF Discussion Topics

## CFRG protocols

Emerging specifications include: HPKE, CPace/OPAQUE, VOPRF, RSA Blind Signatures, hashing to elliptic curves, ristretto255/decaf448

Topics:
- How can we best specify APIs for algorithms and protocols to balance application safety and future extensibility? For example, the VOPRF and VRF standards both depend on hash-to-curve as an internal function, but some (expert) applications may wish to also call these hash-to-curve directly. How do we balance these often-times conflicting concerns?
- Is there a more rigorous way by which we can specify domain separation in algorithms and protocols? TLS 1.3, QUIC, and HPKE all account for domain separation _within_ their respective standards, and algorithms like EdDSA and hash-to-curve accommodate external context or domain separation strings. Criteria for these external domain separation strings, and how they're exposed in APIs, is something we're actively working through. 
- Some emerging standards like HPKE had parallel analysis that supported various design decisions. In contrast, other protocols like CPace, OPAQUE, and VOPRF emerged _after_ security analysis, and the specifications (as currently described) differ in some ways from the original protocol. Often, these specification decisions are made for pragmatic reasons, e.g., to improve performance or admit application extensibility. How can we best plug the gap between security analyses and security specifications? Can we derive models from the specifications directly?

## IETF protocols

Ongoing standardization efforts include: TLS Encrypted ClientHello, MASQUE (QUIC/HTTP proxying), MLS, QUIC Version Negotiation, Oblivious DoH/HTTP, Privacy Pass

Topics:
- Unlike TLS 1.3, analysis of privacy-preserving protocols like ECH, MASQUE, OHTTP, and Privacy Pass is challenging. We need to account for active, malicious attackers and non-cryptographic properties of protocols that might leak sensitive information. Tools like ProVerif provide some useful constructs here, such as indistinguishability between execution traces, but some properties such as unlinkability are difficult to capture. How can we adapt tools to the needs for new analyses?
