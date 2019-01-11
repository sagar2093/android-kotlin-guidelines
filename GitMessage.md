Type can be 
```
#    feat     (new feature)
#    fix      (bug fix)
#    WIP      (work in progress)
#    refactor (refactoring production code)
#    refactor (formatting, missing semi colons, etc; no code change)
#    docs     (changes to documentation)
#    test     (adding or refactoring tests; no production code change)
#    chore    (updating grunt tasks etc; no production code change)
```

Rules for git message and updates.
```
Remember to
#    Capitalize the subject line
#    Use the imperative mood in the subject line
#    Do not end the subject line with a period
#    Separate subject from body with a blank line
#    Use the body to explain what and why vs. how
#    Can use multiple lines with "-" for bullet points in body
```

Updates and git messages can follow below formats.

**Example without jira task id**
```
[feat] integrate login api
[fix]  specific bug fix
```

**Example with Jira Task id**
```
[feat] SAR-12 integrate login api
```

**Daily update Sample**
```skype
*Today's Update (Jan-07,2019) *
[feat] SAR-12 integrate login api
  - add retrofit library
  - fetch and parse login data
  - handle api errors
  - update UI with error
  - update UI with success data
```


