#!/bin/bash

INTERFACE=$1
IS_MANAGED=`iwconfig | grep Managed`

if [ "$EUID" -ne 0 ]; then
	echo "Please run the script as root!"
  	exit
else
	if [ -z "${INTERFACE}" ]; then
		echo "Choose an interface you want to switch!"
	else
		if [[ "$IS_MANAGED" == *"Managed"* ]]; then
                	ifconfig "${INTERFACE}" down
                	iwconfig "${INTERFACE}" mode monitor
                	ifconfig "${INTERFACE}" up

                	echo "Interface ${INTERFACE} switched to Monitor mode"
        	else
                	ifconfig "${INTERFACE}" down
                	iwconfig "${INTERFACE}" mode managed
                	ifconfig "${INTERFACE}" up

                	echo "Interface ${INTERFACE} switched to Managed mode"
		fi

	fi

fi


