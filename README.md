The generated site accessible [here](https://hbock-42.github.io/personal_documentation)

# Commands

```bash title="run a local server"
npx quartz build --serve
```


```bash title="commit and push your work"
npx quartz sync
```

*todo*: add a git commit and push on the content submodule to the sync command

# Some modifications
## Submodule
I use a git submodule to fill the content directory.

### Implications regarding cloning the repository:

1. I must init the submodule
```bash
git submodule init
```

2. Git pull will not update the submodule, I must do it on my own
```bash
git submodule update
```

> [!TIPS]
> 
> All in one
> Clone with submodule:

> ```
> git clone --recurse-submodules
> ```
> Pull with submodule:
> ```
>  git pull --recurse-submodules
> ```


### Implications regarding deploying my spa
Because the `./content` folder is a submodule, the parent git repository only contains a reference to the git submodule, no actual files.

#### Add a step in the CI to clone the submodule
Since we use github actions to build the SPA, it is done directly from the github repository, so there is nothing inside the `./content` folder to actually build the SPA.

To solve this issue I added the line `submodules: true` in the `actions/checkout@v3` action of the `deploy.yml` file.

#### Give cloning permission to the CI
Since my submodule is private, I needed to add permission so github action was allowed to clone it. This was done the `actions/create-github-app-token@v1` action added to the `deploy.yml`. 

More about `create-github-app-token@v1` [here](https://github.com/actions/create-github-app-token?tab=readme-ov-file), but to sum up:

1. Create a Github app ^85f612

2. Install the app on the repository containing my SPA content AND on the current repository (where the CI will be played from).

3. In github, create 2 secrets in the repository:
	. One secret containing the app ID of the app created in step [[HUGO_README#^85f612 | 1]] . We named this secret `PERSONAL_DOC_READ_ONLY_ACCESS_APP_ID`
	. One secret containing the private key of the app created in step [[HUGO_README#^85f612 | 1]] . We named this secret `PERSONAL_DOC_READ_ONLY_ACCESS_APP_PRIVATE_KEY`

3. In the CI deploy file `deploy.yml` we use this secret like that:

```yaml
app-id: ${{ secrets.PERSONAL_DOC_READ_ONLY_ACCESS_APP_ID }}

private-key: ${{ secrets.PERSONAL_DOC_READ_ONLY_ACCESS_APP_PRIVATE_KEY }}
```


# Quartz v4

This is made with quartz

Documentation: https://quartz.jzhao.xyz/
