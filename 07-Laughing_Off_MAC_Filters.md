Part 7: Laughing off MAC filters
============

-Idea was to whitelist based on MAC address. But, MAC addr can be easily spoof.
-Mac addr is part of the WLAN header which is in plaintext 

# aireplay-ng --fakeauth 10 (delay [seconds]) -e SecurityTube mon0
	-connect to the AP with a fake auth and fake association
-if you enable Mac Filtering, the fakeauth won't work since the mac addr is being blacklist.

-wait for the client to connect, get his mac addr and connect spoofing yours with it or , deauth the client and get the mac addr
	-get mac addr with 'airodump' with the second table which presents the client (STATION) connected to the AP (BSSID)
	# aireplay-ng --fakeauth 10 -e $SSID -h $MAC_ADDR_SNIFFED mon0

Captive portal
	-Use Mac filters that only the authenticated client are able to connect
		-vulnerable


