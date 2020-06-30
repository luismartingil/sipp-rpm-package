# Thanks to nacho.gs
# https://src.fedoraproject.org/rpms/sipp/tree/epel7
# https://build.opensuse.org/package/show/network:telephony/sipp

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
sudo yum install -y gsl-devel help2man autoconf-archive gmock-devel gtest-devel
spectool
rpmbuild --undefine=_disable_source_fetch --define "_rpmdir $(pwd)/rpms" -bb sipp.spec
```

# If centos8

```
# Enable PowerTools repo
sudo yum install -y gmock-devel gtest-devel libpcap-devel lksctp-tools-devel pkgconfig gsl-devel gsl
rpmbuild --undefine=_disable_source_fetch --define "_rpmdir $(pwd)/rpms" -bb sipp.spec
```
