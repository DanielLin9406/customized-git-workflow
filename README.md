# Customized Git Workflow

## Situation

- Every feature should have their own developing branch.
- Some features had been developed but not going live soon until the idea has been approved by marketing team member.
- Website needs to be updated and deployed as fast as possible.

## Git flow preview

![git flow preview](https://i.imgur.com/PJBYlzG.png)

## Legend

- Prod. branch refers to official website.
- Stage branch refers to stage website for for reviewing purposes by other team members.

## Idea

- First step is always checkout a new branch from master.
- Run `git rebase prod-branch` before merging feature branch into stage branch or prod. branch.
- Don't directly merge stage branch into prod. branch.
- You can treat stage branch as a pre-prod. branch, but one thing you should be noticed that not all features which has been merged into stage are becoming part of our official release.

## SOP

### Merge feature to stage

When I develop a feature on branch `feature`

#### 1. Rebase prod first

```bash
git checkout feature
git rebase prod
```

#### 2. Checkout stage and run merge

```bash
git checkout stage
git merge feature
```

### Merge feature to prod

When I develop a feature on branch `feature`

#### 1. Rebase prod first

```bash
git checkout feature
git rebase prod
```

#### 2. Checkout stage and run merge

```bash
git checkout prod
git merge feature
```

## Note

- If you want to update remote existing feature branch after local feature branch has been rebased to prod, you may bump into an error. You may want to use replace remote branch with your local feature branch. Please run:

```bash
git push --force origin feature
```

Ref.:
Git push rejected after feature branch rebase - Stack Overflow
