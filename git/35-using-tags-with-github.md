# Using tags with GithHub

When using github, you can use tags to version your code, when done, push it to Github and it will show up on the releases section.

```
git push origin v-0.9-beta
```

To push all tags:

```
git push origin master --tags
```

To delete tag:

```
git push origin :v-0.9-beta
```

