sudo yum install -y gsl-devel help2man
rpmbuild --undefine=_disable_source_fetch --define='ext_man .gz' -bb sipp.spec
