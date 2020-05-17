### Reference -
https://stackoverflow.com/questions/750172/how-to-change-the-author-and-committer-name-and-e-mail-of-multiple-commits-in-gi


### Step 1

```
-> ~/sandbox/external/git-tutorial  ‹master›
╰─➤  git filter-branch --env-filter '
quote> OLD_EMAIL="abc@xyz.com"
quote> CORRECT_EMAIL="k.sangeeth@gmail.com"
quote> if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
quote> then
quote>    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
quote> fi
quote> if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
quote> then
quote>    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
quote> fi
quote> ' --tag-name-filter cat -- --branches --tags
Rewrite 729c8279ee486cc1e7d67d48b972bec22ae57d71 (1/3) (0 seconds passed, remaining 0 
Rewrite 5605e219828ff4525940c6997a71e26b627c8db3 (2/3) (0 seconds passed, remaining 0 
Rewrite 98c1ef21a8497165a75e49e41f520c1b9dc80969 (3/3) (0 seconds passed, remaining 0 
predicted)
Ref 'refs/heads/master' was rewritten
```

### Step 2

```
git push origin master --force
```

