---
{"dg-publish":true,"permalink":"/monorepos/","tags":["dev"]}
---

The following points are in contrast to what I consider to be 'ordinary' or 'natural' usage of repos in which one repo roughly corresponds to one *deployable*.
- Monorepos have easier code-sharing but breaking changes in common code must all be resolved at once.
- Commit messages are more verbose and have higher cognitive load because you need to express the scope of the changes as well as the changes themselves.
- Searching has worse signal to noise ratio in monorepos. When you search for the thing you are looking for you may have to mentally filter out many results which are irrelevant to your current task.