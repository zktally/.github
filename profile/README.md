## ZKTally

Privacy-preserving, anonymously verifiable e-voting from linkable ring signatures, Paillier
homomorphic encryption, and NIZK vote-correctness proofs.

> **Unaudited academic software implementing a protocol from a student research paper. It has
> not been reviewed by professional cryptographers and must not be used for any binding
> election.**

A ballot is three things travelling together: an encrypted vote, a proof that the vote is legal,
and a ring signature proving the caster is on the roll. Tallying multiplies the ciphertexts and
decrypts only the total, so no individual ballot is ever opened — and a deterministic key image
still makes a second ballot from the same key detectable.

### Repositories

| | |
|---|---|
| [**ZKTally**](https://github.com/ZKTally/ZKTally) | Python reference implementation and the `zktally` command line |
| [**zktally-js**](https://github.com/zktally/zktally-js) | TypeScript port for the browser and Node — wire-compatible with the reference |
| [**zktally.github.io**](https://github.com/zktally/zktally.github.io) | Interactive explainer that runs a real election in your browser |
| [**paper**](https://github.com/ZKTally/paper) | The protocol paper |

Both implementations share one wire format and one corpus of test vectors, and each is tested
against boards the other produced. A ballot cast in the browser verifies in Python.

### What it gives you, and what it does not

Ballot secrecy, voter anonymity within the ring, double-vote prevention, ballot-stuffing
resistance, and public verifiability of every ballot. Under threshold mode the tally itself is
verifiable too.

It is **not** receipt-free — the voter holds the encryption randomness, which reconstructs their
ciphertext — and it offers no coercion resistance, no bulletin-board authentication, and no
side-channel or post-quantum protection. Each project's README states its limitations in full,
because a demonstration that only lists its strengths is advertising.
