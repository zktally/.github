<div align="center">

<img src="assets/logo.png" alt="ZKTally logo" width="100%">

# 🗳️ ZKTally

**Verifiable voting you can watch happen**

Privacy-preserving, anonymously verifiable e-voting from linkable ring signatures, Paillier homomorphic encryption, and NIZK vote-correctness proofs.

[![Live App](https://img.shields.io/badge/Live_App-zktally.github.io-2ea44f?style=for-the-badge&logo=googlechrome&logoColor=white)](https://zktally.github.io)
[![PyPI](https://img.shields.io/badge/PyPI-zktally-3775A9?style=for-the-badge&logo=pypi&logoColor=white)](https://pypi.org/project/zktally/)
[![npm](https://img.shields.io/badge/npm-zktally-CB3837?style=for-the-badge&logo=npm&logoColor=white)](https://www.npmjs.com/package/zktally)
[![Demo](https://img.shields.io/badge/Demo-Google_Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/18PG6BfO_0gDqTDWKuW_G36TPddnxkfjP/preview)

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Vue](https://img.shields.io/badge/Vue-3-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-Build-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)

</div>

---

## 🎬 Demo

<div align="center">
  <a href="https://drive.google.com/file/d/18PG6BfO_0gDqTDWKuW_G36TPddnxkfjP/preview">
    <img src="assets/zktally.webp" alt="ZKTally demo" width="100%">
  </a>
  <br>
  <sub>▶ Click to watch the full demo on Google Drive</sub>
</div>

---

## 🔍 What is ZKTally?

**ZKTally** is an e-voting protocol in which no one ever opens an individual ballot, yet anyone
can check the count. A ballot is three things travelling together: an encrypted vote, a proof that
the vote is legal, and a ring signature proving the caster is on the roll. Tallying multiplies the
ciphertexts and decrypts only the total, and a deterministic key image still makes a second ballot
from the same key detectable.

The protocol ships as a Python reference implementation with a `zktally` command line, a
wire-compatible TypeScript port for the browser and Node, and an interactive explainer that runs a
real election in your browser. Both implementations share one wire format (`zktally/1`) and one
corpus of test vectors, so a ballot cast in the browser verifies in Python. ZKTally is
**unaudited academic software** and must not be used for any binding election.

### 🎯 Built for

ZKTally was built for the **II4021-24 Cryptography** course at **STEI ITB**.

---

## ❓ Problem → 💡 Solution

| ❓ Problem | 💡 How ZKTally solves it |
|---|---|
| **Secret ballots hide the count** — if no one may see a vote, there is nothing for voters to check the result against. | **Homomorphic tallying** — Paillier ciphertexts are multiplied into one number and only that aggregate is decrypted, so the total is computed without opening a single ballot. |
| **An encrypted vote can be anything** — a ciphertext of 7 instead of 0 or 1 would add seven votes at once, and nobody can see it. | **NIZK OR-proofs** — every ballot proves its plaintext is a legal vote (binary, or exactly one of *k*) without revealing which. |
| **Anonymity invites double voting** — if the signer is hidden, a voter could cast twice unnoticed. | **Linkable ring signatures** — the caster proves they are *some* registered voter, and the deterministic key image flags any second ballot from the same key. |
| **Verification usually means trusting the authority** — the auditor needs the keys the auditor is meant to check. | **Secret-free audit** — `zktally audit` re-verifies every ballot and partial decryption from public data alone; threshold mode makes the tally itself verifiable. |

---

## 📸 Screenshots

<table>
<tr>
<td width="50%" align="center"><b>Landing — verifiable voting you can watch</b><br><br><img src="assets/screenshots/1.webp" alt="ZKTally landing page with the headline 'Verifiable voting you can watch happen' and the unaudited-software disclaimer" width="100%"></td>
<td width="50%" align="center"><b>Walkthrough — setting up the Paillier key</b><br><br><img src="assets/screenshots/2.webp" alt="Step 1 of 6 of the walkthrough showing the 2048-bit public modulus and the election context digest" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Election sandbox — setup</b><br><br><img src="assets/screenshots/3.webp" alt="Election sandbox form with a yes/no question, voter count slider and key size selector" width="100%"></td>
<td width="50%" align="center"><b>Election created — ring hash and authority warning</b><br><br><img src="assets/screenshots/4.webp" alt="Created election showing 12 voters, a 2048-bit key, the ring hash and a single-authority warning" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Every voter cast a ballot</b><br><br><img src="assets/screenshots/5.webp" alt="Grid of twelve voters all marked as voted, with buttons to inspect the board, count the votes and export JSON" width="100%"></td>
<td width="50%" align="center"><b>Adversary mode — six attacks, all rejected</b><br><br><img src="assets/screenshots/6.webp" alt="Adversary mode cards for double voting, forged key image, own ring, poisoned tally, copied vote and out-of-range vote, each rejected" width="100%"></td>
</tr>
<tr>
<td width="50%" align="center"><b>Result — tally and rejected ballots</b><br><br><img src="assets/screenshots/7.webp" alt="Result page with 8 yes and 4 no votes and a list of five rejected ballots with their reasons" width="100%"></td>
<td width="50%" align="center"><b>Verify a board — paste any board JSON</b><br><br><img src="assets/screenshots/8.webp" alt="Verify a board page with a board JSON editor and a summary of 17 ballots, 12 accepted and 5 rejected" width="100%"></td>
</tr>
</table>

---

## 📦 Repositories

| Repository | Description | Tech Stack | Deployment |
|---|---|---|---|
| [**ZKTally**](https://github.com/ZKTally/ZKTally) | Python reference implementation and the `zktally` command line. | Python · Paillier · LSAG · secp256k1 · gmpy2 | [PyPI](https://pypi.org/project/zktally/) |
| [**zktally-js**](https://github.com/zktally/zktally-js) | TypeScript port for the browser and Node, wire-compatible with the reference. | TypeScript · @noble/curves · @noble/hashes · Web Workers · Vitest | [npm](https://www.npmjs.com/package/zktally) |
| [**zktally.github.io**](https://github.com/zktally/zktally.github.io) | Interactive explainer that runs a real election in your browser. | Vue 3 · Vite · Tailwind CSS · Pinia · Playwright | [zktally.github.io](https://zktally.github.io) |
| [**paper**](https://github.com/ZKTally/paper) | The protocol paper. | LaTeX | — |
| [**.github**](https://github.com/zktally/.github) | This organization profile and its assets. | Markdown | — |

---

<div align="center">
<sub>© 2025 Faiz Atharrahman</sub>
</div>
