# Tutorial
## Intro
Driving in Cyberpunk 2077 isn't as fun as it should be.
But you know what's fun? Need for Speed Nitro on Wii.
So let's get NFS Nitro controls in Cyberpunk!

## Warning
Well, not so fast. Some tinkering will be required, so please read this tutorial
carefully: I will strive to make it detailed and accessible, but you have to
understand what is going on to be able to actually use this setup.
TL;DR: Don't skim through!

## Technical issues
The Wiimote is a bluetooth controller, which means we could try connecting it
as a bluetooth device using the Windows 10 Settings app.
In reality, this doesn't work because the Wiimote requires a special PIN code
we can't input properly using Microsoft's latest tool.
Using the old "Printers and Devices" menu which can still be found under the
traditional "Control Panel" also does not work.
This means we will have to connect our Wiimote using third-party tools.

Those of you who already tinkered with Wiimotes in the past know they are not
properly supported by Windows out-of-the-box, so we will need a way to make
Microsoft's OS detect it as a gamepad. In other words, a driver!

Another more obvious issue is that Cyberpunk does not support the average
random controller. In fact, it only really supports the Xbox controller,
so we also need third-party software to emulate Microsoft's gamepad.

## Third-party fixes
To be able to connect your Wiimote to the computer, we will use
[WiiPair](https://github.com/jmandawg/wiipair/releases),
an
[open-source](https://github.com/jmandawg/wiipair)
stand-alone tool which can pair Wiimotes easily.

To register the Wiimote as a regular gamepad, we will need
[HID-Wiimote](https://www.julianloehr.de/educational-work/hid-wiimote/#download),
an
[open-source](https://github.com/jloehr/HID-Wiimote)
driver for the Wiimote which will expose it to Windows as a standard Human Input
Device (HID). It also requires `Microsoft Visual C++ Redistributable 2017`.

To be able to use any weird HID with Cyberpunk, we will use
[VirtualController](https://sourceforge.net/projects/vjoy-controller/),
which is based on the
[open-source](https://github.com/shauleiz/vJoy)
vJoy project.

## Step-by-step instructions
### 0.
First, we are going to install the HID-Wiimote driver.

Unfortunately, this open-source project will probably never be approved by
Microsoft as trusted software, so we need to disable a few security
measures beforehand.

The first barrier to take down is secure boot. This is usually disabled
by computer enthusiasts to regain control over their hardware so there are
serveral guides available online to help you do that if you need the details.

The exact steps will depend on your specific motherboard and BIOS version,
but in general it boils down to entering your motherboard's setup tool at boot
by pressing a certain key repeatedly and navigate the menus using your keyboard.

### 1.
The second security "fix" we must perform is enabling the Windows Test Mode.
Fortunately, the HID-Wiimote Control Center can turn it on permanently.
Simply run the program and click the corresponding button:

![screenshot 1](/img_main/1.png)

### 2.
The HID-Wiimote Control Center will now look like this.
Reboot your computer to apply the changes.

![screenshot 2](/img_main/2.png)

### 3.
After logging in, you will be greeted by this atrocious message in the bottom-right
corner of the screen. This is Microsoft's way of telling you their security is off:

![screenshot 3](/img_main/3.png)

### 4.
Launch the HID-Wiimote Control Center again and start installing the driver:

![screenshot 4](/img_main/4.png)

### 5.
The driver's installer should pop up. Click Next.

![screenshot 5](/img_main/5.png)

### 6.
Accept the license agreement.
If you disabled Microsoft's security correctly, a warning will appear.

![screenshot 6](/img_main/6.png)

### 7.
Click "Install this driver software anyway".

![screenshot 7](/img_main/7.png)

### 8.
And it should work!

![screenshot 8](/img_main/8.png)

### 9.
The control center should also detect the driver's intallation.
More on this later.

![screenshot 9](/img_main/9.png)

### 10.
Now it's time to connect the Wiimote. Run WiiPair. A console window will appear.

![screenshot 10](/img_main/10.png)

### 11.
Type `1` and press `Enter`

![screenshot 11](/img_main/11.png)

### 12.
You are now asked wether to remove already-paired Wiimotes.
Sometimes disconnected wiimotes still appear in the device manager.
This can help you remove them, and doesn't hurt anyway so you can safely
type `y` and press `Enter` here.

![screenshot 12](/img_main/12.png)

### 13.
You will be asked for confirmation here but there isn't any risk. Press enter.

![screenshot 13](/img_main/13.png)

### 14.
Once all the ghost Wiimotes are removed from the device manager,
open your Wiimote's battery cover and press the red button.
Then, immediately press `Enter`.

![screenshot 14](/img_main/14.png)

### 15.
Your Wiimote should be detected and paired. Press `Enter`.

![screenshot 15](/img_main/15.png)

### 16.
If the Wiimote's leds keep blinking, it means the HID-Wiimote driver isn't used.
We can fix this in the device manager: press `Win`+`R` and run `devmgmt.msc`.

![screenshot 16](/img_main/16.png)

### 17.
Open the "Human Interface Devices" section:

![screenshot 17](/img_main/17.png)

### 18.
Right-click the "Bluetooth HID Device" (this is your Wiimote)
and click "Update driver":

![screenshot 18](/img_main/18.png)

### 19.
A new window appears. Instead of going the regular way,
select "Browse my computer for drivers":

![screenshot 19](/img_main/19.png)

### 20.
We already installed the driver so you can click on
"Let me pick from a list of available drivers on my computer":

![screenshot 20](/img_main/20.png)

### 21.
Select "Wiimote Device" and click on "Next":

![screenshot 21](/img_main/21.png)

### 22.
Windows should switch drivers and the leds should stop blinking!
If it fails, reboot and start over from step 10.

![screenshot 22](/img_main/22.png)

### 23.
The device manager should list the Wiimote as such:

![screenshot 23](/img_main/23.png)

### 24.
Remember the HID-Wiimote Control Center?
If you open it now you can see it allows you to customize the behaviour of the
driver a little bit. This is useful for apps which support generic HID devices,
but we need something much, much more powerful to be able to control Cyberpunk.

![screenshot 24](/img_main/24.png)

### 25.
This something is Virtual Controller, which we will use to create a virtual
Xbox controller from our Wiimote HID device. It should open after installation:

![screenshot 25](/img_main/25.png)

### 26.
Click "Settings" and "IO Devices":

![screenshot 26](/img_main/26.png)

### 27.
A new window appears. On the "Physical" tab, click "Setup" and "Game Controllers":

![screenshot 27](/img_main/27.png)

### 28.
A new window appears.
Make sure to tick the "Enabled" box and lower the update interval to 10 ms.
Close the window.

![screenshot 28](/img_main/28.png)

### 29.
The Wiimote should now be listed in the "Physical" tab:

![screenshot 29](/img_main/29.png)

### 30.
Switch to the "Virtual" tab, click "Setup" and select "Xbox 360 Gamepad":

![screenshot 30](/img_main/30.png)

### 31.
A new window appears.
Make sure to tick the "Enabled" box and click "Install":

![screenshot 31](/img_main/31.png)

### 32.
You will be asked for confirmation.
Untick the "Always trust" checkbox, you don't need that.
Then click "Install".

![screenshot 32](/img_main/32.png)

### 33.
After installation, you will be asked to reboot your computer. Do it.
At this point you can be fairly sure our goal is achievable with your hardware.

![screenshot 33](/img_main/33.png)

### 34.
After rebooting make sure your Wiimote reconnects automatically.
If it is not the case, repeat the steps 10 to 22 to re-pair it.
Then launch Virtual Controller again,
click on "Settings" and "IO Devices":

![screenshot 34](/img_main/34.png)

### 35.
A new window appears.
switch to the "Virtual" tab, click "Setup" and select "Xbox 360 Gamepad":

![screenshot 35](/img_main/35.png)

### 36.
A new window appears.
Make sure to tick the "Enabled" box and click "Configurate":

![screenshot 36](/img_main/36.png)

### 37.
A new window appears.
Click "Plug In":

![screenshot 37](/img_main/37.png)

### 38.
You should hear Windows detecting a new device.
Close the two last windows and the virtual Xbox controller will appear:

![screenshot 38](/img_main/38.png)

### 39.
Close the "IO Devices" window.
In the main app, click "Settings" and this time select "Controls":

![screenshot 39](/img_main/39.png)

### 40.
In the "Controls" window you can click "Tools" to run the Quick Binding tool,
but it does not fit our use case. Just know it's here in case you need it.

![screenshot 40](/img_main/40.png)

### 41.
Instead, click "Bind" and "Create":

![screenshot 41](/img_main/41.png)

### 42.
A new window appears.
Reproduce these settings and click "Settings":

![screenshot 42](/img_main/42.png)

### 43.
In the popup window, tick "Use Input" and set the multiplier to 100%:

![screenshot 43](/img_main/43.png)

### 44.
Close the popup and click "OK".
The "Controls" window should list your new binding:

![screenshot 44](/img_main/44.png)

### 45.
Add another one to emulate the accelerator trigger like so.

![screenshot 45](/img_main/45.png)

### 46.
For this one make sure you do **not** tick "Use Input" though:
we will use a static value. Set it to 100%:

![screenshot 46](/img_main/46.png)

### 47.
Add another one to make Virtual Controller release the virtual trigger when the
associated button is released (you don't want your accelerator stuck, right?):

![screenshot 47](/img_main/47.png)

### 48.
Repeat the process for the braking trigger:

![screenshot 48](/img_main/48.png)

### 49.
Also set it to a static value of 100%:

![screenshot 49](/img_main/49.png)

### 50.
And don't forget to bind the release state:

![screenshot 50](/img_main/50.png)

### 51.
Bind the handbrake for true NFS Nitro drifting madness:

![screenshot 51](/img_main/51.png)

### 52.
And don't forget to bind its release state, buttons also need those:

![screenshot 52](/img_main/52.png)

### 53.
Your "Controls" window should now look like this:

![screenshot 53](/img_main/53.png)

### 54.
It is time to test these settings.
Close the "Controls" window, then select "Main" and "Run".

![screenshot 54](/img_main/54.png)

### 55.
Virtual Controller will start copying your inputs on the virtual Xbox gamepad.
Start Cyberpunk 2077, get in a vehicle, and enjoy.

You can leave the game running in the background and iterate easily by stopping
Virtual Controller, editing the settings and starting it again.

If you paid attention you might have noticed it saves and loads your last
settings automatically, but you can make backups with "Settings" and "Save".

![screenshot 55](/img_main/55.png)

## Honk, radio, etc.
Binding the honk and radio controls is left as an exercise for the reader :P
Virtual Controller is also very powerful and can dynamically switch bindings,
so it should be possible to bind other games controls to the wiimote/nunchuck
and toggle motion-controlled driving mode using a dedicated button. Have fun!

## HID-Wiimote button numbers
Need help understanding what button numbers correspond to?
Here's a trick that will work with any generic HID gamepad:

### 1.
Press `Win`+`R` and run `control panel`

![extra screenshot 1](/img_extra/1.png)

### 2.
The one and only Control Panel will show up.
Under "Hardware and Sound", select "View devices and printers"

![extra screenshot 2](/img_extra/2.png)

### 3.
Right-click your Wiimote and select "Game controller settings"

![extra screenshot 3](/img_extra/3.png)

### 4.
Select "Wiimote Device" and click on "Properties"

![extra screenshot 4](/img_extra/4.png)

### 5.
Windows will greet you with a visualization of the gamepad's functionalities.
Here I am pressing the `B` button, which we can see has `4` as an ID.
The Wiimote is also standing on my desk so we see using it as a steering wheel
directly impacts the `RX` value.

![extra screenshot 5](/img_extra/5.png)
