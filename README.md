# bazel_soci

[Bazel](https://bazel.build) `BUILD` file for [SOCI](http://soci.sourceforge.net).

This does not handle building SOCI itself with Bazel, it only links to the local
SOCI installation on the system.

Everything below assumes the correct libraries and headers are present on the
system.

## Usage

An example can be found [here](https://github.com/nathanws/bazel-examples/tree/master/soci).

In the root Bazel `WORKSPACE` file, add the following:

```
git_repository (
  name = "github_nathanws_bazel_soci",
  commit = "aa0f4a7d1059d798b4c5407d94c4d1ac004f7d3e",
  remote = "https://github.com/nathanws/bazel_soci",
)
```

This will add the git repository to the project. To create individual targets
for use in the project, bind them as following:

```
bind (
  name = "soci-sqlite3",
  actual = "@github_nathanws_bazel_soci//:sqlite3",
)
```

Currently, only targets for `sqlite3`, `mysql`, and `postgresql` exist.

Add the target as a dependency in the necessary `BUILD` file:

```
cc_binary (
  ...
  deps = [
    "//external:soci-sqlite3",
  ],
)
```
