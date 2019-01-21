## History

In order to see the git commit history, you can use command:

```
git log
```

```
commit aa6daef8b82dddc6fd98f253b0ead79d9980421d (HEAD -> master)
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:53:09 2019 +0200

    moved file

commit a6a2066dc8ce8206f995f89c5cc5a36febf230dc
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:51:07 2019 +0200

    another commit

commit a635aaf7f592db3696d3b98bb386c4590ac8e06f
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:42:29 2019 +0200

    initial
```

Note that the last commit is at the top.

You can use also

```
git log abbrev-commit
```

```
commit aa6daef (HEAD -> master)
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:53:09 2019 +0200

    moved file

commit a6a2066
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:51:07 2019 +0200

    another commit

commit a635aaf
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:42:29 2019 +0200

    initial
```

Now the commit ID will be shortened.

```
git log --oneline --graph --decorate
```

This will display the log command with entries compressed in one line, there will be an ASCII graph that will graph the branching, decorate will add any labels or tags that annotates the commits.

```
* aa6daef (HEAD -> master) moved file
* a6a2066 another commit
* a635aaf initial
```

You can specify a range, 

```
git log a635aaf...a6a2066
```

```
commit a6a2066dc8ce8206f995f89c5cc5a36febf230dc
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:51:07 2019 +0200

    another commit
```

You can also date-base search:

```
git log --since="3 days ago"
```

```
commit aa6daef (HEAD -> master)
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:53:09 2019 +0200

    moved file

commit a6a2066
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:51:07 2019 +0200

    another commit

commit a635aaf
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:42:29 2019 +0200

    initial
```

To follow the renames of a file:

```
git log --follow -- l3-file
```

To show information about the commit:

```
git show aa6daef8b82dddc6fd98f253b0ead79d9980421d
```

```
commit aa6daef8b82dddc6fd98f253b0ead79d9980421d (HEAD -> master)
Author: Dāvis Krēgers <example@gmail.com>
Date:   Mon Jan 21 20:53:09 2019 +0200

    moved file

diff --git a/l1/l2/l3/file-3-2 b/l3-file
similarity index 100%
rename from l1/l2/l3/file-3-2
rename to l3-file
```