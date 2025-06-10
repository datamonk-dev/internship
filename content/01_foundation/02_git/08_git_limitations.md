
---

## Where Git Falls Short and What Others Use Instead

Git is widely adopted and incredibly powerful, but it wasn’t designed for every use case. Here are some **real-world challenges companies have faced** using Git — and how they’ve addressed them.

---

### 1. **Git Struggles at Scale (Massive Repositories)**

Git was designed in 2005 for managing the Linux kernel. It works incredibly well for most software projects — especially open-source and web apps.

But as tech companies grew, so did their codebases. Git’s architecture doesn’t scale well when:

* Projects contain **millions of files**
* You need to version **very large binaries**
* Teams have **thousands of developers** working simultaneously

#### Real-World Example: **Facebook**

Facebook found Git too slow for their monorepo — a single massive codebase shared across many teams. Even basic operations like switching branches or checking file history became sluggish.

**Solution**: They built [Sapling](https://engineering.fb.com/2022/11/15/open-source/sapling-source-control-scalable/), a Git-compatible, scalable version control system tailored to fast performance in huge repositories.

> “With Git, some workflows would take over 10 minutes. With Sapling, we brought that down to seconds.”
> — Facebook Engineering

**Alternative Tools**:

* [Sapling](https://sapling-scm.com/) (Meta)
* [Perforce Helix Core](https://www.perforce.com/products/helix-core) (used by Unreal Engine, NVIDIA, and large game studios)

---

### 2. **Git’s Performance with Binary Files and Media Assets**

Git is optimized for code (text), not large binary files like:

* Game textures
* Video files
* Machine learning models
* Design assets (e.g., PSDs)

These files change completely even with small updates, and Git has trouble storing and tracking them efficiently.

#### Real-World Example: **Epic Games / Unreal Engine**

Epic Games and many game developers rely on **Perforce Helix Core**, which is optimized for handling **large binary assets** and provides better file locking and change tracking for art/media workflows.

**Why not Git?**

* Git doesn’t support file locking natively
* Git LFS (Large File Storage) helps, but introduces complexity

**Alternative Tools**:

* Perforce (standard in AAA game development)
* Plastic SCM (popular in Unity-based game dev)

---

### 3. **Access Control and File Locking**

Git assumes everyone has the full repository and can edit anything. This makes **fine-grained permissions** and **file locking** difficult — both of which are often needed in:

* Enterprise environments
* Game development
* Teams working on shared design assets

#### Real-World Example: **NVIDIA**

NVIDIA uses **Perforce** because it offers strict permission control and file locking. Engineers working on firmware can’t afford file conflicts or unauthorized changes — so Git’s open and distributed model doesn’t suit their security requirements.

**Alternative Tools**:

* Perforce (centralized model with access control)
* SVN (Subversion) is also still used in some large orgs with legacy codebases

---

### 4. **Git’s Learning Curve and UX Friction**

Git is flexible — but that comes with **complex commands**, **hidden behavior**, and **sharp edges** for new users. Teams often struggle with:

* Accidental commit loss from `reset` or `rebase`
* Merge conflicts with unclear resolution guidance
* Confusing terminology (`HEAD`, `detached`, etc.)

#### Real-World Example: **Why Some Startups Use Mercurial or JJ**

Some developers prefer Mercurial because it offers simpler commands and clearer workflows. The new Git-compatible tool [JJ](https://jj-vcs.github.io/jj/latest/sapling-comparison/) was created by former Google engineers to “fix” Git's user experience while keeping its power.

> “JJ lets you do Git-style operations with fewer steps and clearer history.”
> — JJ documentation

**Alternative Tools**:

* [Mercurial](https://www.mercurial-scm.org/) — simpler distributed VCS
* [JJ (Just Journaled)](https://github.com/martinvonz/jj) — modern, Git-compatible UX

---

## 🔗 Further Reading

* [Helix Core by Perforce](https://www.perforce.com/products/helix-core)
* [Why Facebook Doesn’t Use Git](https://graphite.dev/blog/why-facebook-doesnt-use-git)
* [Sapling: Source control at Meta scale](https://engineering.fb.com/2022/11/15/open-source/sapling-source-control-scalable/)
* [JJ vs Sapling: A Modern Comparison](https://jj-vcs.github.io/jj/latest/sapling-comparison/)
* [Mercurial SCM](https://www.mercurial-scm.org/)

---
