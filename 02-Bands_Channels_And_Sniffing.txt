-Wireless sniffing-
	-Modes
		-Monitor (wireless): accepts all paquets regardless of the network and receiver
		-Promiscious (wired & wireless): sniffing only in the network
	
	# airmon-ng start wlan0
		-to create a monitor mode interface on top of wlan0 (mon0)

	-use wireshark to capture everything on the mon which is the monitor interface to sniff
	-WLAN frequencies:
		-2.4GHz (bgn)
		-3.6Ghz (y)
		-4.9/5.0GHZ (ahjn)
	-channel are specific frequences
		-ex: bgn channel 2 is 2417 mhz
		 and bgn channel 3 is 2422 mhz
	-difference between Wired and Wireless
		-concept of channel and band
	-to set the channel
		-# iwconfig wlan0 channel 1
	-to make the card cycle (over multiple channel), airodump
			-by default, 2.4GHz
			-# airodump-ng --band bg mon0
