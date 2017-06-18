### CLI Commands

##### Development commands
1. [npm init](#npm-init)
2. [npm install](#npm-install)
3. [npm link](#npm-link)
4. [npm uninstall](#npm-uninstall)
5. [npm list](#npm-list)
6. [npm outdated](#npm-outdated)
7. [npm update](#npm-update)
8. [npm prune](#npm-prune)
9. [npm dedupe](#npm-dedupe)

##### Exploring repo commands
10. [npm view](#npm-view)
11. [npm search](#npm-search)
12. [npm repo](#npm-repo)
13. [npm docs](#npm-docs)

##### User-like commands
14. [npm whoami](#npm-whoami)
15. [npm owner](#npm-owner)
16. [npm login](#npm-login)
17. [npm logout](#npm-logout)

##### Publishing commands
18. [npm version](#npm-version)
19. [npm dist-tag](#npm-dist-tag)
20. [npm publish](#npm-publish)
21. [npm deprecate](#npm-deprecate)
22. [npm unpublish](#npm-unpublish)
23. [npm pack](#npm-pack)

##### Config-like commands
24. [npm config](#npm-config)
25. [npm prefix](#npm-prefix)
26. [npm root](#npm-root)
27. [npm bin](#npm-bin)
28. [npm -v](#npm--v)

##### Running scripts commands
29. [npm run-script](#npm-run-script)
30. [npm test](#npm-test)
31. [npm install-test](#npm-install-test)
32. [npm start](#npm-start)
33. [npm stop](#npm-stop)
34. [npm restart](#npm-restart)

### Running Scripts
1. CLI commands [\[link\]](#cli-commands-1)
2. pre-scripts and post-scripts [\[link\]](#pre-scripts-and-post-scripts)

### Versioning rules
1. Versioning syntax [\[link\]](#versioning-syntax)
1. Versions precedence rules [\[link\]](#versions-precedence-rules)
1. The `semver` package [\[link\]](#the-semver-package)
2. Version's ranges [\[link\]](#versions-ranges)
3. `npm install` versioning rules [\[link\]](#npm-install-versioning-rules)

### Ignore rules
1. The `.npmignore` rules [\[link\]](#the-npmignore-rules)

&nbsp;
&nbsp;
&nbsp;
&nbsp;
## Commands

###### [#top](#cli-commands)
###### npm init
| `npm init` | description |
|:---:|:---|
| `npm init` | Creates `package.json` file in the current location after the questionnaire fill in *(if the `package.json` file already exists, it will get the data from `package.json` file first, and display questionnaire with these data as default)* |
| `npm init --yes` `npm init -y` `npm init --force` `npm init -f` | Creates `package.json` file automatically without questionnaire *(name: current directory name; version: 1.0.0; description: first line of readme.md, otherwise empty; dependencies: all packages from node_modules folder)* |

###### [#top](#cli-commands)
###### npm install
| `npm install` | description |
|:---:|:---|
| `npm install lodash` | Installs the **latest** version *(the version of the `latest` tag)* of the `lodash` package **locally** *(in the `node_modules` folder)*. If the `lodash` is already installed, it updates the installation. |
| `npm install lodash jquery jasmine` | Installs the latest versions of `lodash`, `jquery` and `jasmine` packages **locally** |
| `npm install lodash@latest` | Installs the **latest** version of the `lodash` package **locally** |
| `npm install lodash@4.17.0` | Installs the `4.17.0` version of the `lodash` package **locally** |
| `npm install jasmine@2.5.0 lodash@4.14.0 jquery@2.2.0` | Installs the `2.5.0` version of `jasmine` package, the `4.14.0` version of `lodash` package and the `2.2.0` version of `jquery` package **locally** |
| `npm install lodash@">= 4.15.0 < 5.0.0"` | Installs the *(possible highest)* version of `lodash` package matching the specified **version range**|
| `npm install lodash@"< 3.3.0" jquery@"2.1.*" jasmine@">=2.0.0 < 2.4.0"` | Installs the versions of `lodash` *`[v3.2.0]`*, `jquery` *`[v2.1.4]`* and `jasmine` *`[v2.3.2]`* packages matching the specified **version range** |
| `npm install my-pckg@my-tag` | Installs the version of `my-pckg` package **tagged** *(when published)* with `my-tag` tag; [\[see npm dist-tag\]](#npm-dist-tag) |
| `npm install lodash -g` | Installs the **latest** version of the `lodash` package **globally**|
| `npm install jasmine lodash jquery -g` | Installs the **latest** versions of the `jasmine`, `lodash` and `jquery` packages **globally**  |
| `npm install lodash --link` | Links **globally** installed package into **local** `node_modules` directory. Installs `lodash` package globally and creates shortcut folder in the **local** `node_modules` directory linked to the global path |
| `npm install` | Installs **all packages** listed in the `package.json` file **`dependencies`**, **`devDependencies`** and **`optionalDependencies`** objects **locally** |
| `npm install --production` | npm **will not install** packages listed in **`devDependencies`** object of `package.json` file. Installs packages listed in **`dependencies`** and **`optionalDependencies`** |
| `npm install --only=prod` `npm install --only=production` | npm **will not install** packages listed in **`devDependencies`** object of `package.json` file. Installs packages listed in **`dependencies`** and **`optionalDependencies`** |
| `npm install --only=dev` `npm install --only=development` | npm **will not install** packages listed in **`dependencies`** and **`optionalDependencies`** objects of `package.json` file. Installs **only** packages listed in **`dependencies`**|
| `npm install --no-optional` | npm **will not install** packages listed in **`optionalDependencies`** object of `package.json` file. Installs packages listed in **`dependencies`** and **`devDependencies`** |
| `npm install --production --no-optional` | npm **will not install** packages listed in **`optionalDependencies`** and **`devDependencies`** objects of `package.json` file. Installs packages listed only in **`dependencies`** |
| `npm install -g` | Installs **current package globally** *(with all its dependencies listed in `package.json` file)* |
| `npm install lodash --save` `npm install lodash -S` |  Installs the **latest** version of the `lodash` package **locally** and adds the entry to the `package.json` file `dependencies` object |
| `npm install lodash@4.17.0 --save --save-exact` | Installs the `4.17.0` version of `lodash` and adds the entry to the `package.json` file `dependencies` object as `"lodash":"4.17.0"` rather than `"lodash":"^4.17.0"` *(that allows major updates)*; [\[see package.json versioning rules\]](#packagejson-versioning-rules)|
| `npm install lodash@4.10.0 jquery@2.2.1 jasmine@2.3.1 --save --save-exact` | Installs the `4.10.0` version of `lodash`, `2.2.1` version of `jquery` and `2.3.1` version of `jasmine` and adds the entries to the `package.json` file `dependencies` object as `"dependencies": {"jasmine": "2.3.1", "jquery": "2.2.1","lodash": "4.10.0"}` |
| `npm install lodash --save-dev` `npm install lodash -D` |  Installs the **latest** version of the `lodash` package **locally** and adds the entry to the `package.json` file `devDependencies` object |
| `npm install lodash --save-optional` `npm install lodash -O` | Installs the **latest** version of the `lodash` package **locally** and adds the entry to the `package.json` file `optionalDependencies` object |
| `npm install lodash -g --save` `npm install lodash -g --save-dev`| Installs the **latest** version of the `lodash` package **globally** and **does not add** the entry to the `package.json` file `dependencies` or `devDependencies` object |
| `npm install jasmine --dry-run` | Reports what the `npm install jasmine` would have done. Does **not install** anything. |
| `npm install jasmine --save --dry-run` | Reports what the `npm install jasmine` would have done. Does **not install** anything, does **not add the entry** to the `package.json` file `dependencies` object |
| `npm install my-pckg --force` `npm install my-pckg -f` | Installing `my-pckg` package inside `my-pckg` is forbidden *(npm will refuse to install any package with an **identical name** to the current package)*. It forces the installation of `my-pckg` package inside `my-pckg` package. |
|`npm install https://github.com/user-name/my-pckg/tarball/v2.1.6` | Downloads the `2.1.6` version of `my-pckg` package as the compressed `my-pckg.tar.gz` file from **github tarball url** and installs it; You can **get** the tarball file **url** from releases site, eg. [\[jasmine releases\]](https://github.com/jasmine/jasmine-npm/releases) |
| `npm install https://github.com/user-name/my-pckg/archive/v2.1.6.tar.gz` | Downloads the `2.1.6` version of `my-pckg` package as the compressed `my-pckg.tar.gz` file from **github tarball url** and installs it; You can **get** the tarball file **url** from releases site, eg. [\[jasmine releases\]](https://github.com/jasmine/jasmine-npm/releases) |
|`npm install https://github.com/user-name/my-pckg/tarball/v2.1.6 --save-dev` | Installs `my-pckg` package **locally** and adds the entry to the `package.json` file `devDependencies` object as `"my-pckg": "https://github.com/user-name/my-pckg/tarball/v2.1.6"` |
| `npm install https://github.com/user-name/my-pckg/archive/v2.1.6.tar.gz --save` | Installs `my-pckg` package **locally** and adds the entry to the `package.json` file `dependencies` object as `"my-pckg": "https://github.com/user-name/my-pckg-name/archive/v2.1.6.tar.gz"` |
| `npm install .path/to/packages/my-pckg.tar.gz` | Installs `my-pckg` package from `my-pckg.tar.gz` file, eg. downloaded from https://github.com, eg. [\[jasmine releases\]](https://github.com/jasmine/jasmine-npm/releases) |
| `npm install .path/to/packages/my-pckg.tar.gz --save` | Installs `my-pckg` package from `my-pckg.tar.gz` file and adds the entry to the `package.json` file `dependencies` object as `"my-pckg": "file:path/to/packages/my-pckg.tar.gz"` |
| `npm install git+https://user@email.com/user-name/my-pckg.git` | Installs the `my-pckg` package from Git with the **http protocol**|
| `npm install git+https://user@email.com/user-name/my-pckg.git --save` | Installs the `my-pckg` package from Git with the **http protocol** and adds the entry to the `package.json` file `dependencies` object as `"my-pckg": "git+https://user@email.com/user-name/my-pckg.git"`|
| `npm install git://github.com/user-name/my-pckg.git#v2.1.6` | Installs the `my-pckg` package from Git with the **git protocol** |
| `npm install git://github.com/user-name/my-pckg.git#v2.1.6 --save` | Installs the `my-pckg` package from Git with the **git protocol** and adds the entry to the `package.json` file `dependencies` object as `"my-pckg": "git://github.com/user-name/my-pckg.git#v2.1.6"` |
| `npm install user-name/my-pckg` | Attempts to clone `my-pckg` package from *https://github.com/user-name/my-pckg* url and installs it |
| `npm install jasmine/jasmine-npm#v2.5.0 --save` `npm install github:jasmine/jasmine-npm#v2.5.0 --save` | Installs `2.5.0` version of `jasmine` package from the [github.com](https://github.com/jasmine/jasmine-npm/tree/v2.5.1) repository and adds the entry to the `package.json` file `dependencies` object as `"jasmine": "github:jasmine/jasmine-npm#v2.5.0"`. If the commit-ish `#v2.5.0` is not specified on GitHub, it gets the package from master. |
| `npm install gist:5e7acfcec2a2dda82ca3fd41c2db6d00 --save"` | Installs the package from https://gist.github.com/5e7acfcec2a2dda82ca3fd41c2db6d00  and adds the entry to the `package.json` file `dependencies` object as `"package-name": "gist:5e7acfcec2a2dda82ca3fd41c2db6d00"`. Each gist gets its unique ID when created, which is also the part of gist.github.com link. The installing gist must contain valid `package.json` file |
| `npm install bitbucket:user-name/my-pckg --save` | Installs the `my-pckg` package from the [bitbucket.org](https://bitbucket.org) repository and adds the entry to the `package.json` file `dependencies` object as `"my-pckg": "bitbucket:user-name/my-pckg"` |
| `npm install ./path/to/package` | Installs the package from the `path/to/package` directory. This folder must contain valid `package.json` file |




###### [#top](#cli-commands)
###### npm link
| `npm link` `npm ln` | description |
|:---:|:---|
| `npm link babel-cli` | Links **globally** installed package into **local** `node_modules` directory. Installs `babel-cli` package globally *(if not installed)* and creates shortcut folder in the **local** `node_modules` directory linked to the global path. To **'un-link'** package, use `npm uninstall` |
| `npm link babel-cli --save-dev` | Creates shortcut folder in the **local** `node_modules` directory linked to the global `babel-cli` package path. Does **not add entry** to the `package.json` file `devDependencies` object |

###### [#top](#cli-commands)
###### npm uninstall
| `npm uninstall` `npm remove` `npm unlink` `npm rm` `npm r` `npm un` | description |
|:---:|:---|
| `npm uninstall lodash` | Removes the `lodash` package from the **local** `node_modules` directory *(without removing the entry from `package.json` file `dependencies` or `devDependencies` object)* |
| `npm uninstall lodash -g` | Removes the `lodash` package from the **global** `node_modules` directory |
| `npm uninstall lodash jasmine jquery` | Removes the `lodash`, `jasmine` and `jquery` packages from the **local** `node_modules` directory *(without removing the entries from `package.json` file `dependencies` or `devDependencies` object)* |
| `npm uninstall lodash jasmine jquery -g` | Removes the `lodash`, `jasmine` and `jquery` packages from the **global** `node_modules` directory |
| `npm uninstall lodash --save` `npm uninstall lodash -S` | Removes the `lodash` package from the **local** `node_modules` *(and removes the entry from `package.json` file `dependencies` object)* |
| `npm uninstall lodash jasmine jquery --save` | Removes the `lodash`, `jasmine` and `jquery` packages from the **local** `node_modules` *(and removes the entries from `package.json` file `dependencies` object)* |
| `npm uninstall lodash --save-dev` `npm uninstall lodash -D` | Removes the `lodash` package from the **local** `node_modules` *(and removes the entry from `package.json` file `devDependencies` object)* |
| `npm uninstall lodash jasmine jquery --save-dev` | Removes the `lodash`, `jasmine` and `jquery` packages from the **local** `node_modules` *(and removes the entries from `package.json` file `devDependencies` object)* |
| `npm uninstall lodash --save-optional` `npm uninstall lodash -O` | Removes the `lodash` package from the **local** `node_modules` *(and removes the entry from `package.json` file `optionalDependencies` object)* |

###### [#top](#cli-commands)
###### npm list
| `npm list` `npm ls` `npm la` `npm ll` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm list` `npm ls` | Returns all packages *(and their dependencies)* installed **locally** as a *tree-structured* list. It prints out **extraneous**, **missing**, and **invalid** packages. If the `node_modules` directory **contains** the package, that **is not listed** as `package.json` dependency, the console returns this package as **extraneous** [\[see npm prune\]](#npm-prune). If the `node_modules` directory **does not contain** the package, that **is listed** as `package.json` dependency, the console returns this package as **unmet** *(missing)* **dependency** |
| `npm ls jasmine` | Returns the package name and its version, eg. `jasmine@2.4.0` installed **locally**. If the `jasmine` package is not installed locally, it returns `empty`. It lets to check out whether the package is installed or not |
| `npm ls jasmine-core` | If the `jasmine-core` package is a sub-dependency *(the dependency of other installed package)*, it returns **chain** of packages, that depends on `jasmine-core` *(including `jasmine-core`)* as a **tree-structured list** |
| `npm la` `npm ll` `npm list --long` `npm ls --long` | Returns all packages installed locally with **extended information** from the `package.json` file: `description`, `repository.url` and `homepage`|
| `npm list -g` `npm list --global` | Returns all packages *(and their dependencies)* installed **globally** as a **tree-structured list** |
| `npm list -g --depth=0` | Returns all packages installed globally with the minimal **depth of dependency tree** set *(excluding subdependencies of installed packages)* |
| `npm list --depth=2` | Returns all packages installed locally with the depth of dependency three set to the second level |
| `npm list --prod` `npm list --production` `npm list --only=prod` | Returns the dependency tree only for the packages listed in the `package.json` file `dependencies` object |
| `npm list --dev` `npm list --only=dev` | Returns only the dependency tree for packages listed in the `package.json` file `devDependencies` object |
| `npm list --json` | Returns all packages *(and their dependencies)* installed **locally** in a **JSON** format, including `name`, `version`, `from` *(version-range)* properties|
| `npm list --parseable` | Returns all packages *(and their dependencies)* installed **locally** as a **list of paths** |
| `npm list --parseable --long` `npm la --parseable` | Returns all packages *(and their dependencies)* installed **locally** as a **list of paths** with **extended information** *(path:name@version)* |

###### [#top](#cli-commands)
###### npm outdated
| `npm outdated` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm outdated` | Checks if any of **locally** installed packages is outdated and returns the output of versions: **`package`** *(the name of package)*, **`current`** *(currently installed version, eg. `2.4.1` or `MISSING` if the package is not installed)*, **`wanted`** *(the version that satisfies the `package.json` specified version range)*, **`latest`** *(the version of the package released with the `latest` tag)* **`location`** *(`node_modules/package-name`)*. If all the packages are **up-to-date**, it returns nothing. |
| `npm outdated --long` | Returns **extended information**: **`type`** *(whether the package belongs to `dependencies` or `devDependencies`)* |
| `npm outdated -g` `npm outdated --global` | Checks if any of **globally** installed packages is outdated and returns the output of versions *(described above)*: **`wanted`** *(because there is no global `package.json` file, it returns the current installed version)* |
| `npm outdated babel-cli` | Checks if the `babel-cli` package is outdated and returns the output of versions *(described above)*. If the `babel-cli` package is **up-to-date**, or if it is **not installed**, it returns nothing. |
| `npm outdated --json` | Checks if any of installed packages is outdated and returns the output of versions in a **JSON** format |
| `npm outdated --parseable` | Checks if any of installed packages is outdated and returns the output of versions as a **list of paths** |
| `npm outdated --depth=2` | Checks if any of installed packages *(with the depth of dependency three set to the second level)* is outdated and returns the output of versions *(described above)*. The default is `--depth=0` |

###### [#top](#cli-commands)
###### npm update
| `npm update` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm update` | **Updates all** *(or **installs missing**)* packages listed in `package.json` file as both `dependencies` and `devDependencies` to the **latest version** *(satisfying `package.json` semantic versioning rules)* or to the **lower version** *(if installed version is higher than indicated in `package.json` file)* |
| `npm update lodash` | **Updates** *(or installs)* `lodash` package to the **latest version** *(satisfying `package.json` semantic versioning rules)* |
| `npm update jasmine jquery` | **Updates** `jasmine` and `jquery` packages to the **latest versions** *(satisfying `package.json` semantic versioning rules)* |
| `npm update lodash --save-dev` | **Updates** `lodash` package to the **latest version** *(satisfying `package.json` semantic versioning rules)* and **updates the entry** in `package.json` file `devDependencies` |
| `npm update jquery --save` | **Updates** `jquery` package to the **latest version** *(satisfying `package.json` semantic versioning rules)* and **updates the entry** in `package.json` file `dependencies` |
| `npm update karma -g` | If `karma` package was installed **globally** with `npm install karma -g` or `npm install karma@latest -g` it **updates** `karma` package to the **latest version**. If `karma` package was installed **globally** with `npm install karma@1.6.0 -g` or `npm install karma@1.7.1 -g` it does **not update** `karma` package to the **latest version** *(because there is no global `package.json` file that indicates the acceptable versions range)* |
| `npm update -g` | **Updates** all **globally** installed packages to the **latest version** *(does not install missing packages, because there is no global `package.json` file)* |
| `npm update karma babel -g` | **Updates** `karma` and `babel` packages to the **latest version** |

###### [#top](#cli-commands)
###### npm prune
| `npm prune` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm prune` | Removes all **extraneous** packages from `node_modules` directory; If the `node_modules` directory **contains** the package, that **is not listed** as `package.json` dependency, the console returns this package as **extraneous**. |
| `npm prune --production` | Removes all packages that are listed in `package.json` file as **devDependencies**. Does **not remove** entries on the list of `devDependencies` in `package.json` file. |

###### [#top](#cli-commands)
###### npm dedupe
| `npm dedupe` `npm ddp` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm dedupe` | Searches the local **package tree** in the local `node_modules` directory and attempts to **simplify** the overall **structure** automatically; *(removes duplicated subdependencies and replaces them by the one top-level dependency. The deduplication algorithm walks through the tree, moving each dependency as far up in the tree as possible)* |

###### [#top](#cli-commands)
###### npm view
| `npm view` | description |
|:---:|:---|
| `npm view lodash` | Returns the information about the **latest version** of `lodash` package: `name` `version` `versions` `dist-tags` `author` `license` `description` `main` `dependencies` `devDependencies` `scripts` `time` `keywords` `maintainers` |
| `npm view lodash@4.15.0` | Returns the information about `4.15.0` version of `lodash` package |
| `npm view lodash name` | Returns the **name** of the `lodash` package at the`latest` version |
| `npm view lodash description` | Returns the **description** of the `lodash` package at the `latest` version |
| `npm view lodash keywords` | Returns the **keywords** array of the `lodash` package at the `latest` version |
| `npm view lodash version` | Returns the **version** of the `latest` version of `lodash` |
| `npm view lodash name version description` | Returns the **name**, **version** and **description** of the `lodash` package at the `latest` version |
| `npm view lodash@"^ 4.4.0" version` | Returns the information about **all minor versions** of the `lodash` package at  `4.4.0` version; *eg. `4.5.0` `4.5.1` `4.6.0` ... `4.17.4`* |
| `npm view lodash@"~4.11.0" version` | Returns the information about **all patch versions** of the `lodash` package at `4.11.0` version; *eg. `4.11.0` `4.11.1` `4.11.2`* |
| `npm view lodash versions` | Returns the information about **all published** versions of the `lodash` package |
| `npm view lodash dist-tags` | Returns the information about **all tags** attached to the particular version of `lodash` package |
| `npm view lodash dist-tags.latest` | Returns the version of `lodash` package that has the `latest` **tag** attached |
| `npm view lodash author` | Returns the information about the **author** *(name, email, url)* of the `lodash` package |
| `npm view lodash author.name` | Returns the **name** of the **author** of the `lodash` package |
| `npm view lodash author.email` | Returns the **email** of the **author** of the `lodash` package |
| `npm view lodash author.url` | Returns the **url** of the **author** of the `lodash` package |
| `npm view lodash contributors` | Returns the list of **contributors** *(names, emails)* of the `lodash` package |
| `npm view lodash contributors.name` | Returns the list of **contributors' names** of the `lodash` package |
| `npm view lodash contributors.email` | Returns the list of **contributors' emails** of the `lodash` package |
| `npm view lodash license` | Returns the license type *(eg. `MIT`)* of the `lodash` package |
| `npm view lodash main` | Returns the **main** property from the `package.json` file *(entry point to the program, eg. `index.js`)* |
| `npm view lodash dependencies` | Returns the **dependencies** of the `lodash` package |
| `npm view jasmine-core@$(npm view jasmine dependencies.jasmine-core) version` | Returns the versions of `jasmine-core` package that satisfies `jasmine` package's `dependencies` semantic versioning range for `jasmine-core` as its dependency |
| `npm view angular-cli@"^ 1.0.0-beta" dependencies.webpack` | Returns the versions of `webpack` package that is required as a dependency of the `angular-cli` package of each version equal to or higher than `1.0.0-beta` |
| `npm view jquery devDependencies` | Returns the list of **devDependencies** of the `jquery` package |
| `npm view lodash repository` | Returns the information about the **repository** of the `lodash` package |
| `npm view lodash repository.type` | Returns the **repository type** *(eg. `GIT`)* of the `lodash` package |
| `npm view lodash repository.url` | Returns the **repository URL** *(eg. `git+https://github.com/lodash/lodash.git`)* of the `lodash` package |
| `npm view lodash scripts` | Returns the list of **scripts** of the `lodash` package added to the `package.json` file `"scripts"` object |
| `npm view jasmine time.modified` | Returns the **date and time** when the `jasmine` package was modified last time |
| `npm view jasmine time.created` | Returns the list of **dates and time** when each version of the `jasmine` package was published  |

###### [#top](#cli-commands)
###### npm search
| `npm search` `npm s` `npm se` `npm find` | description |
|:---:|:---|
| `npm search angular` | Searches the registry for packages matching the `angular` term. Returns the data as a table with `name`, `description`, `author`, `date`, `version`, `keywords`. Returns `angular`, `@angular/core`, `@angular/common`, `@angular/compiler`, `@angular/router` etc. |
| `npm search karma jasmine reporter` | Searches the registry for packages matching the `karma`, `jasmine` and `reporter` terms. Returns the results with **colored matches** |
| `npm search babel` | Searches the registry for packages matching the `babel` term. Returns `Babel`, `babel-runtime`, `babel-core`, `babel-preset-es2015`, `babel-polyfill`, `babel-register`, `babel-cli`, etc. |
| `npm search angular --no-description` | **Disables** search matching in package's **descriptions**. Returns the data as a table with `name`, `author`, `date`, `version`, `keywords` |
| `npm search babel --searchopts="plugin transform"` | Passes **extended pattern** to search. Returns `babel-plugin-transform-regenerator`, `babel-plugin-transform-runtime`, `babel-plugin-transform-class-properties`, `babel-plugin-transform-es2015-destructuring`, etc. |
| `npm search karma --searchopts="reporter"` | Passes **extended pattern** to search. Returns `karma-mocha-reporter`, `karma-spec-reporter`, `karma-junit-reporter`, etc. |
| `npm search angular --json` | Returns the data in a **JSON** format |
| `npm search angular --long`|  Returns the data as a table with **full package's descriptions**|
| `npm search angular --parseable` | Returns the data as a table with **tab-separated columns** for each row |

###### [#top](#cli-commands)
###### npm repo
| `npm repo` | description |
|:---:|:---|
| `npm repo jasmine` | Opens [Github](https://github.com/jasmine/jasmine-npm) `jasmine` **repository** in the browser *(if specified in the `package.json` file)* |
| `npm repo babel-cli` | Opens [Github](https://github.com/babel/babel/tree/master/packages/babel-cli) `babel-cli` **repository** in the browser *(if specified in the `package.json` file)* |
| `npm repo angular-cli` | Opens [Github](https://github.com/angular/angular-cli) `angular-cli` **repository** in the browser *(if specified in the `package.json` file)* |
| `npm repo jquery` | Opens [Github](https://github.com/jquery/jquery) `jquery` **repository** in the browser *(if specified in the `package.json` file)* |

###### [#top](#cli-commands)
###### npm docs
| `npm docs` `npm home` | description |
|:---:|:---|
| `npm docs jasmine` | Opens `jasmine` **documentation** [url](https://jasmine.github.io/) in the browser |
| `npm home lodash` | Opens `lodash` **documentation** [url](https://lodash.com/) in the browser |
| `npm docs @angular/cli` | Opens `angular` **documentation** [url](https://github.com/angular/angular-cli) in the browser |
| `npm docs semver express webpack` | Opens `semver` [\[link\]](https://github.com/npm/node-semver#readme), `express` [\[link\]](http://expressjs.com/) and `webpack` [\[link\]](https://github.com/webpack/webpack) **documentation urls** in the browser |
| `npm docs`| Searches for a `package.json` file in the current folder and opens **documentation** url of this package |

###### [#top](#cli-commands)
###### npm whoami
| `npm whoami` | description |
|:---:|:---|
| `npm whoami` | Returns the **username**. This command requires to be logged in; [\[see npm login\]](#npm-login) |

###### [#top](#cli-commands)
###### npm owner
| `npm owner` | description |
|:---:|:---|
| `npm owner ls my-pckg` | Returns the **list of owners** of the `my-pckg` package *(users who are entitled to **modify** a package, **publish** its **new versions**, **add** new and **remove** other **owners**)* |
| `npm owner add user-name my-pckg` | **Adds** new owner `user-name` to the list of owners of the `my-pckg` package *(new owner is entitled to all above actions)*. You have to **be the owner** of `my-pckg` to undertake this action. |
| `npm owner rm user-name my-pckg` | **Removes** the owner `user-name` from the list of owners of the `my-pckg` package. You have to **be the owner** of `my-pckg` to undertake this action. |

###### [#top](#cli-commands)
###### npm login
| `npm login` `npm adduser` `npm add-user` | description |
|:---:|:---|
| `npm login` | **Creates** a new user or **verifies** *(log in)* existing user in the specified registry *(you have to log in in order to **publish**, **unpublish** or **deprecate** the package or to **add** and **remove** the owners of the package)* |

###### [#top](#cli-commands)
###### npm logout
| `npm logout` | description |
|:---:|:---|
| `npm logout` | When you are **logged** into a legacy registry that uses **username** and **password** authentication, it **clears the credentials** in your user configuration. |

###### [#top](#cli-commands)
###### npm version
| `npm version` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:-------------------------------:|:---|
| `npm version` | Returns the information about *(among others)* `node`, `v8` and `npm` installed **version** |
| `npm version major` | Bumps the **version** [\[major release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`1.0.0`; `1.4.2`➤`2.0.0`; `0.1.0-0`➤`1.0.0`; `1.4.2-5`➤`2.0.0` |
| `npm version minor` | Bumps the **version** [\[minor release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`0.2.0`; `1.4.2`➤`1.5.0`; `0.1.0-0`➤`0.1.0`; `1.4.2-5`➤`1.5.0` |
| `npm version patch` | Bumps the **version** [\[patch release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`0.1.1`; `1.2.15`➤`1.2.16`; `0.1.0-0`➤`0.1.0`; `1.4.2-5`➤`1.4.2` |
| `npm version premajor` | Bumps the **version** [\[premajor release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`1.0.0-0`; `1.4.2`➤`2.0.0-0`; `0.1.0-0`➤`1.0.0-0`; `1.4.2-5`➤`2.0.0-0` |
| `npm version preminor` | Bumps the **version** [\[preminor release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`0.2.0-0`; `1.4.2`➤`1.5.0-0`; `0.1.0-0`➤`0.2.0-0`; `1.4.2-5`➤`1.5.0-0` |
| `npm version prepatch` | Bumps the **version** [\[prepatch release\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`0.1.1-0`; `1.4.2`➤`1.4.3-0`; `0.1.0-0`➤`0.1.1-0`; `1.4.2-5`➤`1.4.3-0` |
| `npm version prerelease` | Bumps the **version** [\[prerelease\]](#versioning-syntax) in the `package.json` file of the current package; eg. `0.1.0`➤`0.1.1-0`; `1.4.2`➤`1.4.3-0`; `0.1.0-0`➤`0.1.0-1`; `1.4.2-5`➤`1.4.2-6` |
| `npm version from-git` | Tries to read the latest git tag *(if git repository exists)*, use it as the new npm version and create git commit. **Steps**: Make some changes in repo; `git add .`; `git commit -m "new git commit"`; `git push`; `git tag v1.5.0 -a -m "new git tag"`; `git push origin v1.5.0`; `npm version from-git` *(bumps `package.json` version to `1.5.0` and creates new git commit with message `1.5.0`)*; `git push` *(push commit created by npm)* |
| `npm version from-git -m "npm update to version %s"` | Tries to read the latest git tag *(if git repository exists)*, use it as the new npm version and create git commit. **Steps**: Make some changes in repo; `git add .`; `git commit -m "new git commit"`; `git push`; `git tag v1.5.0 -a -m "new git tag"`; `git push origin v1.5.0`; `npm version from-git -m "npm update to version %s"` *(bumps `package.json` version to `1.5.0` and creates new git commit with message `npm update to version 1.5.0`)*; `git push` *(push commit created by npm)* |

###### [#top](#cli-commands)
###### npm dist-tag
| `npm dist-tag` | description |
|:---:|:---|
| `npm dist-tag add my-pckg@1.1.0 tag-name` | Adds **custom tag** `tag-name` to the `my-pckg` package of the released version `1.1.0`. The client can use `npm install my-pckg@1.1.0` or `npm install my-pckg@tag-name` to install the package `my-pckg` of the version `1.1.0`. If `tag-name` is assigned to another `my-pckg` version *(eg. `1.0.0`)*, it **switches custom tag** `tag-name` from the version `1.0.0` to the version `1.1.0` |
| `npm dist-tag add my-pckg@1.0.0 tag-a; npm dist-tag add my-pckg@1.0.0 tag-b` | Adds **multiple custom tags** `tag-a` and `tag-b` to the package `my-pckg` of the released version `1.0.0`. The client can use `npm install my-pckg@1.0.0` or `npm install my-pckg@tag-a` or `npm install my-pckg@tag-b` to install the package `my-pckg` of the version `1.0.0` |
| `npm dist-tag rm my-pckg tag-name` | Removes custom tag `tag-name` from the list of custom tags of the `my-pckg` package |
| `npm dist-tag ls my-pckg` | Returns the **list** of custom tags of the `my-pckg` package |

###### [#top](#cli-commands)
###### npm publish
| `npm publish` | description |
|:---:|:---|
| `npm publish` | Publishes the package to the registry from the current directory *(must contain valid `package.json` file)*  and adds the `latest` **default tag** to the published version. **Fails** if the package `name` and `version` combination already exists in the registry. |
| `npm publish "./path/to/package"` | Publishes the package to the registry from the **relative path** `path/to/package` directory *(must contain valid `package.json` file)* |
| `npm publish "C:/packages/my-pckg"` | Publishes the package to the registry from the **absolute path** `C:/packages/my-pckg` directory *(must contain valid `package.json` file)* |
| `npm publish --tag tag-name` | Adds the **custom tag** `tag-name` to the new release of the package and publishes it *(by default, npm publishes the package with the `latest` tag)* |
| `npm publish "my-pckg-1.2.5.tgz"` | Publishes the `my-pckg` package to the registry from **tarball file** `my-pckg-1.2.5.tgz` of the current directory. The `.tgz` file should contain valid `package.json` file. Use `npm pack` command to generate `.tgz` tarball package automatically [\[see npm pack\]](#npm-pack) |
| `npm publish "./path/to/package/my-pckg-1.2.5.tgz"` | Publishes the `my-pckg` package to the registry from **tarball file** `my-pckg-1.2.5.tgz` from the **relative path** `path/to/package` directory |
| `npm publish "C:/packages/my-pckg-1.2.5.tgz"` | Publishes the `my-pckg` package to the registry from **tarball file** `my-pckg-1.2.5.tgz` from the **absolute path** `C:/packages` directory |

###### [#top](#cli-commands)
###### npm deprecate
| `npm deprecate` *(uses semver ranges)* | description |
|:---:|:---|
| `npm deprecate my-pckg@"1.2.0" "critical bug"` | Provides a **deprecation warning** to all who attempt to install the `1.2.0` version of `my-pckg` package |
| `npm deprecate my-pckg@"1.1.0 \|\| 1.3.0" "critical bug"` | **Deprecates** the `1.1.0` **and** `1.3.0` version of `my-pckg` package |
|`npm deprecate my-pckg@">=0.2.0 < 0.2.4" "critical bug"`| **Deprecates** the `0.2.0`, `0.2.1`, `0.2.2`, `0.2.3` **but not** `0.2.4` *(and higher)* version of `my-pckg` package|
|`npm deprecate my-pckg@"0.2.2 - 1.0.0" "critical bug"`| **Deprecates** the `>=0.2.2 < 1.0.0` range of versions of `my-pckg` package |
|`npm deprecate my-pckg@"^0" "This version is deprecated. Install version ^1"`| **Deprecates** the `>=0.0.0 < 1.0.0` range of versions of `my-pckg` package |

###### [#top](#cli-commands)
###### npm unpublish
| `npm unpublish` | description |
|:---:|:---|
| `npm unpublish my-pckg --force` | Removes the `my-pckg` package with **all** published versions from the registry. Due to npm rules, unpublishing is only allowed with versions published in the **last 24 hours**. |
| `npm unpublish my-pckg@1.0.0` | Removes the `my-pckg` package of the `1.0.0` version from the registry *(semantic versioning rules and tags are not allowed)* |

###### [#top](#cli-commands)
###### npm pack
| `npm pack` | description |
|:---:|:---|
| `npm pack` | Packs the current package folder to the `.tgz` file *(eg. `my-pckg-2.6.0.tgz`)*. The current folder must contain valid `package.json` file. The `.tgz` file is created in the **current** location |
| `npm pack "./path/to/package"` | Packs the package from the **relative path** `path/to/package` directory to the `.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack "C:/packages"` |  Packs the package from the **absolute path** `C:/packages` directory to the `.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack jasmine` | Packs the `jasmine` package from the **registry** to the `.tgz` file *(eg. `jasmine-2.6.0.tgz`)*. The `.tgz` file is created in the **current** location |
| `npm pack jasmine lodash jquery` | Packs the `jasmine`, `lodash` and `jquery` packages from the **registry** to the `.tgz` files *(eg. `jasmine-2.6.0.tgz`, `lodash-4.17.4.tgz` and `jquery-3.2.1.tgz`)*. The `.tgz` files are created in the **current** location |
| `npm pack jasmine@2.5.0 lodash@4.14.0 jquery@2.2.0` | Packs the `jasmine`, `lodash` and `jquery` packages from the **registry** to the `jasmine-2.5.0.tgz`, `lodash-4.14.0.tgz` and `jquery-2.2.0.tgz` files. The `.tgz` files are created in the **current** location |
| `npm pack jasmine@">=2.0.0 < 2.4.0" lodash@"< 3.3.0" jquery@"2.1.*"` | Packs the `jasmine`, `lodash` and `jquery` packages from the **registry** to the `jasmine-2.3.2.tgz`, `lodash-3.2.0.tgz` and `jquery-2.1.4.tgz` files. The `.tgz` files are created in the **current** location |
| `npm pack https://github.com/jasmine/jasmine-npm/tarball/v2.6.0` | Packs the `jasmine` package from the **Github tarball** file to the `jasmine-2.6.0.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack https://github.com/jasmine/jasmine-npm/archive/v2.6.0.tar.gz` | Packs the `jasmine` package from the **Github tarball** file to the `jasmine-2.6.0.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack git://github.com/jasmine/jasmine-npm.git#v2.6.0` | Packs the `jasmine` package from **Git** with the **git protocol** to the `jasmine-2.6.0.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack jasmine/jasmine-npm` | Packs the `jasmine` package from [Github](https://github.com/jasmine/jasmine-npm) to eg. `jasmine-2.6.0.tgz` file. The `.tgz` file is created in the **current** location |
| `npm pack jasmine/jasmine-npm#v2.5.2` | Packs the `jasmine` package from [Github](https://github.com/jasmine/jasmine-npm/tree/v2.5.2) to the `jasmine-2.5.2.tgz` file. The `.tgz` file is created in the **current** location |

###### [#top](#cli-commands)
###### npm config
| `npm config` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm config get foo` `npm config set foo bar` | Each `npm config` command takes `set` or `get` **sub-command**. the `npm config get foo` retrieves the searching setting `foo` from one of `.npmrc` npm configuration files and prints out its value `bar`, while the `npm config set foo bar` assigns new value `bar` to the specified setting `foo` in one of `.npmrc` npm configuration files. |
| `npm config get globalconfig` | Returns the path to the `.npmrc` **globalconfig** *(global every-user configuration file)*, eg. `users/user_name/AppData/Roaming/npm/etc/.npmrc` |
| `npm config get userconfig` | Returns the path to the `.npmrc` **userconfig** *(per-user configuration file)*, eg. `users/user_name/.npmrc` *(its settings override the **globalconfig** `.npmrc` settings)* |
| `npm config set foo baz -g` | It **creates** *(if any **globalconfig** has been added before)* the `.npmrc` **globalconfig** *(global every-user configuration file)* in the **prefix** path, eg. `users/user_name/AppData/Roaming/npm/etc/.npmrc` and **adds** key-value pair `foo=baz` into this `.npmrc` file. This key-value data will be also stored as **environment variable** `npm_config_foo=baz`. This variable is available via node `process.env.npm_config_foo` *(eg. in the `foo.js` that is ran via `package.json` script, eg. `"scripts":{"get-foo":"node foo.js"}`)*|
| `npm config set foo bar` | It creates *(if any **userconfig** has been added before)* the `.npmrc` **userconfig** *(per-user configuration file)* in the **$HOME** path, eg. `users/user_name/.npmrc` and **adds** key-value pair `foo=bar` into this `.npmrc` file. The `foo=bar` has higher priority than `foo=baz` from **globalconfig**. This key-value data will be also stored as **environment variable** `npm_config_foo=bar` *(overrides global `baz`)*. This variable is available via node `process.env.npm_config_foo` *(eg. in the `foo.js` that is ran via `package.json` script, eg. `"scripts":{"get-foo":"node foo.js"}`)* |
|  | You can manually create `.npmrc` **project config** *(per-project configuration file)* in your **project root** directory *(as a sibling of `node_modules` and `package.json`)*. You can manually add key-value pair `foo=boo` into this `.npmrc` file. The `foo=boo` has higher priority than **userconfig** `foo=bar` and **globalconfig** `foo=baz` . This key-value data will be also stored as **environment variable** `npm_config_foo=boo` *(overrides user `bar` and global `baz`)*. This variable is available via node `process.env.npm_config_foo` *(eg. in the `foo.js` that is ran via `package.json` script, eg. `"scripts":{"get-foo":"node foo.js"}`)*. This variable is available only for the project, that `.npmrc` **project config** file is created in. |
| `npm config get foo` | Returns the `foo`'s value from `.npmrc` **project config** file *(if defines `foo`)*, otherwise from `.npmrc` **userconfig** file *(if defines `foo`)*, otherwise from `.npmrc` **globalconfig** file *(if defines `foo`)*, otherwise returns `undefined`|
| `npm config get foo -g` | Returns the `foo` value from `.npmrc` **userconfig** file *(if defines `foo`)*, otherwise from `.npmrc` **globalconfig** file *(if defines `foo`)*, otherwise returns `undefined` |
|  | You can create **per-package config** object in your `package.json` file, eg. `"config":{"foo":"baz"}`.  This key-value data will be also stored as **environment variable** `npm_package_config_foo=baz`. This variable is available via node `process.env.npm_package_config_foo` *(eg. in the `foo.js` that is ran via `package.json` script, eg. `"scripts":{"get-package-foo":"node foo.js"}`)* |
| `npm config set my-pckg:foo bar` | It creates **per-package config**. It is stored in per-user `.npmrc` configuration file as `my-pckg:foo=bar` key-value pair. It has higher priority than `"config":{"foo":"baz"}` **per-package config** object in your `package.json` file. This key-value data will be also stored as **environment variable** `npm_package_config_foo=bar` *(overrides `package.json`'s `baz`)* |
| `npm config edit` | Opens the `.npmrc` **userconfig** file in an editor. |
| `npm config edit -g` | Opens the `.npmrc` **globalconfig** file in an editor. |
| `npm config list` `npm config ls` | Shows the list of key-value pairs added in the project as **project config** *(from `.npmrc` pre-project configuration file - if exists)*, added as **userconfig**, eg. `npm config set foo bar` *(from `.npmrc` per-user configuration file - if exists)*, added as **globalconfig**, eg. `npm config set foo baz -g` *(from `.npmrc` global configuration file - if exists)* |
| `npm config list -l` `npm config ls -l` | Shows the list of **project config**, **userconfig**, **globalconfig** and **default values** *(set of configuration parameters that are internal to npm and are defaults if nothing else is specified)* |
| `npm config delete foo` | Deletes the key-value pair `foo=value` from `.npmrc` **userconfig** file |
| `npm config delete foo -g` | Deletes the key-value pair `foo=value` from `.npmrc` **globalconfig** file |
| `npm config get prefix` | Returns the path to the global `npm` directory *(where `npm install my-pckg -g` installs packages)*, *eg. `users/user_name/AppData/Roaming/npm`* |
| `npm config set init-author-name` | Sets the value that `npm init` should use by default for the `package.json` author's **name** |
| `npm config set init-author-email` | Sets the value that `npm init` should use by default for the `package.json` author's **email** |
| `npm config set init-author-url` | Sets the value that `npm init` should use by default for the `package.json` author's **homepage** |
| `npm config set init-license` | Sets the value that `npm init` should use by default for the `package.json` **license** |
| `npm config set init-version` | Sets the value that `npm init` should use by default for the `package.json` **version** number; the default is `1.0.0` |
| `npm config set long true` | If `long` setting is set to `true`, `npm ls` and `npm search package-name` will show extended information by default, as with `npm ls -l` and `npm search package-name -l` |
| `npm config set message "package.json version updated to %s"` | Sets the default **commit message** for `npm version from-git` [\[see npm version\]](#npm-version) *(`%s` is automatically replaced with version number, eg. `1.2.5`)* |
| `npm config set only dev` `npm config set only development` | `npm install` and `npm ls` will affect **only** packages specified in `package.json` **`devDependencies`** object *(by default `only=null` - the mentioned commands affects both `dependencies` and `devDependencies`)* |
| `npm config set only prod` `npm config set only production` | `npm install` and `npm ls` will affect **only** packages specified in `package.json` **`dependencies`** object *(by default `only=null` - the mentioned commands affects both `dependencies` and `devDependencies`)* |
| `npm config set production true` | Sets the "production mode"; `npm install` **will not install** modules specified in `package.json` **`devDependencies`** object. Installs packages specified in `package.json` **`dependencies`** and **`optionalDependencies`** objects |
| `npm config get registry` | Returns the base url of the npm package **registry**, eg. `https://registry.npmjs.org/` |
| `npm config set save true` | If `save` setting is set to `true`, the `npm install lodash` will add the entry to the `package.json` file *(if exists)* **`dependencies`** object by default. `npm uninstall lodash` will remove the entry from the `package.json` file *(if exists)* **`dependencies`** object by default |
| `npm config set save-dev true` | If `save-dev` setting is set to `true`, `npm install lodash` will add the entry to the `package.json` file *(if exists)* **`devDependencies`** object by default. `npm uninstall lodash` will remove the entry from the `package.json` file *(if exists)* **`devDependencies`** object by default |
| `npm config set save-optional true` | If `save-optional` setting is set to `true`, `npm install lodash` will add the entry to the `package.json` file *(if exists)* **`optionalDependencies`** object by default. `npm uninstall lodash` will remove the entry from the `package.json` file *(if exists)* **`optionalDependencies`** object by default |
| `npm config set save-exact true` | If `save-exact` setting is set to `true`, the `npm install jquery --save` or `npm install jquery --save-dev` will add the entry with **exact version number** to the `package.json` file *(if exists)* `dependencies` or `devDependencies` object as eg. `"jquery":"3.2.0"`, rather than semver range entry `"jquery":"^3.2.0"` or `"jquery":"~3.2.0"` |
| `npm config set save-prefix "~"` | Sets semver prefix that allows only patch upgrades. `npm install lodash --save` will add the entry to the `package.json` file `dependency` object as `"lodash":"~4.17.4"` rather than `"lodash":"^4.17.4"` *(default `^` that allows minor upgrades)* |
| `npm config get tmp` | Returns the path to the location where npm **temporary files** are stored on a program run *(and should be deleted upon successful exit)* |
| `npm config set unicode true` | Uses unicode characters *(rather than default ASCII characters)* to draw the **output trees**, eg. for `npm ls` |
| `npm config get cache` | Returns the path to the location of npm's **cache** directory, eg. `users/user_name/AppData/Roaming/npm-cache` |
| `npm config set depth 0` | Sets the **depth** to go when npm is recursing directories, eg. for `npm ls` or `npm outdated ` *(it will display only installed top-level packages list, without their dependencies)* |

###### [#top](#cli-commands)
###### npm prefix
| `npm prefix` | description |
|:---:|:---|
| `npm prefix` | Returns the **local prefix** *(the path to the root directory of current package, where valid `package.json` file exists)*; eg. `path/to/projects/my-pckg` |
| `npm prefix -g` `npm prefix --global` | Returns the **global prefix** *(the path to the global npm directory, where the packages are installed globally)*, eg. `users/user_name/AppData/Roaming/npm`. This is the equivalent of `npm config get prefix` |

###### [#top](#cli-commands)
###### npm root
| `npm root` | description |
|:---:|:---|
| `npm root` | Returns the **local** `node_modules` directory path; *eg. `path/to/projects/my-pckg/node_modules`* |
| `npm root -g` `npm root --global` | Returns the **global** `node_modules` directory path; *eg. `users/user_name/AppData/Roaming/npm/node_modules`* |

###### [#top](#cli-commands)
###### npm bin
| `npm bin` | description |
|:---:|:---|
| `npm bin` | Returns the path to the directory where npm installs **executables locally**; *eg. `path/to/projects/my-pckg/node_modules/.bin`* |
| `npm bin -g` `npm bin --global` | Returns the path to the directory where npm installs **executables globally**; *eg. `users/user_name/AppData/Roaming/npm`* |

###### [#top](#cli-commands)
###### npm -v
| `npm -v` | description |
|:---:|:---|
| `npm -v` | Returns the **current version** of `npm` package |

## Running scripts

#### CLI commands

###### [#top](#cli-commands)
###### npm run-script
| `npm run-script` `npm run` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm run-script` | Returns the **list of** availabe **scripts** from the `scripts` object of the `package.json` file |
|`npm run-script "get jasmine version"`| Assuming, that there is a `script:{"get jasmine version":"jasmine -v"}` in the `package.json` file and `jasmine` package is installed **locally** or **globally**, it runs `jasmine -v` command and returns the output message |
| `npm run js -- "index"` | Assuming, that there is a `script:{"js":"node"}` in the `package.json` file, it passes `index` as an **argument**, running `node "index"` command and executes `index.js` file|
| `npm run globals -- --depth=0` | Assuming, that there is a `script:{"globals":"npm ls -g"}` in the `package.json` file, it passes `--depth=0` as an **argument**, running `npm ls -g --depth=0` command. |
| `npm run env` | Prints out the list of environment variables, eg. `npm_config_*` *(where `*` is the name of the setting specified by the user in one of `.npmrc` npm configuration files)*, `npm_package_config_*` *(where `*` is the name of the setting specified by the user in the `"config"` object in `package.json` file)*, `npm_package_*` *(where `*` is the property name from the `package.json` file, eg. `npm_package_version`)*, `npm_package_dependencies_*` *(where `*` is the name of installed dependency)*, `npm_package_devDependencies_*` *(where `*` is the name of installed devDependency)*, `npm_package_scripts_*` *(where `*` is the name of script in the `package.json` `"scripts"` object)*, etc. Environment variable can be used in the script content, eg `"get-email":"echo %npm_package_author_email%"` *(for windows cmd)*. Environment variables are available via node, eg. `process.env.npm_package_version` *(eg. in the `version.js` that is ran via `package.json` script, eg. `"scripts":{"get-current-version":"node version.js"}`)*|

###### [#top](#cli-commands)
###### npm test
| `npm test` `npm run-script test` | description |
|:---:|:---|
| `npm test` | This is the equivalent of `npm run-script test`. It runs `"test"` script from the `package.json` `"scripts"` object. |

###### [#top](#cli-commands)
###### npm install-test
| `npm install-test` | description |
|:---:|:---|
| `npm install-test` | It triggers the `test` script of the current `package.json` file **after** all `dependencies` and `devDependencies` installation. |
| `npm install-test lodash` | It triggers the `test` script of the current `package.json` file **after** `lodash` package installation. |

###### [#top](#cli-commands)
###### npm start
| `npm start` `npm run-script start` | description |
|:---:|:---|
| `npm start` | This is the equivalent of `npm run-script start`. It runs `"start"` script from the `package.json` `"scripts"` object. |

###### [#top](#cli-commands)
###### npm stop
| `npm stop` `npm run-script stop` | description |
|:---:|:---|
| `npm stop` | This is the equivalent of `npm run-script stop`. It runs `"stop"` script from the `package.json` `"scripts"` object. |

###### [#top](#cli-commands)
###### npm restart
| `npm restart` `npm run-script restart` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | description |
|:---:|:---|
| `npm restart` | This is the equivalent of `npm run-script restart`. If `restart` is not overridden in `package.json` `"scripts"` object, it triggers the cycle of scripts in the following order *(if specified)*: `prerestart` `prestop` **`stop`** `poststop` `prestart` **`start`** `poststart` `postrestart` |

#### pre-scripts and post-scripts

| | description |
|:---:|:---|
| `premyscript` | Assuming, that there is `scripts:{"premyscript":"...","myscript":"..."}` in the `package.json` file, npm runs `premyscript` script **before** the user's `"myscript"` script on `npm run myscript` command |
| `postmyscript` | Assuming, that there is `scripts:{"postmyscript":"...","myscript":"..."}` in the `package.json` file, npm runs `postmyscript` script **after** the user's `"myscript"` script on `npm run myscript` command |
| `"preget email"` | Assuming, that there is `scripts:{"preget email":"...","get email":"..."}` in the `package.json` file, npm runs `"preget email"` script **before** the user's `"get email"` script on `npm run "get email"` command |
| `"postget email"` | Assuming, that there is `scripts:{"postget email":"...","get email":"..."}` in the `package.json` file, npm runs `"postget email"` script **after** the user's `"get email"` script on `npm run "get email"` command |
| `prepublishOnly` | Runs **before** `npm publish` |
| `publish` `postpublish` | Runs **after** `npm publish` |
| `preinstall` | If it is the script of `package-name` that is about to be installed, it runs **before** `npm install package-name`. If it is the script of current `package.json` file, it runs **before** `npm install` *(without any arguments)*. |
| `install` `postinstall` | If it is the script of `package-name` that is about to be installed, it runs **after** `npm install package-name`. If it is the script of current `package.json` file, it runs **after** `npm install` *(without any arguments)*. |
| `preuninstall` | If it is the script of `package-name` that is about to be uninstalled, it runs **before** `npm uninstall package-name`. |
| `uninstall` `postuninstall` | If it is the script of `package-name` that is about to be uninstalled, it runs **after** `npm uninstall package-name`. |
| `preversion` | Runs **before** `npm version patch`, `npm version minor`, etc. |
| `version` `postversion` | Runs **after** `npm version patch`, `npm version minor`, etc. |
| `pretest` | Runs **before** `npm test` or `npm run test` |
| `posttest` | Runs **after** `npm test` or `npm run test` |
| `prestop` | Runs **before** `npm stop` or `npm run stop` |
| `poststop` | Runs **after** `npm stop` or `npm run stop` |
| `prestart` | Runs **before** `npm start` or `npm run start` |
| `poststart` | Runs **after** `npm start` or `npm run start` |
| `prerestart` | Runs **before** `npm restart` or `npm run restart` |
| `postrestart` | Runs **after** `npm restart` or `npm run restart` |

## Versioning rules

#### Versioning syntax
| `versioning rule` | description |
|:---:|:---|
| `0.1.0` | **Major version zero** is for initial development. The public API should not be considered stable|
| `1.0.0` | The stable project should start at `1.0.0` version |
| `1.0.1` `1.0.2` `1.0.3` | **Patch release**: Implements **bug fixes** and other minor changes *(you should install all new patch releases!)* |
| `1.0.0` `1.1.0` `1.2.0` | **Minor release**: Implements **new features** which **don't break** existing features *(if you want to use new features implemented in the new minor release, you can install new minor release without worrying, that this new release would break your application)* |
| `1.0.0` `2.0.0` `3.0.0` | **Major  release**: Implements changes that **break backwards compatibility** *(you should be aware, that new major release can breake your application)* |
| `1.0.0-alpha` `1.0.0-alpha.1` `1.0.0-0.3.7` `1.0.0-x.7.z.92` `1.0.0-1235` | Additional labels for **pre-release** *(A pre-release version indicates that the version is unstable and might not satisfy the intended compatibility requirements as denoted by its associated normal version)* |
| `1.0.0-alpha+001` `1.0.0+20130` `1.0.0-beta+exp.sha.5114f85` | Additional labels for **build metadata** *(follows the **patch version** or **pre-release** version)* |

#### Versions precedence rules
| `precedence rules` | description |
|:---:|:---|
| `1.0.0 < 2.0.0 < 2.1.0 < 2.1.1` | Precedence is determined by the first difference when comparing each of these identifiers from left to right |
| `1.0.0-alpha < 1.0.0` | When major, minor, and patch are equal, a pre-release version has **lower precedence** than a normal version |
|`1.0.0-alpha+001 < 1.0.0-alpha+002 < 1.0.0-beta+001 < 1.0.0` | Precedence for two pre-release versions with the same major, minor, and patch version **must** be determined by comparing each dot separated identifier from left to right until a difference is found |
| `1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.` | A larger set of pre-release fields has a higher precedence than a smaller set, if all of the preceding identifiers are equal |

#### The `semver` package
Run in the bash:
```bash
> npm install semver
> node
```
When **node** is run in the bash:
```javascript
var s = require('semver');

//checks whether this is a valid version syntax
//if true, returns parsed version, otherwise returns null
s.valid('1.2.3-alfa.1.2'); //'1.2.3-alfa.1.2'
s.valid('0.0.0'); //'0.0.0'
s.valid('*.*.*'); //null
s.valid('2.b'); //null

//returns the version incremented by the release type
s.inc('1.33.2','major'); //'2.0.0'
s.inc('0.1.2-alfa','major'); //'1.0.0'
s.inc('1.6.22','minor'); //'1.7.0'
s.inc('1.6.5-beta','minor'); //'1.7.0'
s.inc('1.0.2','patch'); //'1.0.3'
s.inc('1.0.2-alfa','patch'); //'1.0.2'
s.inc('1.5.2','premajor'); //'2.0.0-0'
s.inc('2.5.2-33','premajor'); //'3.0.0-0'
s.inc('1.2.6','preminor'); //'1.3.0-0'
s.inc('2.0.6-15','preminor'); //'2.1.0-0'
s.inc('2.0.6','prepatch'); //'2.0.7-0'
s.inc('0.2.4','prepatch'); //'0.2.5-0'
s.inc('0.2.4','prerelease'); //'0.2.5-0'
s.inc('0.2.4-alfa','prerelease'); //'0.2.4-alfa.0'
s.inc('0.2.4-33','prerelease'); //'0.2.4-34'

//returns an array of prerelease components, or null if none exist
s.prerelease('1.2.5'); //null
s.prerelease('1.2.5-alfa'); //['alfa']
s.prerelease('1.2.5-alfa-5.22.3'); //['alfa-5', 22, 3]
s.prerelease('1.2.5-3.5.beta'); //[3, 5, 'beta']

//returns the major, minor or patch version number
s.major('2.5.22'); //2
s.minor('2.5.22'); //5
s.patch('2.5.22'); //22

//checks whether the first version is greater than the second one
s.gt('1.2.3','1.0.0'); //true
s.gt('2.5.0','2.5.0-alfa'); //true
s.gt('2.2.0-alfa','2.2.0-beta'); //false
s.gt('1.0.0','1.0.0'); //false

//checks whether the first version is greater or equal than the second one
s.gte('1.2.3','1.0.0'); //true
s.gte('1.0.0','1.0.0'); //true

//checks whether the first version is lower than the second one
s.lt('1.0.0','1.2.3'); //true
s.lt('2.5.0-alfa','2.5.0'); //true
s.lt('2.2.0-beta','2.2.0-alfa'); //false
s.lt('1.0.0','1.0.0'); //false

//checks whether the first version is lower or equal than the second one
s.lte('1.0.0','1.2.3'); //true
s.lte('1.0.0','1.0.0'); //true

//checks if two versions are logically equivalent (==), even if they're not the exact same string
s.eq('1.3.0','1.3.0'); //true
s.eq('1.3.0','1.3.3'); //false

//checks if two versions are NOT logically equivalent (==)
s.neq('1.3.0','1.3.0'); //false
s.neq('1.3.0','1.3.3'); //true

//compares two versions with the chosen passed comparator
s.cmp('2.0.0','>', '2.0.5'); //false
s.cmp('2.0.0','<', '2.0.5'); //true
s.cmp('2.0.5','>=', '2.0.5'); //true
s.cmp('2.0.5','<=', '2.0.5'); //true
s.cmp('2.0.5','==', '2.0.5'); //true
s.cmp('2.0.5','!==', '2.0.5'); //false

//compares two versions and returns 1, -1 or 0 if the first version is greater, lower or equal to the second one
s.compare('2.0.0','1.0.0'); //1
s.compare('1.0.0','2.0.0'); //-1
s.compare('2.0.0','2.0.0'); //0

//returns difference between two versions by the release type
s.diff('1.3.0', '2.2.0'); //'major'
s.diff('2.3.0', '2.2.0'); //'minor'
s.diff('2.2.5', '2.2.6'); //'patch'
s.diff('2.2.5', '3.0.0-alfa'); //'premajor'
s.diff('2.2.5', '2.5.0-alfa'); //'preminor'
s.diff('2.2.5', '2.2.6-alfa'); //'prepatch'
s.diff('2.2.5', '2.2.5-alfa'); //'prerelease'

//returns the range of passed semver rule
s.validRange('2.0.0'); //'2.0.0'
s.validRange('^2'); //'>=2.0.0 <3.0.0'
s.validRange('^0.3.0'); //'>=0.3.0 <0.4.0'
s.validRange('^0.0.5'); //'>=0.0.5 <0.0.6'
s.validRange('2.x'); //'>=2.0.0 <3.0.0'
s.validRange('2.3.x'); //'>=2.3.0 <2.4.0'
s.validRange('^2.3.5-alfa'); //'>=2.3.5-alfa <3.0.0'
s.validRange('~2.3.5-alfa'); //'>=2.3.5-alfa <2.4.0'

//returns true if the version satisfies the range
s.satisfies('1.5.0','^1.0.0'); //true
s.satisfies('2.3.33','2.3.x'); //true
s.satisfies('1.5.4','1.5.* - 1.7.*'); //true
s.satisfies('1.8.0','1.5 - 1.7'); //false

//returns the highest version in the list that satisfies the range, or null if none of them do
s.maxSatisfying(['2.5.0','2.7.11','2.7.11-beta'],'^2.5.0'); //'2.7.11'
s.maxSatisfying(['2.5.0-built.1.2','2.5.0','3.0.0'],'2'); //'2.5.0'
s.maxSatisfying(['1.3.0','2.0.0'],'^2.5.0'); //null

//returns the lowest version in the list that satisfies the range, or null if none of them do
s.minSatisfying(['1.2.2','1.3.3'],'>=1.0.0 < 2.0.0'); //'1.2.2'
s.minSatisfying(['2.1.0-built','2.2.0','2.5.55-alfa'],'>=2.0.0 < 3.0.0'); //'2.2.0'
s.minSatisfying(['2.3.1','2.3.33','2.4.0'],'~2.3'); //'2.3.1'

//returns true if the version is greater than range
s.gtr('2.4.0','~2.3.*'); //true
s.gtr('3.3.0','3.2'); //true
s.gtr('3.0.0','3.0.0-alfa'); //true
s.gtr('3.0.0-alfa','3.0.0'); //false

//returns true if the version is lower than range
s.ltr('2.0.0','>2.0.0'); //true
s.ltr('2.5.0','^2.5.0'); //false
s.ltr('2.55.0-beta','2.54.0'); //false

//returns true if the version is higher or lower than range 
s.outside('2.0.0','>=1.3.0 < 1.8.0','>'); //true
s.outside('2.0.0','>=1.3.0 < 1.8.0','<'); //false
s.outside('1.0.0','>=1.3.0 < 1.8.0','>'); //false
s.outside('1.0.0','>=1.3.0 < 1.8.0','<'); //true
```

#### Version's ranges
| version notation | satisfies | not satisfy |
|:---:|:---:|:---:|
| `2.0.0` | `2.0.0` | `2.0.1` `2.1.1` `1.0.0` `3.0.0` `2.0.0-alfa` |
| `*` `""` `x` `X` `X.x.*` `x.5.9` `x.9.9` `>=0.0.0` | `0.0.0` `0.1.0` `1.0.0` `5.55.999` | `1.0.0-alfa` `2.5.3-beta` |
| `2.0` `2.0.x` `2.0.X` `2.0.*`  `>=2.0.0 <2.1.0` | `2.0.0` `2.0.1` `2.0.55` | `2.0.0-alfa` `2.1.0` `2.5.0` `3.0.0` |
| `4` `4.x` `4.X` `4.*` `4.x.x` `4.X.X` `4.x.X` `4.*.X` `4.x.1` `4.x.5` `4.x.99` `>=4.0.0 <5.0.0` | `4.0.0` `4.0.1` `4.1.1` `4.5.99` `4.99.999` | `3.0.0` `3.9.9` `4.0.0-alfa` `5.0.0` |
| `>=1.2.7` | `1.2.7` `1.2.8` `2.5.3` `1.3.9` | `1.2.6` `1.1.0` |
| `>=1.2.7 <1.3.0` | `1.2.7` `1.2.8` `1.2.99` | `1.2.6` `1.3.0` `1.1.0` |
| `1.2.7 \|\| >=1.2.9 <2.0.0` | `1.2.7` `1.2.9` `1.4.6` | `1.2.8` `2.0.0` |
| `>1.2.2-ab` | `1.2.2-aba` `1.2.2-ac` `1.2.2-b` `1.2.2-ab1` `1.2.2-ab.1` | `1.2.2-a` `1.2.2-a.b` `1.2.2-a.1` |
| `>1.2.2-alfa.1` | `1.2.2-alfa.2` `1.2.2-beta` `1.2.2` `1.2.3` `1.3.3` | `1.2.3-alfa` `1.2.3-beta` `1.3.3-alfa` `2.3.3-alfa` |
|`1.2.3 - 2.3.4` `>=1.2.3 <=2.3.4`| `1.2.3` `2.3.4` `1.3.3` `2.0.0` `2.2.1` | `1.2.2` `2.3.5` `1.2.3-alfa` `2.3.4-alfa` `1.2.3-alfa` `2.0.0-alfa`|
| `2 - 2.3.0` `2.0.0 - 2.3.0` `>=2 <=2.3.0` | `2.0.0` `2.3.0` `2.1.1` `2.2.55` | `2.0.0-alfa` |
| `2.0.0 - 2.3` `>=2.0.0 <=2.3` `>=2.0.0 <2.4.0` | `2.0.0` `2.3.0` `2.3.1` `2.3.99` | `2.4.0` `2.3.1-alfa` |
| `2.0.0 - 3` `>=2.0.0 <=3` `>=2.0.0 <4.0.0` | `2.0.0` `2.3.0` `2.9.9` `3.0.0` `3.1.1` `3.9.5` | `4.0.0` `2.0.0-alfa` `2.9.9-alfa` |
| `~1.2.3` `>=1.2.3 <1.3.0` | `1.2.3` `1.2.4` `1.2.99` | `1.2.0` `1.2.2` `1.2.3-alfa` `1.3.0` |
| `~1.2` `>=1.2.0 < 1.3.0` `1.2.x` `1.2` | `1.2.0` `1.2.1` `1.2.99` | `1.2.0-alfa` `1.3.0` `1.1.0` `1.1.99` |
| `~3` `>=3.0.0 <4.0.0` `3` `3.x` | `3.0.0` `3.0.1` `3.1.1` `3.5.55` | `3.0.0-alfa` `4.0.0` `2.0.0` `2.9.9` |
| `~1.2.3-alfa.1.2` | `1.2.3` `1.2.4` `1.2.99` `1.2.3-alfa.1.3` `1.2.3-beta` | `1.3.0` `1.2.2` `2.0.0` `1.2.4-alfa.1.2` `1.2.3-alfa.1.1` `1.2.3-alfa` |
| `^1.2.3` `>=1.2.3 < 2.0.0` | `1.2.3` `1.2.23` `1.2.4` `1.2.99` `1.3.0` `1.9.5` `1.99.55`  | `1.2.3-alfa` `2.0.0` `1.2.2` `1.0.0` |
| `^0.5.5` `>=0.5.5 <0.6.0` | `0.5.5` `0.5.6` `0.5.55` `0.5.45` | `0.5.5-alfa` `0.6.0` `0.5.4` `0.4.0` `1.0.0` `0.4.99` |
| `^0.0.3` `>=0.0.3 < 0.0.4` | `0.0.3` | `0.0.4` `0.0.3-alfa` `0.0.4-alfa` `0.0.44` `0.1.0` `1.0.0` |
| `^2.2.0` `^2.2` `^2.2.*` `^2.2.x` `^2.2.X` `>=2.2.0 <3.0.0` | `2.2.0` `2.2.1` `2.3.0` `2.3.55` `2.9.9` | `2.2.0-alfa` `3.0.0` `2.1.0` `2.1.99` |
| `^3.0.0` `>=3.0.0 <4.0.0` `3` `3.x` `3.x.x` `3.*.*` | `3.0.0` `3.0.1` `3.1.0` `3.5.5` `3.99.999`  | `3.0.0-alfa` `4.0.0` `2.0.0` `2.9.99` |
| `^1.2.3-alfa.1.2` | `1.2.3` `1.2.4` `1.2.99` `1.3.0` `1.9.99` `1.2.3-alfa.2.2` `1.2.3-beta.1.1`  | `1.2.2` `2.0.0` `1.2.3-a` `1.2.3-alfa` `1.2.3-alfa.1.1` |

#### `npm install` versioning rules
All lodash versions *(and `dist-tags`)*:

| `npm view lodash versions` `npm view lodash "dist-tags"`|
|:---:|
| `0.1.0` `0.2.0` `0.2.1` `0.2.2` `0.3.0` `0.3.1` `0.3.2` `0.4.0` `0.4.1` `0.4.2` `0.5.0-rc.1` `0.5.0` `0.5.1` `0.5.2` `0.6.0` `0.6.1` `0.7.0` `0.8.0` `0.8.1` `0.8.2` `0.9.0` `0.9.1` `0.9.2` `0.10.0` `1.0.0-rc.1` `1.0.0-rc.2` `1.0.0-rc.3` `1.0.0` `1.0.1` `1.0.2` `1.1.0` `1.1.1` `1.2.0` `1.2.1` `1.3.0` `1.3.1` `2.0.0` `2.1.0` `2.2.0` `2.2.1` `2.3.0` `2.4.0` `2.4.1` `2.4.2` `3.0.0` `3.0.1` `3.1.0` `3.2.0` `3.3.0` `3.3.1` `3.4.0` `3.5.0` `3.6.0` `3.7.0` `3.8.0` `3.9.0` `3.9.1` `3.9.2` `3.9.3` `3.10.0` `3.10.1` `4.0.0` `4.0.1` `4.1.0` `4.2.0` `4.2.1` `4.3.0` `4.4.0` `4.5.0` `4.5.1` `4.6.0` `4.6.1` `4.7.0` `4.8.0` `4.8.1` `4.8.2` `4.9.0` `4.10.0` `4.11.0` `4.11.1` `4.11.2` `4.12.0` `4.13.0` `4.13.1` `4.14.0` `4.14.1` `4.14.2` `4.15.0` `4.16.0` `4.16.1` `4.16.2` `4.16.3` `4.16.4` `4.16.5` `4.16.6` `4.17.0` `4.17.1` `4.17.2` `4.17.3` `4.17.4 {latest}` |

Assume, that you install `lodash` package `npm install lodash@<version>`. Compare and find out, which version of `lodash` is actually installed with the different semver rules passed to the `npm install lodash@<version>` command:

| `npm install lodash@ver` | installed version | `npm install lodash@^ver` | installed version | `npm install lodash@~ver` | installed version | 
|:---:|:---:|:---:|:---:|:---:|:---:|
|`npm install lodash`|`lodash@4.17.4`|||||
|`npm install lodash@*`|`lodash@4.17.4`|`npm install lodash@^*`|`lodash@4.17.4`|`npm install lodash@~*`|`lodash@4.17.4`|
|`npm install lodash@latest`|`lodash@4.17.4`|||||
|`npm install lodash@X`|`lodash@4.17.4`|`npm install lodash@^X`|`lodash@4.17.4`|`npm install lodash@~X`|`lodash@4.17.4`|
|`npm install lodash@x`|`lodash@4.17.4`|`npm install lodash@^x`|`lodash@4.17.4`|`npm install lodash@~x`|`lodash@4.17.4`|
|`npm install lodash@*.*.*`|`lodash@4.17.4`|`npm install lodash@^*.*.*`|`lodash@4.17.4`|`npm install lodash@~*.*.*`|`lodash@4.17.4`|
|`npm install lodash@x.x.x`|`lodash@4.17.4`|`npm install lodash@^x.x.x`|`lodash@4.17.4`|`npm install lodash@~x.x.x`|`lodash@4.17.4`|
|`npm install lodash@x.x.2`|`lodash@4.17.4`|`npm install lodash@^x.x.2`|`lodash@4.17.4`|`npm install lodash@~x.x.2`|`lodash@4.17.4`|
|`npm install lodash@x.x.3`|`lodash@4.17.4`|`npm install lodash@^x.x.3`|`lodash@4.17.4`|`npm install lodash@~x.x.3`|`lodash@4.17.4`|
|`npm install lodash@x.5`|`lodash@4.17.4`|`npm install lodash@^x.5`|`lodash@4.17.4`|`npm install lodash@~x.5`|`lodash@4.17.4`|
|`npm install lodash@x.15`|`lodash@4.17.4`|`npm install lodash@^x.15`|`lodash@4.17.4`|`npm install lodash@~x.15`|`lodash@4.17.4`|
|`npm install lodash@0`|`lodash@0.10.0`|`npm install lodash@^0`|`lodash@0.10.0`|`npm install lodash@~0`|`lodash@0.10.0`|
|`npm install lodash@0.x`|`lodash@0.10.0`|`npm install lodash@^0.x`|`lodash@0.10.0`|`npm install lodash@~0.x`|`lodash@0.10.0`|
|`npm install lodash@0.x.x`|`lodash@0.10.0`|`npm install lodash@^0.x.x`|`lodash@0.10.0`|`npm install lodash@~0.x.x`|`lodash@0.10.0`|
|`npm install lodash@0.8`|`lodash@0.8.2`|`npm install lodash@^0.8`|`lodash@0.8.2`|`npm install lodash@~0.8`|`lodash@0.8.2`|
|`npm install lodash@0.8.x`|`lodash@0.8.2`|`npm install lodash@^0.8.x`|`lodash@0.8.2`|`npm install lodash@~0.8.x`|`lodash@0.8.2`|
|`npm install lodash@0.8.1`|`lodash@0.8.1`|`npm install lodash@" ^0.8.1"`|`lodash@0.8.2`|`npm install lodash@~0.8.1`|`lodash@0.8.2`|
|`npm install lodash@1`|`lodash@1.3.1`|`npm install lodash@^1`|`lodash@1.3.1`|`npm install lodash@~1`|`lodash@1.3.1`|
|`npm install lodash@1.x`|`lodash@1.3.1`|`npm install lodash@^1.x`|`lodash@1.3.1`|`npm install lodash@~1.x`|`lodash@1.3.1`|
|`npm install lodash@1.x.x`|`lodash@1.3.1`|`npm install lodash@^1.x.x`|`lodash@1.3.1`|`npm install lodash@~1.x.x`|`lodash@1.3.1`|
|`npm install lodash@1.0`|`lodash@1.0.2`|`npm install lodash@" ^1.0"`|`lodash@1.3.1`|`npm install lodash@~1.0`|`lodash@1.0.2`|
|`npm install lodash@1.0.x`|`lodash@1.0.2`|`npm install lodash@" ^1.0.x"`|`lodash@1.3.1`|`npm install lodash@~1.0.x`|`lodash@1.0.2`|
|`npm install lodash@1.0.0`|`lodash@1.0.0`|`npm install lodash@" ^1.0.0"`|`lodash@1.3.1`|`npm install lodash@~1.0.0`|`lodash@1.0.2`|
|`npm install lodash@2`|`lodash@2.4.2`|`npm install lodash@^2`|`lodash@2.4.2`|`npm install lodash@~2`|`lodash@2.4.2`|
|`npm install lodash@3`|`lodash@3.10.1`|`npm install lodash@^3`|`lodash@3.10.1`|`npm install lodash@~3`|`lodash@3.10.1`|
|`npm install lodash@3.x`|`lodash@3.10.1`|`npm install lodash@^3.x`|`lodash@3.10.1`|`npm install lodash@~3.x`|`lodash@3.10.1`|
|`npm install lodash@3.x.x`|`lodash@3.10.1`|`npm install lodash@^3.x.x`|`lodash@3.10.1`|`npm install lodash@~3.x.x`|`lodash@3.10.1`|
|`npm install lodash@3.9`|`lodash@3.9.3`|`npm install lodash@" ^3.9"`|`lodash@3.10.1`|`npm install lodash@~3.9`|`lodash@3.9.3`|
|`npm install lodash@3.9.x`|`lodash@3.9.3`|`npm install lodash@" ^3.9.x"`|`lodash@3.10.1`|`npm install lodash@~3.9.x`|`lodash@3.9.3`|
|`npm install lodash@3.9.2`|`lodash@3.9.2`|`npm install lodash@^3.9.2`|`lodash@3.10.1`|`npm install lodash@~3.9.2`|`lodash@3.9.3`|

## The `.npmignore` rules
Create the `.npmignore` file in your package's **root** folder *(or any subfolder of your package)*. When `.npmignore` is not present, the `.gitignore` is used instead.

| `.npmignore` `.gitignore` rules | description |
|:---:|:---|
| `.npmrc` `.git` `node_modules` | These paths and files are ignored by default  |
| `package.json` `README` `LICENSE` | These paths and files are never ignored *(adding them to `.npmignore` is pointless)* |
| `#foo` ` ` | Blank lines or lines starting with # are ignored *(comments)* |
| `*.scss` | Ignores all files ending with `.scss` |
| `!main.scss` | Include `main.scss` even though it's ignored by the other rule |
| `*~` | Ignores all files whose name ends with `~` *(temporary files)* |
| `index.js` | Ignores `index.js` in the current directory and subdirectories |
| `/index.js` | Ignores `index.js` only in the current directory |
| `dist/` | Ignores `dist` directory with its all files and subdirectories |
| `dist/*.scss` | Ignores `dist/main.scss` but not `dist/scss/main.scss` |
| `dist/**/*.scss` | Ignores `dist/main.scss`, `dist/scss/main.scss`, `dist/styles/scss/foo.scss`, etc. |
| `[Bb]in/` | Ignores `Bin` or `bin` directory |
