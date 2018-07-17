# Simple script for checking is a sub path have changes in a travis PR build

## Usage

```
git travis-change andoird ./script/test-android.sh
```

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
