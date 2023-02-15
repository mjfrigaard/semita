README
================

### Git workflow for issue/feature

Assume the following repository for Git/GH workflow:
<https://github.com/MayaGans/ghapitest>

1.  New issue/feature is created (`add README #1`)  

2.  Create branch for feature/issue (`fix-01`)

    ``` bash
    git checkout -b fix-01
    ```

3.  Fix issue/implement feature (add, commit message `closes #1`)

    ``` bash
    git add . 
    git commit -m "closes #1"
    git push --set-upstream origin fix-01
    ```

4.  Submit PR for `#01`

    - <https://github.com/MayaGans/ghapitest/issues/1>

5.  Request review for `#01`

6.  Comment and mark `#01` as reviewed

    - Creates `#02`: <https://github.com/MayaGans/ghapitest/pull/2>

7.  “Merge pull request `#2` from `MayaGans/fix-01` closes `#01`”

    - [`fd2f3da`](https://github.com/MayaGans/ghapitest/commit/fd2f3daed49f0ee245cc3aae26a05b60b79c1215)

> `#01` is closed, but not tested (or associated with any tests), so if
> we want to include a link to the *test* that’s associated with an
> issue/feature, we create another issue (`#03`)

8.  Create branch to test `#01` (maybe `test-fix-01`?)

9.  Write/run test for issue/feature (`#01`)

10. Create pull request that closes issue `#3` (new branch name?)

11. Request review for `#03`…

12. Comment and mark `#03` as reviewed…

13. “Merge pull request `#4` from `MayaGans/<test-fix-01>` closes `#03`”

------------------------------------------------------------------------

### Traceability matrix:

| issue/feature | issue/feature completed by | system test | test completed by | pass/fail |
|---------------|----------------------------|-------------|-------------------|-----------|
|               |                            |             |                   |           |
|               |                            |             |                   |           |
|               |                            |             |                   |           |

## Querying GitHub

The `gh` package will give us commits

``` r
# this gives all commits in main only
rpo_commits <- gh("/repos/{owner}/{repo}/commits", 
   owner = "MayaGans", 
   repo = "ghapitest")
head(rpo_commits)
## [[1]]
## [[1]]$sha
## [1] "fd2f3daed49f0ee245cc3aae26a05b60b79c1215"
## 
## [[1]]$node_id
## [1] "C_kwDOI-UjqtoAKGZkMmYzZGFlZDQ5ZjBlZTI0NWNjM2FhZTI2YTA1YjYwYjc5YzEyMTU"
## 
## [[1]]$commit
## [[1]]$commit$author
## [[1]]$commit$author$name
## [1] "Martin J Frigaard"
## 
## [[1]]$commit$author$email
## [1] "mjfrigaard@pm.me"
## 
## [[1]]$commit$author$date
## [1] "2023-02-15T18:55:22Z"
## 
## 
## [[1]]$commit$committer
## [[1]]$commit$committer$name
## [1] "GitHub"
## 
## [[1]]$commit$committer$email
## [1] "noreply@github.com"
## 
## [[1]]$commit$committer$date
## [1] "2023-02-15T18:55:22Z"
## 
## 
## [[1]]$commit$message
## [1] "Merge pull request #2 from MayaGans/fix-01\n\ncloses #01"
## 
## [[1]]$commit$tree
## [[1]]$commit$tree$sha
## [1] "acfb970deee525def5a5613b43d75739e9419aec"
## 
## [[1]]$commit$tree$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/trees/acfb970deee525def5a5613b43d75739e9419aec"
## 
## 
## [[1]]$commit$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/commits/fd2f3daed49f0ee245cc3aae26a05b60b79c1215"
## 
## [[1]]$commit$comment_count
## [1] 0
## 
## [[1]]$commit$verification
## [[1]]$commit$verification$verified
## [1] TRUE
## 
## [[1]]$commit$verification$reason
## [1] "valid"
## 
## [[1]]$commit$verification$signature
## [1] "-----BEGIN PGP SIGNATURE-----\n\nwsBcBAABCAAQBQJj7SqaCRBK7hj4Ov3rIwAAxW4IAACGD/732fpBL9YjPtYaHzMk\nkTi9mzyfhrG3LM1heqDSQ/stHtjQLGmoMnTIivLODk/wej62vJyeQMq1Vr6VEJyc\nf+wHKwny/+/Jt8pRcVdEKG+0jdyS2cTYEdVBpxuQhqzlFOjQXR/UVPH3GFwiuv+E\nwugcw25h3kEgoiQUIKXE0CwsGR8Bk08goqs1gp93DAN9yBS5J1UtUEm6g3eiZSDp\n/FFYkt9QtkCwrp37h4gbt4hcQdcrAJylKH7Nk4Ziu+punck3KnIvURIXaCoCR3ry\nOKtLqrAmSXxXnPbnPvxjkvKRvn9zFMwxXqM5DqLk+jLAnp5LCyruPx5PDlrnnjc=\n=LzIP\n-----END PGP SIGNATURE-----\n"
## 
## [[1]]$commit$verification$payload
## [1] "tree acfb970deee525def5a5613b43d75739e9419aec\nparent f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4\nparent ac4b038c36de907eb2ac04868c25fc8588af9a37\nauthor Martin J Frigaard <mjfrigaard@pm.me> 1676487322 -0800\ncommitter GitHub <noreply@github.com> 1676487322 -0800\n\nMerge pull request #2 from MayaGans/fix-01\n\ncloses #01"
## 
## 
## 
## [[1]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/fd2f3daed49f0ee245cc3aae26a05b60b79c1215"
## 
## [[1]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/fd2f3daed49f0ee245cc3aae26a05b60b79c1215"
## 
## [[1]]$comments_url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/fd2f3daed49f0ee245cc3aae26a05b60b79c1215/comments"
## 
## [[1]]$author
## [[1]]$author$login
## [1] "mjfrigaard"
## 
## [[1]]$author$id
## [1] 8368326
## 
## [[1]]$author$node_id
## [1] "MDQ6VXNlcjgzNjgzMjY="
## 
## [[1]]$author$avatar_url
## [1] "https://avatars.githubusercontent.com/u/8368326?v=4"
## 
## [[1]]$author$gravatar_id
## [1] ""
## 
## [[1]]$author$url
## [1] "https://api.github.com/users/mjfrigaard"
## 
## [[1]]$author$html_url
## [1] "https://github.com/mjfrigaard"
## 
## [[1]]$author$followers_url
## [1] "https://api.github.com/users/mjfrigaard/followers"
## 
## [[1]]$author$following_url
## [1] "https://api.github.com/users/mjfrigaard/following{/other_user}"
## 
## [[1]]$author$gists_url
## [1] "https://api.github.com/users/mjfrigaard/gists{/gist_id}"
## 
## [[1]]$author$starred_url
## [1] "https://api.github.com/users/mjfrigaard/starred{/owner}{/repo}"
## 
## [[1]]$author$subscriptions_url
## [1] "https://api.github.com/users/mjfrigaard/subscriptions"
## 
## [[1]]$author$organizations_url
## [1] "https://api.github.com/users/mjfrigaard/orgs"
## 
## [[1]]$author$repos_url
## [1] "https://api.github.com/users/mjfrigaard/repos"
## 
## [[1]]$author$events_url
## [1] "https://api.github.com/users/mjfrigaard/events{/privacy}"
## 
## [[1]]$author$received_events_url
## [1] "https://api.github.com/users/mjfrigaard/received_events"
## 
## [[1]]$author$type
## [1] "User"
## 
## [[1]]$author$site_admin
## [1] FALSE
## 
## 
## [[1]]$committer
## [[1]]$committer$login
## [1] "web-flow"
## 
## [[1]]$committer$id
## [1] 19864447
## 
## [[1]]$committer$node_id
## [1] "MDQ6VXNlcjE5ODY0NDQ3"
## 
## [[1]]$committer$avatar_url
## [1] "https://avatars.githubusercontent.com/u/19864447?v=4"
## 
## [[1]]$committer$gravatar_id
## [1] ""
## 
## [[1]]$committer$url
## [1] "https://api.github.com/users/web-flow"
## 
## [[1]]$committer$html_url
## [1] "https://github.com/web-flow"
## 
## [[1]]$committer$followers_url
## [1] "https://api.github.com/users/web-flow/followers"
## 
## [[1]]$committer$following_url
## [1] "https://api.github.com/users/web-flow/following{/other_user}"
## 
## [[1]]$committer$gists_url
## [1] "https://api.github.com/users/web-flow/gists{/gist_id}"
## 
## [[1]]$committer$starred_url
## [1] "https://api.github.com/users/web-flow/starred{/owner}{/repo}"
## 
## [[1]]$committer$subscriptions_url
## [1] "https://api.github.com/users/web-flow/subscriptions"
## 
## [[1]]$committer$organizations_url
## [1] "https://api.github.com/users/web-flow/orgs"
## 
## [[1]]$committer$repos_url
## [1] "https://api.github.com/users/web-flow/repos"
## 
## [[1]]$committer$events_url
## [1] "https://api.github.com/users/web-flow/events{/privacy}"
## 
## [[1]]$committer$received_events_url
## [1] "https://api.github.com/users/web-flow/received_events"
## 
## [[1]]$committer$type
## [1] "User"
## 
## [[1]]$committer$site_admin
## [1] FALSE
## 
## 
## [[1]]$parents
## [[1]]$parents[[1]]
## [[1]]$parents[[1]]$sha
## [1] "f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[1]]$parents[[1]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[1]]$parents[[1]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## 
## [[1]]$parents[[2]]
## [[1]]$parents[[2]]$sha
## [1] "ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[1]]$parents[[2]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[1]]$parents[[2]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## 
## 
## 
## [[2]]
## [[2]]$sha
## [1] "ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[2]]$node_id
## [1] "C_kwDOI-UjqtoAKGFjNGIwMzhjMzZkZTkwN2ViMmFjMDQ4NjhjMjVmYzg1ODhhZjlhMzc"
## 
## [[2]]$commit
## [[2]]$commit$author
## [[2]]$commit$author$name
## [1] "Maya Gans"
## 
## [[2]]$commit$author$email
## [1] "jaffe.maya@gmail.com"
## 
## [[2]]$commit$author$date
## [1] "2023-02-15T18:49:36Z"
## 
## 
## [[2]]$commit$committer
## [[2]]$commit$committer$name
## [1] "Maya Gans"
## 
## [[2]]$commit$committer$email
## [1] "jaffe.maya@gmail.com"
## 
## [[2]]$commit$committer$date
## [1] "2023-02-15T18:49:36Z"
## 
## 
## [[2]]$commit$message
## [1] "closes #01"
## 
## [[2]]$commit$tree
## [[2]]$commit$tree$sha
## [1] "acfb970deee525def5a5613b43d75739e9419aec"
## 
## [[2]]$commit$tree$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/trees/acfb970deee525def5a5613b43d75739e9419aec"
## 
## 
## [[2]]$commit$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/commits/ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[2]]$commit$comment_count
## [1] 0
## 
## [[2]]$commit$verification
## [[2]]$commit$verification$verified
## [1] FALSE
## 
## [[2]]$commit$verification$reason
## [1] "unsigned"
## 
## [[2]]$commit$verification$signature
## NULL
## 
## [[2]]$commit$verification$payload
## NULL
## 
## 
## 
## [[2]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[2]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[2]]$comments_url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/ac4b038c36de907eb2ac04868c25fc8588af9a37/comments"
## 
## [[2]]$author
## [[2]]$author$login
## [1] "MayaGans"
## 
## [[2]]$author$id
## [1] 6053906
## 
## [[2]]$author$node_id
## [1] "MDQ6VXNlcjYwNTM5MDY="
## 
## [[2]]$author$avatar_url
## [1] "https://avatars.githubusercontent.com/u/6053906?v=4"
## 
## [[2]]$author$gravatar_id
## [1] ""
## 
## [[2]]$author$url
## [1] "https://api.github.com/users/MayaGans"
## 
## [[2]]$author$html_url
## [1] "https://github.com/MayaGans"
## 
## [[2]]$author$followers_url
## [1] "https://api.github.com/users/MayaGans/followers"
## 
## [[2]]$author$following_url
## [1] "https://api.github.com/users/MayaGans/following{/other_user}"
## 
## [[2]]$author$gists_url
## [1] "https://api.github.com/users/MayaGans/gists{/gist_id}"
## 
## [[2]]$author$starred_url
## [1] "https://api.github.com/users/MayaGans/starred{/owner}{/repo}"
## 
## [[2]]$author$subscriptions_url
## [1] "https://api.github.com/users/MayaGans/subscriptions"
## 
## [[2]]$author$organizations_url
## [1] "https://api.github.com/users/MayaGans/orgs"
## 
## [[2]]$author$repos_url
## [1] "https://api.github.com/users/MayaGans/repos"
## 
## [[2]]$author$events_url
## [1] "https://api.github.com/users/MayaGans/events{/privacy}"
## 
## [[2]]$author$received_events_url
## [1] "https://api.github.com/users/MayaGans/received_events"
## 
## [[2]]$author$type
## [1] "User"
## 
## [[2]]$author$site_admin
## [1] FALSE
## 
## 
## [[2]]$committer
## [[2]]$committer$login
## [1] "MayaGans"
## 
## [[2]]$committer$id
## [1] 6053906
## 
## [[2]]$committer$node_id
## [1] "MDQ6VXNlcjYwNTM5MDY="
## 
## [[2]]$committer$avatar_url
## [1] "https://avatars.githubusercontent.com/u/6053906?v=4"
## 
## [[2]]$committer$gravatar_id
## [1] ""
## 
## [[2]]$committer$url
## [1] "https://api.github.com/users/MayaGans"
## 
## [[2]]$committer$html_url
## [1] "https://github.com/MayaGans"
## 
## [[2]]$committer$followers_url
## [1] "https://api.github.com/users/MayaGans/followers"
## 
## [[2]]$committer$following_url
## [1] "https://api.github.com/users/MayaGans/following{/other_user}"
## 
## [[2]]$committer$gists_url
## [1] "https://api.github.com/users/MayaGans/gists{/gist_id}"
## 
## [[2]]$committer$starred_url
## [1] "https://api.github.com/users/MayaGans/starred{/owner}{/repo}"
## 
## [[2]]$committer$subscriptions_url
## [1] "https://api.github.com/users/MayaGans/subscriptions"
## 
## [[2]]$committer$organizations_url
## [1] "https://api.github.com/users/MayaGans/orgs"
## 
## [[2]]$committer$repos_url
## [1] "https://api.github.com/users/MayaGans/repos"
## 
## [[2]]$committer$events_url
## [1] "https://api.github.com/users/MayaGans/events{/privacy}"
## 
## [[2]]$committer$received_events_url
## [1] "https://api.github.com/users/MayaGans/received_events"
## 
## [[2]]$committer$type
## [1] "User"
## 
## [[2]]$committer$site_admin
## [1] FALSE
## 
## 
## [[2]]$parents
## [[2]]$parents[[1]]
## [[2]]$parents[[1]]$sha
## [1] "f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[2]]$parents[[1]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[2]]$parents[[1]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## 
## 
## 
## [[3]]
## [[3]]$sha
## [1] "f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[3]]$node_id
## [1] "C_kwDOI-UjqtoAKGYyYzJhZmM1YWI4ZmY5YzZhYmM0NDFlMTVkY2Y5OWY4YTE2NDgzZjQ"
## 
## [[3]]$commit
## [[3]]$commit$author
## [[3]]$commit$author$name
## [1] "Maya Gans"
## 
## [[3]]$commit$author$email
## [1] "jaffe.maya@gmail.com"
## 
## [[3]]$commit$author$date
## [1] "2023-02-15T18:47:14Z"
## 
## 
## [[3]]$commit$committer
## [[3]]$commit$committer$name
## [1] "Maya Gans"
## 
## [[3]]$commit$committer$email
## [1] "jaffe.maya@gmail.com"
## 
## [[3]]$commit$committer$date
## [1] "2023-02-15T18:47:14Z"
## 
## 
## [[3]]$commit$message
## [1] "first commit"
## 
## [[3]]$commit$tree
## [[3]]$commit$tree$sha
## [1] "a3f566a1c79bf476ced5b6b1d25b3b2a69c7d70a"
## 
## [[3]]$commit$tree$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/trees/a3f566a1c79bf476ced5b6b1d25b3b2a69c7d70a"
## 
## 
## [[3]]$commit$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/git/commits/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[3]]$commit$comment_count
## [1] 0
## 
## [[3]]$commit$verification
## [[3]]$commit$verification$verified
## [1] FALSE
## 
## [[3]]$commit$verification$reason
## [1] "unsigned"
## 
## [[3]]$commit$verification$signature
## NULL
## 
## [[3]]$commit$verification$payload
## NULL
## 
## 
## 
## [[3]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[3]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/commit/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4"
## 
## [[3]]$comments_url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/commits/f2c2afc5ab8ff9c6abc441e15dcf99f8a16483f4/comments"
## 
## [[3]]$author
## [[3]]$author$login
## [1] "MayaGans"
## 
## [[3]]$author$id
## [1] 6053906
## 
## [[3]]$author$node_id
## [1] "MDQ6VXNlcjYwNTM5MDY="
## 
## [[3]]$author$avatar_url
## [1] "https://avatars.githubusercontent.com/u/6053906?v=4"
## 
## [[3]]$author$gravatar_id
## [1] ""
## 
## [[3]]$author$url
## [1] "https://api.github.com/users/MayaGans"
## 
## [[3]]$author$html_url
## [1] "https://github.com/MayaGans"
## 
## [[3]]$author$followers_url
## [1] "https://api.github.com/users/MayaGans/followers"
## 
## [[3]]$author$following_url
## [1] "https://api.github.com/users/MayaGans/following{/other_user}"
## 
## [[3]]$author$gists_url
## [1] "https://api.github.com/users/MayaGans/gists{/gist_id}"
## 
## [[3]]$author$starred_url
## [1] "https://api.github.com/users/MayaGans/starred{/owner}{/repo}"
## 
## [[3]]$author$subscriptions_url
## [1] "https://api.github.com/users/MayaGans/subscriptions"
## 
## [[3]]$author$organizations_url
## [1] "https://api.github.com/users/MayaGans/orgs"
## 
## [[3]]$author$repos_url
## [1] "https://api.github.com/users/MayaGans/repos"
## 
## [[3]]$author$events_url
## [1] "https://api.github.com/users/MayaGans/events{/privacy}"
## 
## [[3]]$author$received_events_url
## [1] "https://api.github.com/users/MayaGans/received_events"
## 
## [[3]]$author$type
## [1] "User"
## 
## [[3]]$author$site_admin
## [1] FALSE
## 
## 
## [[3]]$committer
## [[3]]$committer$login
## [1] "MayaGans"
## 
## [[3]]$committer$id
## [1] 6053906
## 
## [[3]]$committer$node_id
## [1] "MDQ6VXNlcjYwNTM5MDY="
## 
## [[3]]$committer$avatar_url
## [1] "https://avatars.githubusercontent.com/u/6053906?v=4"
## 
## [[3]]$committer$gravatar_id
## [1] ""
## 
## [[3]]$committer$url
## [1] "https://api.github.com/users/MayaGans"
## 
## [[3]]$committer$html_url
## [1] "https://github.com/MayaGans"
## 
## [[3]]$committer$followers_url
## [1] "https://api.github.com/users/MayaGans/followers"
## 
## [[3]]$committer$following_url
## [1] "https://api.github.com/users/MayaGans/following{/other_user}"
## 
## [[3]]$committer$gists_url
## [1] "https://api.github.com/users/MayaGans/gists{/gist_id}"
## 
## [[3]]$committer$starred_url
## [1] "https://api.github.com/users/MayaGans/starred{/owner}{/repo}"
## 
## [[3]]$committer$subscriptions_url
## [1] "https://api.github.com/users/MayaGans/subscriptions"
## 
## [[3]]$committer$organizations_url
## [1] "https://api.github.com/users/MayaGans/orgs"
## 
## [[3]]$committer$repos_url
## [1] "https://api.github.com/users/MayaGans/repos"
## 
## [[3]]$committer$events_url
## [1] "https://api.github.com/users/MayaGans/events{/privacy}"
## 
## [[3]]$committer$received_events_url
## [1] "https://api.github.com/users/MayaGans/received_events"
## 
## [[3]]$committer$type
## [1] "User"
## 
## [[3]]$committer$site_admin
## [1] FALSE
## 
## 
## [[3]]$parents
## list()
```

And comments

``` r
# this returns comments (in GH) on PR
rpo_comments <- gh("/repos/{owner}/{repo}/pulls/comments", 
   owner = "MayaGans", 
   repo = "ghapitest")
head(rpo_comments)
## [[1]]
## [[1]]$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/pulls/comments/1107569361"
## 
## [[1]]$pull_request_review_id
## [1] 1300152207
## 
## [[1]]$id
## [1] 1107569361
## 
## [[1]]$node_id
## [1] "PRRC_kwDOI-Ujqs5CBCrR"
## 
## [[1]]$diff_hunk
## [1] "@@ -0,0 +1 @@\n+This is a README"
## 
## [[1]]$path
## [1] "README.md"
## 
## [[1]]$position
## [1] 1
## 
## [[1]]$original_position
## [1] 1
## 
## [[1]]$commit_id
## [1] "ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[1]]$original_commit_id
## [1] "ac4b038c36de907eb2ac04868c25fc8588af9a37"
## 
## [[1]]$user
## [[1]]$user$login
## [1] "mjfrigaard"
## 
## [[1]]$user$id
## [1] 8368326
## 
## [[1]]$user$node_id
## [1] "MDQ6VXNlcjgzNjgzMjY="
## 
## [[1]]$user$avatar_url
## [1] "https://avatars.githubusercontent.com/u/8368326?v=4"
## 
## [[1]]$user$gravatar_id
## [1] ""
## 
## [[1]]$user$url
## [1] "https://api.github.com/users/mjfrigaard"
## 
## [[1]]$user$html_url
## [1] "https://github.com/mjfrigaard"
## 
## [[1]]$user$followers_url
## [1] "https://api.github.com/users/mjfrigaard/followers"
## 
## [[1]]$user$following_url
## [1] "https://api.github.com/users/mjfrigaard/following{/other_user}"
## 
## [[1]]$user$gists_url
## [1] "https://api.github.com/users/mjfrigaard/gists{/gist_id}"
## 
## [[1]]$user$starred_url
## [1] "https://api.github.com/users/mjfrigaard/starred{/owner}{/repo}"
## 
## [[1]]$user$subscriptions_url
## [1] "https://api.github.com/users/mjfrigaard/subscriptions"
## 
## [[1]]$user$organizations_url
## [1] "https://api.github.com/users/mjfrigaard/orgs"
## 
## [[1]]$user$repos_url
## [1] "https://api.github.com/users/mjfrigaard/repos"
## 
## [[1]]$user$events_url
## [1] "https://api.github.com/users/mjfrigaard/events{/privacy}"
## 
## [[1]]$user$received_events_url
## [1] "https://api.github.com/users/mjfrigaard/received_events"
## 
## [[1]]$user$type
## [1] "User"
## 
## [[1]]$user$site_admin
## [1] FALSE
## 
## 
## [[1]]$body
## [1] "This review comment is about your README"
## 
## [[1]]$created_at
## [1] "2023-02-15T18:52:27Z"
## 
## [[1]]$updated_at
## [1] "2023-02-15T18:52:27Z"
## 
## [[1]]$html_url
## [1] "https://github.com/MayaGans/ghapitest/pull/2#discussion_r1107569361"
## 
## [[1]]$pull_request_url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/pulls/2"
## 
## [[1]]$author_association
## [1] "COLLABORATOR"
## 
## [[1]]$`_links`
## [[1]]$`_links`$self
## [[1]]$`_links`$self$href
## [1] "https://api.github.com/repos/MayaGans/ghapitest/pulls/comments/1107569361"
## 
## 
## [[1]]$`_links`$html
## [[1]]$`_links`$html$href
## [1] "https://github.com/MayaGans/ghapitest/pull/2#discussion_r1107569361"
## 
## 
## [[1]]$`_links`$pull_request
## [[1]]$`_links`$pull_request$href
## [1] "https://api.github.com/repos/MayaGans/ghapitest/pulls/2"
## 
## 
## 
## [[1]]$reactions
## [[1]]$reactions$url
## [1] "https://api.github.com/repos/MayaGans/ghapitest/pulls/comments/1107569361/reactions"
## 
## [[1]]$reactions$total_count
## [1] 0
## 
## [[1]]$reactions$`+1`
## [1] 0
## 
## [[1]]$reactions$`-1`
## [1] 0
## 
## [[1]]$reactions$laugh
## [1] 0
## 
## [[1]]$reactions$hooray
## [1] 0
## 
## [[1]]$reactions$confused
## [1] 0
## 
## [[1]]$reactions$heart
## [1] 0
## 
## [[1]]$reactions$rocket
## [1] 0
## 
## [[1]]$reactions$eyes
## [1] 0
## 
## 
## [[1]]$start_line
## NULL
## 
## [[1]]$original_start_line
## NULL
## 
## [[1]]$start_side
## NULL
## 
## [[1]]$line
## [1] 1
## 
## [[1]]$original_line
## [1] 1
## 
## [[1]]$side
## [1] "RIGHT"
```

## Examples of the `gh` package:

``` r
repos <- gh("GET /orgs/{org}/repos", org = "r-lib")
vapply(repos, "[[", "", "name")
gh("/users/{username}/repos/{repo}",
   username = "hadley",
   repo = "adv-r")
gh("/users/{username}/repos/{repo}",
   username = "hadley",
   repo = "adv-r")
gh("/repos/{owner}/{repo}/comments",
   owner = "hadley",
   repo = "adv-r")
```
