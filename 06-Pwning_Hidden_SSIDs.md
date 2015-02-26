=== 6 - Pwning Hidden SSIDs ===

-SSID
	-identify network
	-advertise with beacon frame
-Hidden SSID
	-turn off broadcasting in beacon frames
		-by monitoring, an attacker won't see the SSID
	-"Security through Obscurity" -> doesn't improve security
	-airodump doesn't list hidden SSIDs by default
		-header paramter "SSID=Broadcast" (truly setted to Null)
	
-Techniques
	-Theory
		-The SSID name is not present in broadcast (beacon frame) but is it in Probe request
	-Passive solution
		-Listen for a new client connection to get the Probe request/response and the SSID associated
		# airodump-ng mon0 --bssid $bssidPoc
			-start that command and wait for a connection to happen, and the table will fill itself

		-Probe and Association contains SSID but not Authentication
	-Active solution
		-Break connections between hidden AP and client connected. Then, the clients will reconnect and we will see the values
		-Send a deauthentication notification to the client
			-Deauthentication packet is a subtype of management packet and cause the packet to break his connection.
			-break one connection (basic deauth packet) or all connections (broadcast deauth)
			# aireplay-ng --deauth 0 -a $BSSID mon0 
				- (0 for 'broadcast deauth')

