# Fluxion is the future of MITM WPA attacks
Fluxion is a remake of linset by vk496 with (hopefully) less bugs and more functionality. It's compatible with the latest release of Kali (rolling). The attack is mostly manual, but experimental versions will automatically handle most functionality from the stable releases.

## :trident: FAQ

#### "Clients are not automatically connected to the fake access point"
This is a social engineering attack and it's pointless to drag clients in automatically. The script relies on the fact that a user should be present in order to enter the wireless credentials.

#### "There's no Internet connectivity in the fake access point"
There shouldn't be one. All of the traffic is being sinkholed to the built in captive portal via a fake DNS responder in order to capture the credentials.

#### "Fake sites don't work"
There might be a problem with lighttpd. The experimental version is tested on lighttpd 1.439-1, anything neweer may break functionality. If you have problems, please use the stable version.

#### "Experimental menu is not responsive"
In the experimental version it will automatically check the handshake. I will fix the menu shortly. If you need a GUI, use the stable version (which doesn't automatically control handshakes).

#### "I need to sign in (on Android)"
This is how the script works. The fake captive portal is set up by the script itself to collect the credentials. Don't freak, it's al okay.

#### "The MAC address of the fake access point differs from the original"
The MAC address of the fake access point differs by one octet from the original in order to prevent fluxion deauthenticating clients from itself during the session. 

## Installation
``` git clone https://github.com/Eduardo084/fluxionOLD/ && cd fluxionOLD/ ```, run ./fluxion and install all dependencies 

## :book: How it works
* Scan the networks.
* Capture a handshake (can't be used without a valid handshake, it's necessary to verify the password)
* Use WEB Interface *
* Launch a FakeAP instance to imitate the original access point
* Spawns a MDK3 process, which deauthenticates all users connected to the target network, so they can be lured to connect to the FakeAP and enter the WPA password.
* A fake DNS server is launched in order to capture all DNS requests and redirect them to the host running the script
* A captive portal is launched in order to serve a page, which prompts the user to enter their WPA password
* Each submitted password is verified by the handshake captured earlier
* The attack will automatically terminate, as soon as a correct password is submitted

## :heavy_exclamation_mark: Requirements

A Linux-based operating system. We recommend Kali Linux 2 or Kali 2016.1 rolling. Kali 2 & 2016 support the latest aircrack-ng versions. An external wifi card is recommended.


## Disclaimer

***Fluxion is intended to be used for legal security purposes only, and you should only use it to protect networks/hosts you own or have permission to test. Any other use is not the responsibility of the developer(s).  Be sure that you understand and are complying with the Fluxion licenses and laws in your area.  In other words, don't be stupid, don't be an asshole, and use this tool responsibly and legally.***
