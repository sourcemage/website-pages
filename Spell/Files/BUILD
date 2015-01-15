= BUILD =

This file controls the actual build process. If the BUILD file is not present in the [[Spell|spell]], [[Sorcery/Commands/Cast|cast]] uses {{{default_build}}}.

**Note:** {{{default_build}}} is not the same in [[Grimoire/API|build API]] 1 as in the new build API 2!
----

== Build API 2 ==

{{{default_build}}} for build API 2:

{{{
OPTS="$OPTS --build=${BUILD}"

[[ $CROSS_INSTALL == on ]] && OPTS="$OPTS --host=${HOST}"

./configure --prefix=${INSTALL_ROOT}/usr  \
        --sysconfdir=${INSTALL_ROOT}/etc  \
     --localstatedir=${INSTALL_ROOT}/var  \
            --mandir=${INSTALL_ROOT}/usr/share/man   \
           --infodir=${INSTALL_ROOT}/usr/share/info  \
                     $OPTS                 &&

make
}}}

To add an option to {{{./configure}}}, use this instead of copying the above and then adding the options:

{{{
OPTS="--option-1 --option-2 ${OPTS}" &&

default_build
}}}

or if the values are in a variable:

{{{
OPTS="${MY_CUSTOM_OPTS} ${OPTS}" &&

default_build
}}}

**Warning:** **do not under any circumstances use {{{OPTS}}} in conjunction with the** {{{config_query}}} API or as a persistent variable. {{{OPTS}}} is an internal [[Sorcery]] variable which is auto-generated from dependency information, using it as a persistent variable is a direct contradiction with the intended purpose of persistent variables and **will not work correctly**.

If you need to have a custom value for {{{OPTS}}} //(beyond the auto-filled values from dependencies)// use another persistent variable list {{{<SPELL>_OPTS}}}.
----

== Build API 1 (obsolete) ==

{{{default_build}}} for build API 1:

{{{
(

[[ $CROSS_INSTALL == on ]] && OPTS="$OPTS --host=${HOST} --build=${BUILD}"

./configure --prefix=${INSTALL_ROOT}/usr  \
        --sysconfdir=${INSTALL_ROOT}/etc  \
     --localstatedir=${INSTALL_ROOT}/var  \
            --mandir=${INSTALL_ROOT}/usr/share/man   \
           --infodir=${INSTALL_ROOT}/usr/share/info     \
                     $OPTS                &&

make                                     &&
prepare_install                    &&
make    install

) > $C_FIFO 2>&1
}}}

**Note:** it is here solely as a reference since build API 1 spells still exist. Do not write new spells in build API 1, use build API 2 instead!