`#!/bin/bash

[[ ${EUID} -ne 0 ]] && {
printf "Must be run as root. Try 'sudo $0'\n"
exit 1
}

usage() { echo "Usage: $0 -u FIRST-UID username1 [username2 ... ] " 1>&2; exit 1; }

while getopts ":u:" o; do
case "${o}" in
u)
u=${OPTARG}
;;
*)
usage
;;
esac
done
shift $((OPTIND-1))

if [ -z "${u}" ] ; then
usage
fi

NEWUID=${u}; NEWGID=${NEWUID}

for Uname in "${@}"
do

grep -q :${NEWGID}: /etc/group && {
printf "GID ${NEWGID} already exist\n"
exit 1
}
grep -q ^${Uname}: /etc/group && {
printf "groupname ${Uname} already exist\n"
exit 1
}

grep -q :${NEWUID}: /etc/passwd && {
printf "UID ${NEWUID} already exist\n"
exit 1
}
grep -q ^${Uname}: /etc/passwd && {
printf "username ${Uname} already exist\n"
exit 1
}

addgroup -gid ${NEWGID} "${Uname}" && \
adduser --gecos '' --home /home/${Uname} --shell /bin/bash -UID ${NEWGID} -GID ${NEWGID} --disabled-login ${Uname}

((NEWUID++))
((NEWGID++))

done`
