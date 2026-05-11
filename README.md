## export friendly dir
### yêu cầu
 - cho output câu lệnh ls -l /etc
 - yêu cầu hãy tạo ra một report gồm column:

```
type	name
 - adduser.conf
 - at.deny
 - bash.bashrc
 - bash_completion
 - d	acpi
d	alternatives
d	apm
d	apparmor
d	apparmor.d
d	apport
d	apt
d	bash_completion.d
...
```

## solution
### cách 1 ( sơ khai, chạy lệnh ls 2 lần)
```
paste \
	<(ls -l /etc | tail -n +2 | cut -c 1) \
	<(ls -l /etc | tail -n +2 | tr -s ' ' | cut -d ' ' -f 9) \
	| sort -t $'\t' -k 1,1 \
	> output.csv
```
