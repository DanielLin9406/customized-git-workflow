# Customized Git Workflow

## Situation

- Feature development is one per feature.
- Some features had been developed but never going live until the idea has beddn aproved by marketing team member.
- Website needs to be updated as fast as possible.

## Git flow preview

![git flow preview](https://i.imgur.com/PJBYlzG.png)

## Idea

- Always start with checkouting a new branch from master.
- Prod. branch is refered to official website
- Stage branch is refered to stage website for team member review before go live.
- Before merge feaute into stage/prod, must run rebase prod first.

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

- Never ever directly merge stage into prod.
- Always merge feature into stage in order to preserve other features which has been merged into stage but not on live.
- Stage is a temp branch
- If you want to update remote existing feature branch after local feature branch has been rebased to prod, you may bump into an error. You may want to use replace remote branch with your local feature branch. Please run:

```bash
git push --force origin feature
```

Ref.:
Git push rejected after feature branch rebase - Stack Overflow
