# /bin/bash
trap '' SIGINT
terminal=/dev/rfcomm0
#$(ls /dev/ttyACM* 2>/dev/null)
xset r rate 30 30
counter=0

echo "Connected at $terminal"
echo -n "Checking Permissions"
echo "Ready"
while [[ ! "$done" == "0" ]]
do
read -sn1 var
if [[ "$var" == '' ]]
then
	read -sn2 temp
	var="$var$temp"
	case "$var" in
	'[A')
		 echo 'up'
		 echo -n "AAAA" >"$terminal"
	;;
	'[B')
                 echo 'down'
		echo -n "AAAAA" >"$terminal"
        ;;
	'[C')
                 echo 'right'
		echo -n "AAA" >"$terminal"
        ;;
	'[D')
                 echo 'left'
		echo -n "x" >"$terminal"
        ;;


	*)
		echo "unknown"
	;;
	esac
else
	case "$var" in
        'x')
                 echo 'exiting'
		echo -n "aaaaaa" >"$terminal"
		xset r rate 200 20

		done=0
        ;;
	'a')
                 echo 'increasing speed'
		echo -n '@@#3##' >"$terminal"
		
        ;;
	's')
                 echo 'decreasing speed'
		echo -n '@@#3#???' >"$terminal"
		
        ;;
	 *)
		echo "not spcial char"
        ;;

	esac
fi
done
