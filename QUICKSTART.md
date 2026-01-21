# Quickstart

At the end of the `head` element of `index.html` change this variables in the last script tag:

```js
  // Menu items used to parse data from documentation folder.
  const docPages = ["Basics", "Objects", "Classes", "Utility Types", "../QUICKSTART"];

  // Documentation folder.
  const docRoot = "docs";

  // Branch where pages is deployed.
  const repoBranch = "main";

  // GitHub username.
  const defaultUserName = `jhauga`;
  
  // GitHub repo name.
  const defaultRepoName = `markedPages`;
```

> [!NOTE]
> Use relative path syntax if the file is not in the `docRoot` folder as illustrated above.
