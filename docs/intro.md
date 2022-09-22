---
sidebar_position: 1
---

# Introduction

The Docusaurus sidebar autogenerator normally [checks for category indeces](https://github.com/facebook/docusaurus/blob/6514f0784bd91bdce5d86be5fb1df338089db9d7/packages/docusaurus-plugin-content-docs/src/docs.ts#L432-L442), converting the category into a link if there is nothing but an index in it. It does this by checking if the file is named `"index"`, `"readme"`, or the name of the category itself.

This process fails if the category has a name that contains non-latin characters, e.g. `"æ"`. In that case the file will not be seen as an index (regardless of its name).

This site is a reproduction of the issue. The docs folder consists of two category folders, the only difference between them being the name:

```
docs
 ├─ abc
 │  └─ index.md
 └─ æøå
    └─ index.md
```

As you can see from the sidebar, only one of them is correctly collapsed into a link.
