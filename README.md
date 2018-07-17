# Simple script for checking is a sub path have changes in a travis PR build

## Usage

```
source <(curl https://raw.githubusercontent.com/oursky/git-travis-change/master/install)
git travis-change andoird ./script/test-android.sh
```

## Example travis.yml

```
before_install:
  - curl https://raw.githubusercontent.com/oursky/git-travis-change/master/install | bash
script:
  - git travis-change backend script/build-backend.sh
```

Note: in Travis-CI osx image, source will fails. So it assume all script are
run at default path, that why git will find git-travis-change

# Objective of the script

When we have multiple project in same repo and use travis matrix to build for
testing, travis will build all matrix regardless there is any change in the
folder.

For example, we have following folder:

```
ios/
web/
skygear/
```

Changes are often only happen in one sub-folder. i.e. PR changing ios code
will not likely to change the web code.

Although running all test against any line of change does not hurt, but in
reality the resource is limited and we want to make good use of them.

This script is intended to make the checking easy while the making the build
script is still local runnable.
