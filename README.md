# Led Board and Application Set-Up

# add assembly images and 3d files link

### Disclaimer: SSH or remote access us utilized to edit and install files on the Raspberry Pi. It is up to the user to configure the security setting to meet their specific needs.

## Required Hardware Refrenced at the Bottom
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/8d0cddf8-83f3-448e-90b9-70a758afb57e" alt="IMG_0584" width="300" height="200">
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/bb6920f6-ff4d-49ce-815f-a3bd049cfb54" alt="IMG_0584" width="300" height="200">
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/1f8c8b90-3964-40ef-b4b5-e148caa803fe" alt="IMG_0584" width="300" height="200">
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/7fb41a0d-764e-4189-bd65-df001cf257da" alt="IMG_0584" width="300" height="200">
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/0bf04dc4-fd7b-4d76-9d15-3d24ce158498" alt="IMG_0584" width="300" height="200">
<img src="https://github.com/cashhollister2u/Led_App_Prod/assets/153677541/5357fde8-a1d5-40a6-84a5-42ef1514189a" alt="IMG_0584" width="300" height="200">

# 3D Printer Files
- It may be a good idea to initiate the print before completing the tutorials. Print time is roughly 6.5 hours (Bambu Labs P1S)
- Files:

# iOS App
- Currently in Beta ***
- Download TestFlight from the iOS store
- Email LED_APP_Controller@gmail.com with your icloud email and I can authorize the download.

# Hardware Set-Up
- Pre-Made Button for On/Off switch (optional)
  - [amazon](https://www.amazon.com/Twidec-Normal-Momentary-Pre-soldered-PBS-110-XR/dp/B07RV1D98T/ref=sr_1_2?dib=eyJ2IjoiMSJ9.cc92CYD6puREW-x_KclpTxxF9dJcV70bwpHP-jv-Wn2_PPcrELPjwRkWQH12hJr2dz5d-kDj8Gqh3-SzwORFMF7KfkKKUL8Gr94a0AC91_Qm8w9eVfvEArO9o3QgMDzNxYQhj0qf56dxpL16K72le_0ZEBwkry7Zh9IWC3ZaSD_FYDiE5sCKnJWk8Xk_RDVnh1xd3hJFhQKd1CObGwGfsE0Od-4hqoPX3EcL7heuV00.3lw6QoZoAzrgV8Qc4Dn2bHNZNRAPMQfgz7cn0diES90&dib_tag=se&keywords=Raspberry%2BPi%2BPower%2BButton&qid=1720996822&sr=8-2&th=1)
- If utilizing the button it must be soldered to the "SCL" and "GND" pins of the Matrix Bonnet. The orientation of the wires does not matter. (optional)
  - <img src="https://github.com/user-attachments/assets/fcf34ac5-c3ea-4da0-820d-abdcc2f5171a" alt="IMG_0584" width="300" height="200">
- For best quality solder pin 4 and pin 18 with a jumper wire. (Further details and pictures in the link below) (optional)
- It is reccomended to complete all soldering before connecting the Raspberry Pi to the Matrix Bonnet.
- It is reccomended to attach the pi to the 3D printed mounting platform before proceeding.
  - 4 M2 nuts are press fit into the mouniting platform
  - 4 M2 nuts are placed on top to act as a spacer between the Raspberry Pi and the mounting platform
  - The 4 corners of the Raspberry Pi each rest on top of 2 M2 nuts
  - A brass spacer is threaded through the board and the 2 M2 nuts securing the corner in place (REPEAT for the other 3 corners)
- This page provides detailed instructions on how to propperly connect the bonnet to either the Raspberry Pi 4 or the RaspBerry Pi Zero 2 as well as connecting the bonnet to the LED Matrix.
  - https://learn.adafruit.com/adafruit-rgb-matrix-bonnet-for-raspberry-pi/driving-matrices
- 



# Software Set-Up

## Sign-Up For Free API Services:
- All api services provided by the led application utilize the free trials of the following. 
### Twelve Market Data
- https://twelvedata.com/pricing
- API key required for led application 
### Open Weather Map
- https://openweathermap.org/price
- API key required for led application
### Spotify Developer Account
- https://developer.spotify.com/documentation/web-api/tutorials/getting-started
- IGNORE everything after "Create an App" the led applicaiton handles the rest
- Ensure "REDIRECT URI" is set to http://localhost:8080/
- CLIENT ID AND CLIENT SECRET are required for the led application
    - To Locate go to "DashBoard" select the app you created and click on "Settings" in the top right corner.

## Download Raspberry Pi Imager
- https://www.raspberrypi.com/software/

## RaspBerry Pi 4 Set-Up (Software)
### STEP 1:
- Insert Micro SD into computer
- Open Raspberry Pi imager

## STEP 2:
- Click on "Choose Device"
- Select Raspberry Pi Zero 2 
- Click on "Choose OS"
- Select Raspberry Pi OS (Other) 
- Select Raspberry Pi OS Lite (32-bit)
- Click on "Choose Storage"
- Select Micros SD
- Click "Next"
- Click "EDIT Settings"
- Select General
- Set Hostname: “LedApp”.local (IMPORTANT)
- Set username: “led_app” (IMPORTANT)
- Set password: Your Choice
- Configure wifi
- Select Services
- Enable SSH
- Enable Password or Public-Key Auth
- Click Save
- Click "YES" (use custom settings)
- Click "YES" (erase previous data)
- Wait for install to complete

## STEP 3:
- Unplug Micro sd and insert into Raspberry Pi  (Ensure Pi is off)
- Turn on Raspberry Pi
- To test if the Raspberry Pi is accepting a connection run the following in you computer's terminal/command prompt:
  - "ping LedApp.local" 
- Pi will cycle through a initial boot and reboot for the first boot cycle if it takes longer than 5 minutes to get a responce repeat steps 1 and 2 data may be corrupted
- Gain remote access to the Raspberry Pi:
  - “ssh led_app@LedApp.local”
- Run the following commands after gaining access and logging into the Raspberry Pi:
  - "sudo apt update" (update available software)
  - "sudo apt install git" (needed for the "git clone" command)
  - "git clone https://github.com/cashhollister2u/Led_App_Prod.git" (download this repository)
  - "sudo ./Led_App_Prod/Bash_Scripts/install.sh" (refer to "Bash_Scripts/install.sh")
- Follow the prompts that the terminal displays
- Have the api keys associated with the accounts you created. You will be prompted for them.
- When prompted to reboot select "y" or yes for changes to take effect.


## That completes the software set up for the Raspberry Pi 
- If the hardware is configured propperly you should see the LED Display propt you to connect the iOS app
- Download the app from TestFlight 
- Open the app
- Click "Settings"
- Click "Show" next to the Spotify Auth
- Click "Authenticate"
- Click "Home" on the app display and select one fo the four display options
  - If selecting "Spotify" ensure Spotify is currently playing. Otherwise the screen may display an error.

## Debugging Hardware / Software
- If the board displays lights but does not appear as expected or jumbled first follow the steps here:
  - https://learn.adafruit.com/adafruit-rgb-matrix-bonnet-for-raspberry-pi/help
- If chosen to take the soldering approach re-check solder connections between the pi zero 2 and the gpio pins.
  - 
 
## Basic Operation:
- Plug in the board to turn on or press the optional physical button
- To connect select one of the 4 displays in the iOS app when the screen prompts you to "connect to iOS"
- To turn off the board use the power button in the iOS app or optional physical button
  - To be safe look through the vent holes in the back for the green light to stop flashing on the Raspberry Pi
- WARNING: If the board is unpluged without using the iOS app it may corrupt the files.
- WARNING: Spotify Updates every 8 seconds (this is for program stability) / Song titles DO NOT scroll (this is for album cover image stability)
- NOTE: If anyone actually uses this I can post an update fixing the Warnings above. 

# Hardware List (Raspberry Pi 4)
- Raspbery Pi Zero 2
  - [https://www.adafruit.com/product/4296](https://www.adafruit.com/product/5291)
- GPIO header pins (solderless) (OPTION 1)
  - https://www.adafruit.com/product/3662?gad_source=1&gbraid=0AAAAADx9JvQF9r4jQa4XoDPi65FgIZNb-&gclid=EAIaIQobChMI4IuM2eWnhwMVJ25_AB0yUQ59EAQYASABEgJf4_D_BwE
- GPIO header pins (soldering req) (OPTION 2)
  - https://www.adafruit.com/product/2822
- 16 or 32 gb Micro SD Card for Raspberry Pi
  - [Amazon](https://www.amazon.com/SanDisk-Ultra-microSDXC-Memory-Adapter/dp/B073JWXGNT/ref=sr_1_8?crid=3BA0SAU4Z3BVC&dib=eyJ2IjoiMSJ9.gma2hVfUgy-OBJ-COHM6pbshqICnhWgymisufu6qkTikGx9DMDOT-3dc7naXHtt0GM5F7Dc-Kzp8nmsDFj5eZRuSTCXBZHiIuxiikhiAopv-ALnQMJtZZVEZLa4dxi8Tr1MkCnvShyoG4zFOWRbtyg1_XfMy-BaL2RcxbW6T4j0bIq9oyaprOGw9gEz1MJSrd4Xhy54847gErjsLfFbm8xlkS_w2olOighTBk9fXdI329hnd6R0Gkh-Ykuode-GpM0Fs1ZgVM-bJ4eExbhLlgDixoFgMeH63-s7JflFici0.Aj76Y7zJJKxqQMwN3vLCvcBD0_9C8W23b6iYM99UH6c&dib_tag=se&keywords=32+gb+micro+sd&qid=1720498866&s=electronics&sprefix=32+gb+micro+sd%2Celectronics%2C131&sr=1-8)
- gpio extention (optional)
  - https://www.adafruit.com/product/2223?gad_source=1&gbraid=0AAAAADx9JvRoR7oa6Xt2MOaaaoUYxxSop&gclid=CjwKCAjwnK60BhA9EiwAmpHZw2OqCtdnE_kqISjUMuYMXSpIDnCF-1EZaFNnZ6MPz9KHeC91vC1JABoCNKQQAvD_BwE
- Pre-Made Button for On/Off switch (optional)
  - [amazon](https://www.amazon.com/Twidec-Normal-Momentary-Pre-soldered-PBS-110-XR/dp/B07RV1D98T/ref=sr_1_2?dib=eyJ2IjoiMSJ9.cc92CYD6puREW-x_KclpTxxF9dJcV70bwpHP-jv-Wn2_PPcrELPjwRkWQH12hJr2dz5d-kDj8Gqh3-SzwORFMF7KfkKKUL8Gr94a0AC91_Qm8w9eVfvEArO9o3QgMDzNxYQhj0qf56dxpL16K72le_0ZEBwkry7Zh9IWC3ZaSD_FYDiE5sCKnJWk8Xk_RDVnh1xd3hJFhQKd1CObGwGfsE0Od-4hqoPX3EcL7heuV00.3lw6QoZoAzrgV8Qc4Dn2bHNZNRAPMQfgz7cn0diES90&dib_tag=se&keywords=Raspberry%2BPi%2BPower%2BButton&qid=1720996822&sr=8-2&th=1)
- IPhone (used for LED Board controller)
- Adafruit Matrix Bonnet
  - https://www.adafruit.com/product/3211
- 32 X 64 3mm pitch LED Matrix (Ive found that 3mm is best for Desktop Visibility) (3D files built to support 3mm pitch)
  - [Amazon](https://www.amazon.com/Waveshare-Full-Color-Individual-Adjustable-Brightness/dp/B0B5N5HPKX/ref=sr_1_2?crid=3EE2RLGAFVNC0&dib=eyJ2IjoiMSJ9.6oWrmhaCysWQ6qbBZtvRPtuQFAcbo_KZfVjT3w0WNRURf4c_8LdoDPCJzGhy9tWullLorzWBjrTn1PlSDj-DX7ZxVfj83l0zLvIAVLbHu0bE95X980lZwgOa7jkOEbl_Enki0Q3Jo-yasOGaD7XEsSKcH8O2vhA2hQwktcXNVlq-TFHk7Sfo1ZQ-2zCC3MNrgMAuG0W_xDqNSZJfmaBb1N-TG0UULugbZZ1GlVODYvs.AxmNy8pyNuM09ZaFkDXfzJ-czBjdJapyLn1JC3J6bL0&dib_tag=se&keywords=32+X+64+3mm+pitch+LED+Matrix&qid=1720499174&sprefix=32+x+64+3mm+pitch+led+matrix%2Caps%2C214&sr=8-2)
- 5V 10 Amp charger with Barrel Connector Male (Power both the LED board and Raspberry Pi)
  - [Amazon](https://www.amazon.com/10A-Power-Supply-Adapter-Switching/dp/B07H9XRZBP/ref=sr_1_2?crid=31A60WJNMKB4L&dib=eyJ2IjoiMSJ9.je877a0xnR4pfYxTF_0U6VDr9ZWNS3ATxNAOGSqhnWM__La7IzTYY-_Mg6yM072tnJQ8MZD80hURwLODE9jFtcwCrMps8yq-YBtffrXRhZI8poQBa3unZHCNaHB_90uOPAmM2O-sTZ-_fa6W8CyureTFLDfdoQTdiTz8Bvg_fhH1QWd44OH97XIj0_Qqs0qsn-s-NyyGDLf-SiQkKKxLwJ04E0gCHSD87Zubs4jyWnQ.B6CIy5o4OmhKjVlphmawFai7AqbyU_APljyTN0I94Vw&dib_tag=se&keywords=5V+10+Amp+charger+cool&qid=1720499223&sprefix=5v+10+amp+charger+cool%2Caps%2C99&sr=8-2)
- RaspBerry Pi Brass Spacer Kit with M2 Nuts and Screws
  - [Amazon](https://www.amazon.com/Geekworm-Raspberry-Installation-Standoff-Accessories/dp/B0756CW6Y2/ref=sr_1_6?crid=1WIJ52THVGKAP&dib=eyJ2IjoiMSJ9.4vBz5jbdFFOUtiz9dlUIeNocA1PZrMFELvxfpBsJEauqSijKi8LOeXqvuXxtIXUkgwOsq_9PlPbgfsAGFdJaNxzQZgTj-yARI76t3xqQWNyB9At3IsBCIWPSF6dq5QvkSnASFhCdwWz463ftttUuG7MaqhrD9E-eNHP1ojmMRMxDNMBSbyNPwyLDj4hL06kszQLs6uqNLImpSXhbkOveOf-zzTU06B8clHoEHzymkRY.cGx_1wekEp3kUjAIoMOEXhOosZFJUN_5ML_G8om5nY0&dib_tag=se&keywords=RaspBerry+Pi+Brass+Spacer+Kit&qid=1720499301&sprefix=raspberry+pi+brass+spacer+kit%2Caps%2C102&sr=8-6)
- Solder Iron / Jumper Wire (This can be skipped but reduces quality) (Would also have to reinstall the bonnet library refer to above instructions)
- Access to 3D Printer (for housing)
- Small Skrew Driver
