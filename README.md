#### _Running:_

```sh
$ docker run --rm getshipup/commitlint:<version>
```

You'll get a `/app` work directory, so all you need to do is mount your `git`-based project in the that directory with the `-v, --volume` docker parameter:

```sh
--volume $(pwd):/app
```

If you prefer, you can mount only your `.git` directory and your [configuration](https://github.com/marionebl/commitlint#config) file, like so:

```sh
--volume $(pwd)/.git:/app/.git \
--volume $(pwd)/.commitlintrc:/app/.commitlintrc
```

Or, if, for whatever reason, you need a different work directory, you can simply set it with `-w, --workdir`:

```sh
--workdir /my-app \
--volume $(pwd):/my-app
```

**Note 1**: If you want `commitlint` to read from `STDIN`, don't forget to set the `-i, --interactive` flag to keep `STDIN` open.

**Note 2**: This image ships with the following `commitlint`'s configuration preset packages (so you can extend them in your [configuration](https://github.com/marionebl/commitlint#config) file):

* [`@commitlint/config-angular`](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-angular)
* [`@commitlint/config-angular-type-enum`](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-angular-type-enum)
* [`@commitlint/config-conventional`](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-conventional)
* [`@commitlint/config-lerna-scopes`](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-lerna-scopes)
* [`@commitlint/config-patternplate`](https://github.com/marionebl/commitlint/tree/master/%40commitlint/config-patternplate)

---

#### _Developing:_

```sh
$ make build    # Builds a new image
$ make test     # Runs/tests the image
$ make push     # Pushes the image up
$ make clean    # Removes any generated artifacts
$ make clobber  # Removes artifacts and generated images
```

