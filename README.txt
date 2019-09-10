# Thanks to nacho.gs
# https://src.fedoraproject.org/rpms/sipp/tree/epel7
# https://build.opensuse.org/package/show/network:telephony/sipp

# Install build deps
sudo yum install -y gsl-devel help2man autoconf-archive gmock-devel gtest-devel

# If centos6 - NOT supported
# Error when compiling
# src/call.cpp:3267: error: ‘nullptr’ was not declared in this scope
# -std=gnu++0x does not seem to fix it

```
spectool -g -R sipp.spec
rpmbuild --define "_rpmdir $(pwd)/rpms" -bb sipp.spec
```

# If centos7

```
rpmbuild --undefine=_disable_source_fetch --define "_rpmdir $(pwd)/rpms" -bb sipp.spec
```
