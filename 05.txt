---Dissecting WLAN Headers---

-Terminology
	-STA: Station (wireless client)
	-BSS: Basic Service Set (set of nodes communicating to each other)
		-Infrastructure BSS (AP and clients)
		-Independent BSS (Ad-Hoc clients)
	-ESS: Extended Service Set (set of connected BSS)
	-BSSID: Basic Service Set Identifier
		-Infrastructure BSS: mac adr of AP
		-Independent BSS: randomly chocen mac adr
	-DS: Distribution System
		-System between BSS

-WLAN packet header
	-Field mandatory for a header: Frame Control, Duration/ID, Address 1 and FCS
	-"Frame control"
		-Protocol, Type (Mgt, Ctrl, Data), ToDS/FromDS (BSS type), Order, etc.
	-"Duration/ID"
		-Set the Network Allocation Vector (NAV)
	-"Address $num"
		-More than 2 adr (src and dst), but usually BSSID also.
		-Depends on types/subtypes
	-"Sequence Control"
		-Sequence number and fragment number
	-"QoS Control"
	-"FCS"
		-CRC over MAC header and frame body
		
