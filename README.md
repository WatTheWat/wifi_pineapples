# Wi-Fi Pineapple 
This is a replacement for the in-person tech talk. The aim of this is to emulate the information that I presented during the talk. The slides / speaker notes for the slides accompany this document.

## Preface
This talk was made using a *headless* Raspberry 3 Pi. The term headless means that there were no supporting peripherals connected to the Pi. There was no monitor, keyboard, mouse, etc. The only added connection was a wireless adapter that allowed the *monitor* mode functionality over Wi-Fi. 

In order to access this headless Pi, we used an [ssh connection](https://forums.raspberrypi.com/viewtopic.php?t=341473). 

## The Tools
There are three main programs funcitoning on this Pi to make the Evil Twin attack possible. 

The first is hostapd. Hostapd creates our wireless network - allowing us to turn our device into a hotspot. Once configured, our network will be visible to any searching devices. It will appear like any other network would. 

The second is uphcpd. uphcpd allows our device to automatically assign ip addresses to devices connecting to our network made with hostapd. This means that the Pi is now working as a network bridge - using dhcp to keep victim's wifi connection uninterrupted. A victim now connecting to the Pi would be able to access any website without knowing we were acting as a router in between. The victim's credentials and internet traffic can already be captured at this step. If the victim is connecting to a non-HTTPS website we can view their field inputs (usernames, passwords, banking information, etc.)

The third tool is DNSchef. DNSchef completes the DNS spoofing attack - allowing our Pi to redirect traffic to any domain that we wish. 

## An Example

Does this situation seem relatable to you? You're sitting at a coffee shop and decide to do some homework. After all, the ambiance of this cute little joint is perfect to finish up my homework. Why wouldn't you? They even offer free Wi-Fi! You connect to their Wi-Fi and get redirected to a login page. All it's asking for is your email and password for the coffee shop. Just a little information and you're seconds away from free Wi-Fi!

What our victim isn't aware of is a "funcitonality" of most Wi-Fi capable devices. If two networks share the same network id the device will automatically connect to the one that offers a stronger connection. This is useful for interacting with large meshes - such as UTD's CometNet. The functionality can also be exploited allowing for our Man-in-the-middle attack. The Raspberry Pi's antenna would likely give a stronger connection than the router placed futher in the room - or even multiple rooms away. 

An attacker using DNSchef would be able to hijack the user's internet traffic, redirecting them to a fake login page. While the page may seem real, the information entered would be given to the attacker. 

## The Counter
The safest and simplest solution is to not connect to public networks, "Free" Wi-Fi may not be as free as it seems. Another solution is to use a good, quality VPN. Once again, the "free" alternative to VPNs rarely work in adequately securing your data. Using an international VPN is also recommended, as your traffic is much harder to acquire by local governments, but that is outisde the scope of Evil Twin attacks.
