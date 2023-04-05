# KeyTau
FOS "Integrated Typing Environment" built in Tauri, Leptos, and a pinch of Solid

<br/>

## Getting Started

> This is a [meta-repo](https://github.com/mateodelnorte/meta), you can treat it as a monorepo as long as you prefix your git commands with `meta`. if you are just making changes to 1 sub-repo, you can just use plain git.

### Install
```
npm i -g meta
meta git clone https://github.com/robolab-io/KeyTau.git
```


### Run
1. download rust: https://www.rust-lang.org/
2. Check OS Specific Tauri-Reqs: https://tauri.app/v1/guides/getting-started/prerequisites 
    - Windows requires [VS C++ BuildTools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
3. $ `npm run tauri dev` or `npm run tauri build` (first run takes a bit as to init rust deps)


### DX
1. **vscode git-graph extension:** `ctrl+shift+p` and run `>Git Graph: Add Git Repository...` for each sub-repo. This will let you easily toggle between them.
2. **VSCode Source Control Tab:** click on the three dots for options => Views => Source Control Repositories. This will let you select the sub-repo whose diffs you wish to see.
3. **Release Shortcut:** the release is kinda buried so a shortcut/alias helps for quick access. I've added mine to a top level `build` directory, which is gitingore'd. example paths:
   - `...\KeyTau\src-tauri\target\release\KeyTau.exe`
   - `...\KeyTau\src-tauri\target\release\bundle\msi`
   - Might be possible to change the tauri release output dir, but that can wait.


## Contributing

<br/>

Once you are ready to commit, heres the rule of thumb:
> If changes affect multiple repos (check `meta git status` or vscode source control tab), then `meta commit`. If it affects 1 repo, it doesn't matter which method you use as empty commits will be ignored (I think).
> 
> In the event a change to a single repo affects the functionality of other repos, you might wish to indicate so by allowing an empty commit there as well:
>
> `meta commit --allow-empty -m "commit message" --include-only dir1,dir2`

<br/>

### Commit Formatting

https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13

https://www.conventionalcommits.org/en/v1.0.0/

<details>
<summary>Types:</summary>

```
Feat
  - Functional Update

Style
  - non-functional style update

Fix
  - Functional fix

Chore
  - cleaning, formatting, notes, other non-functional updates and maintenance

Docs
  - updating documentation

Ref
  - refactor, rewrites, code splitting, restructuring, etc.

Trial
  - an experiment that may or may not work

Checkpoint
  - potentially non-functional commit, mid-feature

Init
  - instantiating a dep or dev-ops feature

Util
  - Developer Utility/tooling/build-pipeline feature/update

Test
  - code testing updates
```

</details><br/>

<details>
<summary>Scopes:</summary>

```
meta
  - Affects multiple repos

sr
  - Affects single repo
```

</details><br/>

<details open>
<summary>Examples:</summary>

```
Feat(meta): implement & connect some tauri api to FE
Docs(sr): fix spelling on single repo's docs

Fix(meta): only backend code changed but has significant functional on FE
^--allow-empty
```

</details><br/>


### Branching

```
master/
  - feat/ (pre-release feature, just lazy, unrelated to immediate dev-branch goal, or a long-lived refactor/feat with unknown delivery time)
  - fix/  (hot-fix)
  - dev/vX.Y.Z (keeps master unblocked for prod hot-fixes)
    - feat/ (short lived branches usually outlined by the dev branches goals)
    - fix/ (dev fix)
```

PR's will likely be squash-merged

<br/>

## Why Use a Meta-Repo?
<br/>


**Pros:**

As an open-source project, low barrier to entry and ease of customization are big priorities. A meta-repo accomplishes this in a few ways:
1. Its possible to swap out whole client or other parts with a single line via the `.meta` file. It does not require a mass diff like in a monorepo.
2. There are no knew concepts or opinions, repos and git commands as usual, just with an iterative utility.
3. Separation of concern - commits, features, issues, changes, and scope are inherently organized. This makes it easier to identify areas of relevance and onboard devs.

Furthermore, meta is an non-opinionated, agnostic tool. The skill you build using this can be utilized in most any project.


<br/>

**Cons:** 
- PR's are a tad redundant (I consider this more of a github UI issue than anything). There is however a [plugin](https://github.com/mateodelnorte/meta-gh) to alleviate these issues.
- Inability to view all git-graphs and changes at once. This is more of a trade off than a con. Also, I only use [VS-Code Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph), other git-guis may have tools to do so. Worst case scenario I can throw together a quick tool myself.
- A tad slow, could use a rust rewrite 🦀🚀
- Not as much DX support as monorepos

Most of these cons are solvable issues, just lacking due to the monorepo dogma.

<br/>

**Comparison:**

Most monorepo alternatives - lerna, pnpm, turborepo, all have a strong JS/TS bias. Turborepo also has a very cool caching strategy, but as developers who routinely updates code, caching doesn't really do much for us.

Most importantly, these are highly opinionated tools that come with conceptual overhead or lock-in. Meta-repos on the other hand, just use basic commands iteratively on plain git repos.
