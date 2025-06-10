
---

We’ll create a tiny project with two files and one folder and walk through Git internals. That how everything looks like under the hood.

---

## Step-by-Step Walkthrough

### Step 0: Setup

```bash
mkdir internals
cd internals
git init
```

Now we have an empty Git repository.

---

### Step 1: Create Files

```bash
echo "I am Iron Man" > marvel.txt
mkdir docs
echo "jarvis is alive" > docs/secret.txt
```

Your directory structure now looks like:

```
internals/
├── marvel.txt
└── docs/
    └── jarvis.txt
```

---

### Step 2: Stage the Files

```bash
git add .
```

### Step 3: Inspect the Objects Git Created

Let’s now look at the **blob hashes** (file content objects):

```bash
git hash-object marvel.txt
# e.g., => e69de29bb2d1d6434b8b29ae775ad8c2e48c5391

git hash-object docs/jarvis.txt
# e.g., => 9daeafb9864cf43055ae93beb0afd6c7d144bfa4
```

You can also view file content using this hash
```bash
git cat-file -p 9daeafb9864cf43055ae93beb0afd6c7d144bfa4
```

These are **blobs**, the raw contents of your files, compressed and stored in `.git/objects`.

---

### Step 4: Create a Tree (index snapshot)

When you commit, Git takes a snapshot of the directory (the *tree*):

```bash
git commit -m "Initial commit"
```

To see the commit hash:

```bash
git log --oneline
# e.g., 6a1f0c1 Initial commit
```

---

### Step 5: Explore the Commit Internals

#### Get the commit’s tree:

```bash
git cat-file -p 6a1f0c1
```

Output:

```
tree 35e3fcb6e7...
author You <groot@iam.com> ...
...
```

That `tree` hash represents the root of your project.

---

### Step 6: Inspect the Tree

```bash
git cat-file -p 35e3fcb6e7...
```

Example output:

```
100644 blob e69de29bb2...    hello.txt
040000 tree 1f3b0c55...      docs
```

* `blob` is the file
* `tree` is the subdirectory (`docs`)

Now inspect the `docs` sub-tree:

```bash
git cat-file -p 1f3b0c55...
```

Output:

```
100644 blob 9daeafb986...    guide.txt
```

Boom — this is how Git recursively nests trees.

---

## Summary: What Happens on `git checkout`

When you do:

```bash
git checkout main
```

Git internally:

1. **Finds the latest commit hash** of `main`
2. **Finds the tree** associated with that commit
3. Recursively:

   * Reads tree → gets file and folder names and their hashes
   * Folders (subtrees) are traversed the same way
4. **Decrypts the blob objects** (using their hash)
5. **Writes the files back** to the working directory

---

## Bonus: View All Objects Git Created

```bash
git rev-list --objects --all
```

You’ll see a list of all commits, trees, blobs — and their hashes.

---

## Visual Recap

```
Commit (points to a Tree)
│
└── Tree (root)
    ├── hello.txt → blob (file content)
    └── docs/ → Tree
        └── guide.txt → blob
```

---

