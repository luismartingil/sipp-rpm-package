# https://github.com/SIPp/sipp/releases/tag/v3.6.0
# https://build.opensuse.org/package/show/network:telephony/sipp

# Install build deps
sudo yum install -y gsl-devel help2man

# If centos6
spectool -g -R sipp.spec
rpmbuild --define='ext_man .gz' -bb sipp.spec

# If centos7
rpmbuild --undefine=_disable_source_fetch --define='ext_man .gz' -bb sipp.spec
