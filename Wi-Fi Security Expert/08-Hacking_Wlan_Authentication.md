Part 8: Hacking WLAN Authentication
=================

-'Open authentication' type
	-Simple 2 packet exchanged between Client and AP
	-Fail when 'Mac Filering is enable'

-'Shared authentication' type
	-WEP
		-Needed two parameters
			-3 bytes IV
			-WEP key
		-RC4 algorithm using the two parameters to create a key string
		-The plaintext is XORed with the key string
	-Scenario between Wireless station and AP
		- ->
			- Authentication request
		- <-
			- Response with a challenge which is a 128 bytes plaintext (randomly created)
		- ->
			- Send the Response the plaintext ciphered with the text
		- <- 
			- Send a sucess/failure depending of the decryption of the response with the plaintext

	-'airodump' only catch the Auth type ("Open" VS "Shared (SKA)") a client connect since it catches the challenge-response exchange.
	-Practical
		- From client to AP
			- "Authentication SEQ: 0x0001"
		- From AP to client
			- "Challenge text" with the random plaintext  
		- From client to AP
			- "WEP parameters" containing the "Initialization vector"
			- "Data" with the encrypted text sent
		- From AP to Client
			- Status code: Succesful (or not)

	-Basic cracking:
		-Intercept a plaintext and a corresponding ciphertext to get the key stream with those.
		-With the 'airodump' 'write' flag, the key stream (and the IV) for a WEP handshake is given (.xor file)
		-Workflow
			# airodump-ng mon0 --bssid $BSSID --write $FILENAME
			# aireplay-ng --fakeauth 10 mon0 -e $SSID -y $XOR_FILE_FROM_BEFORE
			-Authentication and Association succesful
		

