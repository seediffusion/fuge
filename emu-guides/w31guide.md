# The accessible Windows 3.1 setup guide, by SeedyThreeSixty

Hello, blind retro computing nerds, and welcome to the accessible Windows 3.1 setup guide.

Whether your very first computer ran Windows 3.x, or you're just experiencing it for the first time, this guide will explain everything you need to know in order to get a fully functional Windows 3.1 installation, complete with working sound and a screen reader.

* * *

## Section 1: What is Windows 3.1?

Microsoft Windows 3.1 was released on April 6th, 1992\. Unlike the Windows we know today, Windows 3.1 is not a full-blown operating system. Instead, it is an operating environment, or shell, that runs inside of MS-DOS, or Microsoft Disk Operating System. Despite this, Windows 3.1 still needs its own set of programs, drivers and system utilities to function.

Windows 3.1 does not include the traditional start menu, desktop or Windows Explorer we've come to know and love today; those were introduced in its successor, Windows 95\. Rather, Windows 3.1 programs are organised into program groups. These program groups can either be created by you, the user, or generated automatically by a program installer. These program groups can be accessed through the Window menu of the Windows 3.1 shell.

By default, Windows 3.1 does not include sound support or a screen reader for the blind and visually impaired. Therefore, we must install these things ourselves. Fear not, though, this guide will walk you through all these steps, and a whole lot more.

* * *

## Section 2: Notes and disclaimer

*   Seedy, the author of this guide, shall take no responsibility for any data loss or system damage that should arise as a result of following this guide.
*   The information and instructions contained within this guide have been thoroughly researched and tested. Care has been taken to ensure the highest level of accuracy. That said, no 2 computers are the same, and no 2 people process instructions in the same way. Therefore, what works fine for one person might not work so well for another, and some might find one or more of the instructions harder to follow than others.
*   This guide will only cover DOSBox-X for Windows.

* * *

## Section 3: Preconfigured

If you just want a preconfigured Windows 3.1 installation without going through the steps, you can [download a preinstalled DOSBox-X package](/files/DOSBox-X_preinstalled.zip). The only thing you'll need to do before running DOSBox-X is install com0com, the virtual serial port driver.

Do the following to launch the Windows 3.1 environment in DOSBox-X, assuming com0com is installed.

1.  Navigate to the vbns-ao2 folder inside the folder where you extracted the preconfigured DOSBox-X, and launch the file called start_emu to start up the virtual Braille-n-Speak.
2.  Navigate to the folder where you extracted the preconfigured DOSBox-X, and launch the file called DOSBox-X.exe. If your system isn't configured to show file extensions, the second DOSBox-x file is the one you want; the first one is the program's configuration file. You can right arrow twice on a file to get its type. If it says application, that's the executable file you want. You should hear the ASAP screen reader for DOS start speaking when DOSBox-X launches.
3.  In the DOSBox-X prompt, type the following commands to start Windows 3.1, pressing Enter after typing each command.
    1.  > cd windows

    2.  > win

If you feel comfortable enough to set everything up yourself, let's proceed to the next section.

* * *

## Section 4: Minimum requirements

Hear are the things you'll need to get started following this guide. We'll download everything else later on as we need it.

1.  DOSBox-X, the MS-DOS emulator we'll be using for this exercise.
    *   [64-bit download](https://github.com/joncampbell123/dosbox-x/releases/download/dosbox-x-v2024.07.01/dosbox-x-mingw-win64-20240702034526.zip)
    *   [32-bit download](https://github.com/joncampbell123/dosbox-x/releases/download/dosbox-x-v2024.07.01/dosbox-x-mingw-win32-20240702034526.zip)

Go inside the mingw-build folder with your zip archiver of choice, and copy either the mingw or mingw-sdl2 folders to a location of your choice. Rename the newly copied folder to something easy to remember, like DOSBox. Go inside the copied folder and press Control + Shift + N to create a new folder. For the folder name, type

> CDrive

and press Enter. You can call this folder whatever you like, but we're using CDrive because it's easy to remember. The other reason for this name will make sense later on.*   ASAP, the screen reader for MS-DOS. [download ASAP](/files/asap.zip) Extract the downloaded ASAP zip file into the CDrive folder inside your DOSBox folder.*   com0com, the virtual serial port driver. The screen readers we will be using require a hardware speech synthesizer. We can get around this problem using a virtual serial port driver, which is where com0com comes into play. [Download com0com](/files/com0com.zip)*   vbns-ao2, the tool we'll be using to emulate a Braille-n-Speak synthesizer. [Download vbns-ao2](/files/vbns-ao2.zip) This tool works by piping the output of a screen reader that is configured to use a Braille-n-Speak synthesizer through a screen reader running on your physical machine, such as NVDA or JAWS. You can also tell it to pipe through SAPI 5 if you want. For convenience, a file called start_emu.bat is included in the vbns-ao2 folder. Simply extract the zip file and run the start_emu file to launch the virtualised Braille-n-Speak. When it launches, your screen reader should say 'ready'.

* * *

## Section 5: Installing com0com

1.  Extract the com0com zip file we downloaded in section 4 to a location of your choice.
2.  Navigate to the location of the extracted files, and launch any of these setup files depending on your OS architecture.

*   64-bit systems: setup-x64
*   32-bit systems: setup-x86

4.  Answer yes to the UAC prompt with Alt + Y, then the com0com setup wizzard should appear. If not, Alt + Tab until you land on it.
5.  Press Alt + N in the setup wizzard to get past the initial screen.
6.  Because you totally sat down and read that license agreement, press Alt + A to accept.
7.  Press the End key, or FN + Right Arrow if you don't have an End key on your keyboard, press the space bar to uncheck the very last box in the components to install screen, and press Alt + N.
8.  You will be asked to choose where the com0com program files should be installed. The default location is fine, so press Alt + I to start the installation.
9.  During the install process, you'll get a windows security dialog. Unfortunately for screen reader users, this dialog does not take focus automatically, so you'll have to find it with Alt + Tab. Once you do find it, tab to the install button in the dialog and press the space bar.
10.  Wait for the installation to complete, then press Alt + F when the dialog appears.

Now, we need to configure the serial ports.

1.  Press Windows + R to open the run dialog, type cmd, press Control + Shift + Enter, and answer yes to the UAC prompt.
2.  Type the following depending on your OS architecture.

*   64-bit systems:

    > "%programfiles(x86)%\com0com\setupc.exe"

*   32-bit systems:

    > "%programfiles%\com0com\setupc.exe"

4.  Execute the following commands.
    *   > change CNCA0 PortName=COM8

    *   > change CNCB0 PortName=COM9

5.  Type quit to get out of com0com setup.
6.  Type exit to get out of the command prompt.

### An important note for secure boot users

If secure boot is enabled on your Windows 10 or 11 machine, and your system has not been upgraded from a prior version of Windows, you will need to enable driver test signing before installing com0com. You can do so by running [this tool](/files/TestDriver.exe) as an administrator. Simply right click on the downloaded executable and select run as administrator.

Note: By enabling driver test signing, you are allowing potentially dangerous drivers on to your system. We know that com0com is completely harmless, but that doesn't mean all drivers and programs are completely harmless. Always be careful of the files you download to your computer.

* * *

## Section 6: configuring DOSBox-X

While DOSBox-X has a graphical configuration tool, it is completely inaccessible to screen reader users. Therefore, we have to modify the DOSBox-X.conf file in a text editor to change settings.

Navigate to your DOSBox-X install folder and open DOSBox-X.conf in your text editor of choice. For those who don't have file extensions showing, DOSBox-X.conf is the very first file with 'DOSBox-X' in its name. Right arrow twice on the file to find its type. If it says conf file, that's the right file to open.

We need to modify 3 existing lines, and add 3 new lines. In most text editors, you can jump to a specific line number by pressing Control + G, typing in the desired line number and pressing Enter.

### Lines to modify

#### Line 211

change

> hostkey = mapper

to

> hostkey = altshift

This changes the modifier key used to perform special functions in DOSBox-X to something easier to access; F11 is the default on Windows.

#### Line 212

Change

> mapper send key = ctrlaltdel

to

> mapper send key = alttab

Alt + Tab doesn't get passed to DOSBox-X when we're in the Windows environment, so we have to assign a special hotkey to it. In this case, it's Alt + Shift + Delete, or Alt + Shift + FN + Backspace on a notebook keyboard.

#### Line 941

Change

> serial1 = dummy

to

> serial1 = directserial realport:com9

This tells DOSBox-X to use the physical (or virtual in our case) COM9 serial port on our machine.

### Lines to add

Press Control + End, or Control + FN + Right Arrow, to go to the very bottom of the file, and add these 3 lines.

*   mount C: CDrive
*   C:
*   asap\asap.com bns com1

Now, every time we launch DOSBox-X, it will mount the C: drive using the CDrive folder we made in section 4, change to the C: drive, and start the ASAP screen reader.

* * *

## Section 7: Installing Windows

After all that installing and configuring, it's finally time for the fun part, installing Windows 3.1!

For convenience, you can [download a pre-extracted Windows for Workgroups 3.11 setup](/files/Win31.zip). This zip file contains all the files required to set up Windows in a single folder, meaning you don't have to keep swapping floppy disks. Simply extract the zip file into your DOSBox-X CDrive folder.

Windows for Workgroups 3.11 is an updated version of Windows 3.1 from 1993 that includes networking support and a few other improvements. We won't cover networking in this guide, but if there's enough demand for it, I'll look into adding a section on networking.

So, without any further ado, let's install Windows!

1.  Navigate to your vbns-ao2 folder and open the start_emu file to launch the virtual Braille-n-Speak.
2.  Navigate to your DOSBox-X folder and launch the DOSBox-X executable file. ASAP should start to speak right away when DOSBox-X fires up. If not, go back through the guide and make sure you installed and configured everything correctly.
3.  Type

    > cd Win31

    to change to the Win31 folder we extracted earlier.
4.  Type

    > setup

    to launch the Windows for Workgroups 3.11 setup program.
5.  Press Enter to get past the welcome screen and start setup.
6.  We can now choose between 2 setup types: express, and custom. To speed things up, we'll choose Express, which will let Windows configure default settings for us. Express is highlighted, so press Enter.
7.  Wait 2 to 3 minutes for files to be copied and hardware to be found. With the NVDA screen reader, you can use OCR to check on progress with the NVDA modifier key + the letter R.
8.  Windows will now ask you to enter your name, company, and product number. You are automatically placed in the name field, so type your full name or common handle. If you're not in a company and/or don't have a Windows registration card, you can just leave these fields blank. Otherwise, press the Tab key to navigate to the appropriate field and type in your data. From the name field, Tab once for company, Tab again for product number. Once the desired information has been entered, press Enter.
9.  You will be asked to verify if the data you just entered is right. If so, press Enter.
10.  Wait 1 to 2 minutes for files to be copied.
11.  The printer installation wizzard will then appear. Just press Enter here, as we won't be installing any printers.
12.  At the network setup screen, press Enter, as we won't be installing networking.
13.  5 to 10 seconds later, A Windows tutorial screen will appear. We don't want to go through the inaccessible tutorial, so press the Tab key once and press Enter.
14.  Press Enter one more time to exit setup. You will be rebooted back to MS-DOS. Windows for Workgroups 3.11 is successfully installed!

* * *

## Section 8: Sound drivers

This Windows installation is pretty useless to us right now because we have no audio. By default, DOSBox-X emulates a Creative Sound Blaster 16 card. We need to install the drivers for this card in order for Windows to see it and give us sound.

1.  [Download the SB16 driver](/files/sb16w31.zip) and extract it to your CDrive folder.
2.  In DOSBox-X, type

    > cd sb16win31

    to change to the driver directory.
3.  type

    > install

    to start the installer.
4.  When ASAP prompts you, press enter to dismiss the initial screen. ASAP will speak very minimally during this setup, so feel free to use OCR if you need to.
5.  Press Enter for recommended settings.
6.  3 to 5 seconds later, a list of default settings will appear. Up arrow twice, press Enter, and press Enter again to choose the default path of C:\Windows. Press Enter once again to accept the settings.
7.  after 5 to 10 seconds, another list of settings will come up. Press the Up Arrow 3 times, press Enter, Down Arrow once to set the IRQ value to 7, and press Enter again. We're satisfied with those settings, so press Enter once again.
8.  The rest of the install process will take 3 to 5 minutes. If you get a backup/skip/proceed prompt, Down Arrow twice to the proceed option and press Enter.
9.  When the installation is complete, press F10 to reboot MS-DOS.
10.  Type the following commands to launch Windows and test the sound.
    *   cd windows
    *   win
11.  If everything worked, you should hear a chime to indicate Windows has started.
12.  Finally, Press Escape to dismiss the audio software dialog.

* * *

## Section 9: The screen reader

The last thing we need to do to make this thing accessible is install a screen reader. The reader we will be using in this exercise is Window-Eyes 3.1\. That's nice and easy to remember, because Windows 3.1, Window-Eyes 3.1.

Note: in Windows 3.x, Window-Eyes will not provide speech during setup.

1.  [Download Window-Eyes 3.1](/files/wineyes.zip) and extract it into your CDrive folder.
2.  In DOSBox-X, With the Windows 3.1 shell in view, press Alt + F, then the letter R for Run.
3.  Type

    > C:\wineyes\setup

    and press Enter to launch the setup program. In a few seconds, you should hear a short audio message welcoming you to Window-Eyes 3.1.
4.  After the welcome message, a dialog will appear asking if you want to use quick setup. We do, so press Y.
5.  You will then be asked to enter your name and company; sound familiar? None of this matters and we can just leave it blank, so press Enter.
6.  In the synthesizer selection screen, press Shift + Tab twice, press the letter B for braille, Up Arrow once, and press enter.
7.  In 1 to 2 minutes, the setup will be complete. Press Enter, and you will once again be rebooted back to DOS.
8.  When you launch Windows 3.1 again, Window-Eyes should start to speak, and you can use the arrow keys to move around.

* * *

## Section 10: The sound of music

Midi freaks, I see you! DOSBox-X does a good job of emulating SB16 midi, but it sounds terrible by default. Let's sort that out now!

1.  In the Windows 3.1 shell, press Alt + W to access the window menu.
2.  Down Arrow until you find the 'Main' program group and press Enter.
3.  Inside the program group, press C for Control Panel and press Enter.
4.  Inside the Windows control panel, press the letter M until you hear Midi Mapper, and press Enter.
5.  We want to choose the SB16 All Midi option, so press Tab once, press Home or FN + Left Arrow to highlight the option, press Enter to select, and Alt + F4 to get out of Control Panel.
6.  To test it out, press Alt + F, press R for Run, type canyon.mid, hit Enter, and press the space bar to play the file. See how much better that is?

* * *

## Section 11: Conclusion

Congratulations! You now have a fully working and accessible package of MS-DOS and Windows 3.1! Feel free to explore the environment, get a feel for the different program groups, Windows settings, and just play around. If there's enough demand, I'll look into installing a game or 2!

To shut down DOSBox-X at any time, press Control + F9.

* * *

## Section 12: Credits and thanks

*   Huge thanks to Tyler Spivey's [DOSBox guide](https://allinaccess.com/dosbox-guide/) which inspired this whole project!
*   The [DOSBox-X wiki](https://dosbox-x.com/wiki/#Home) was a great help when writing this guide, especially when it came to downloading drivers.
*   [Jake Gross's website](https://datajake.braillescreen.net) is a huge library of retro programs, games, audio files, software manuals, midi files and more.

## Section 13: Connect with Seedy

*   [Visit my personal website](https://seedy.cc)
*   [Visit the Seediffusion site](https://seediffusion.cc)
*   [Follow me on Mastodon](https://fwoof.space/@TheCube)
*   [Follow Seediffusion on Mastodon](https://tweesecake.social/@seediffusion)
*   [Send me an email](mailto:seedy@seediffusion.cc?subject=Hi Seedy)
*   Discord: seedy360
*   Skype: SeedyThreeSixty
*   [Send me a telegram](https://t.me/SeedyThreeSixty)
*   [Support Seedy on Ko-Fi](https://ko-fi.com/seediffusion)
*   PayPal: seedy360@hotmail.com