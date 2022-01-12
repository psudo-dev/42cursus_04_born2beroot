## monitoring.sh

This is the layout of my monitoring script, I changed it because the one used in the example had some typos and errors but also because I think that this way is nicer.

I put some extra things including the time and date that the script runs because it facilitates for the evaluator to know if it's running in the intervals that it should.

```bash
#SYSTEM:
	#Architecture:
			${ARCHITECTURE}

	#LVM: ${LVM}
	#User Log: ${USER_LOG}
	#Sudo: ${SUDO} Commands
	#Last Boot: ${LAST_BOOT}

#HARDWARE:
	#CPU: ${PHYSICAL_CPU} / vCPU: ${VIRTUAL_CPU}
	#CPU Load:
		${CPU_USAGE}%
	#Memory Usage:
		${USED_RAM}/${TOTAL_RAM}MB (${MEM_USAGE}%)
	#Disk Usage:
		${USED_DISK}/${TOTAL_DISK}MB (${DISK_USAGE}%)

#CONNECTIONS:
	#Active:
		TCP: ${TCP} / STATUS: ${ACTIVE_TCP}
		SSH: ${SSH} / STATUS: ${ACTIVE_SSH}
	#Network:
		Hostname: ${HOSTNAME}
		Public IP: ${PUBLIC_IP}
		Private IP: ${PRIVATE_IP}

#Date:	${WEEK}, ${DAY} ${MONTH} ${YEAR}
#Time:	${TIME} (Time Zone ${TZ_NUM})
```
