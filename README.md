# KeyTau
FOS "Integrated Typing Environment" built in Tauri, Leptos, and a pinch of Solid

<br/>

## Getting Started

> This is a [meta repo](https://github.com/mateodelnorte/meta), you can treat it as a monorepo as long as you prefix your git commands with `meta`. if you are just making changes to 1 sub-repo, you can just use plain git.

### Install
```
npm i -g meta
meta git clone https://github.com/robolab-io/KeyTau.git
```


### Run
1. download rust: https://www.rust-lang.org/
2. Check OS Specific Tauri-Reqs: https://tauri.app/v1/guides/getting-started/prerequisites 
    - Windows requires [VS C++ BuildTools](https://visualstudio.microsoft.com/visual-cpp-build-tools/)
3. $ `npm run tauri dev` (first run takes a bit as to init rust deps)


### DX
1. **vscode git-graph extension:** `ctrl+shift+p` and run `>Git Graph: Add Git Repository...` for each sub-repo. This will let you easily toggle between them.
2. **VSCode Source Control Tab:** click on the three dots for options => Views => Source Control Repositories. This will let you select the sub-repo whose diffs you wish to see.