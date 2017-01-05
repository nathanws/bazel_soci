cc_library (
  name = "core",
  # specifying rpath since soci is installed in /usr/local/lib64
  # (instead of /usr/local/lib), bazel does not look in lib64 by default
  linkopts = ["-Wl,-rpath,/usr/local/lib64", "-lsoci_core"],
  visibility = ["//visibility:private"],
)

# soci must be built with -DWITH_MYSQL=ON for this to work
cc_library (
  name = "mysql",
  deps = [":core"],
  linkopts = ["-lsoci_mysql"],
  visibility = ["//visibility:public"],
)

# soci must be built with -DWITH_POSTGRESQL=ON for this to work
cc_library (
  name = "postgresql",
  deps = [":core"],
  linkopts = ["-lsoci_postgresql"],
  visibility = ["//visibility:public"],
)

# soci must be built with -DWITH_SQLITE3=ON for this to work
cc_library (
  name = "sqlite3",
  deps = [":core"],
  linkopts = ["-lsoci_sqlite3"],
  visibility = ["//visibility:public"],
)
