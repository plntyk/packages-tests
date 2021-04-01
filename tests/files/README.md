
cpp_intl.cpp
via: https://stackoverflow.com/questions/1003360/complete-c-i18n-gettext-hello-world-example

g++ -ohellogt hellogt.cxx
xgettext -d hellogt -o hellogt.pot hellogt.cxx
msginit --no-translator -l es_MX -o hellogt_spanish.po -i hellogt.pot
sed --in-place hellogt_spanish.po --expression='/#: /,$ s/""/"hola mundo"/'
sed --in-place hellogt_spanish.po --expression='s/PACKAGE VERSION/hellogt 1.0/'
mkdir -p ./es_MX/LC_MESSAGES
msgfmt -c -v -o ./es_MX/LC_MESSAGES/hellogt.mo hellogt_spanish.po
export LANG=es_MX
ls -l $PWD/es_MX/LC_MESSAGES/hellogt.mo
./hellogt
strace -e trace=open ./hellogt
