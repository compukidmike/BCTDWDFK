# BCTDWDFK

Happy Holidays!

MKFactor and Klipper are proud to announce the 2024 holiday badge! 

## Assembly Instructions:

Place the ESP32 module in the headers to keep them straight:
![IMG_0241](https://github.com/user-attachments/assets/18bfba40-6f04-400e-b17f-5bee3ec91e24)

Place the pins through the back of the house to the front:
![IMG_0242](https://github.com/user-attachments/assets/e62078e3-69a9-4b24-9cb8-2e4d4add541f)

Solder the pins on the front:
![IMG_0243](https://github.com/user-attachments/assets/a57d0da4-9ecc-4844-a9b7-5d7a2f4e1b1d)

Remove both screens from the packaging. You will use the straight pins (discard the 90 degree ones). The LONG side will be soldered on the BACK of the screens. The plastic part and shorter pins will be on the screen side:
![IMG_0248](https://github.com/user-attachments/assets/a8fc3962-aa74-4d42-80ce-34bc4bc17ae0)

Solder the long pins on the back of the screens. Setting them on a table can help:
![IMG_0249](https://github.com/user-attachments/assets/59ceb395-7a25-4c0f-9af2-317558efd333)

Peel off that sweet, sweet, screen protection film:
![IMG_0251](https://github.com/user-attachments/assets/f469f472-02f3-4547-b565-39494e0705d8)

Push the pins from the back to the front of the badge. They will be tight so it will require a bit of force. Make sure to apply force on the header pins and not the screens. Once it is pushed through, solder the pins on the front of the badge.
![IMG_0252](https://github.com/user-attachments/assets/9d1f532b-326c-4767-a508-7a960c77e7ad)

Remove the ESP32 module so you can access the pads to solder the button:
![IMG_0253](https://github.com/user-attachments/assets/7f568535-de28-4f7e-8104-f9816c3e2940)

Push the button where the doorknow goes, and the pins will push through to the back of the door:
![IMG_0254](https://github.com/user-attachments/assets/c6655dd2-2f82-4280-81c5-4f1aaf911eec)

Solder the 4 pins for the button on the back of the badge (no polarity):
![IMG_0256](https://github.com/user-attachments/assets/ac982329-19a4-4652-bcf8-bdafa630f582)

Place the minibadge headers on the front of the badge (the chimney)
![IMG_0258](https://github.com/user-attachments/assets/920eea55-3c13-42ce-9b1d-37bf21fc0fb2)

Putting a minibadge in the headers can help keep things straight. Flip the badge over and solder the pins:
![IMG_0259](https://github.com/user-attachments/assets/35809132-2e76-473e-815d-e04aa684be26)

That's all there is to it! At this point, the LEDs will not turn on and the left screen will be flashing. This is normal! The following steps will take you through the process of updating the firmware to get everything working!

## Firmware Update:

You'll need to download the firmware.bin and wled_presets.json files from this repository for the following steps.

Fire up the badge and look for the wled-ap access point and connect to it. The password is wled1234. It should present a captive portal that takes you to the configuration page. Once you are connected, go to the wifi settings and scan for your local wifi and join the badge to it. You can set a static IP if you'd like. If not, make note of the mDNS address or lookup the new IP lease in your dhcp server. 

Now browse to the IP or url of your badge. At the top of the web interface, click on "Config". Now click on "Security & Updates". Click the "Manual OTA Update" button. Click "Choose File" and select the firmware.bin file from this repository. Now click "Update". The badge will upload the new firmware and reboot. You may need to manually power cycle the badge after it finishes the firmware update. If at any point throughout this process you can't access the web interface or things seem to be acting weird, power cycling the badge usually fixes things.

With the new firmware, the right screen should show an image. However, there are still a couple other settings to change. Go back to the web interface and click on "Config". Now click on "Security & Updates". Scroll down to the "Backup & Restore" section and click "Choose File" under "Restore presets". Select the wled_presets.json file from this repository. Now click "Upload". Then click "Back" and click on "LED Preferences". Under "Hardware setup" change the Color Order to RGB, Length to 25, and GPIO to 17. It should look like this:
![LEDSettings](https://github.com/user-attachments/assets/991e8caf-8c3d-4237-a01b-50fe8f57ec6c) 

Then click "Save" at the top of the page. 

At this point at least one LED should be on and both screens should be on. The badge is programmed to automatically change the preset each day to light up another LED, all the way up to the 25th!

If you run into any issues or have questions, please let us know!

If you're interested in playing with the code and changing things, the source is available here: https://github.com/compukidmike/WLED-BCTDWDFK
