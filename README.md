# HiveOS GDDR6X Temperatures for NVIDIA GPUs
#### For HiveOS versions BELOW 0.6-214@220331
##

This simple script reads temperatures from NVIDIA GPUs as reported by:

- t-rex v0.25.9+
- gminer 2.88+
- lolminer 1.47+

and adds them to the normal GPU statistics collected by HiveOS.

This script doesn't alter any HiveOS core files, so it's rather safe to use.

# Supported GPUs
All GDDR6X NVIDIA GPUs are supported as well as some GDDR6 (!):
- RTX 3090
- RTX 3080 Ti
- RTX 3080
- RTX 3070 Ti
- RTX 3060 Ti (GDDR6), only few known models, namely:
```
BIOS 94.04.38.40.17 (EVGA RTX 3060 Ti 8GB FTW3 ULTRA)
BIOS 94.04.38.00.F0 (MSI RTX 3060 Ti 8GB Gaming X TRIO)
```
- RTX 2080 Ti (GDDR6, only few models) 
- RTX 2080 (GDDR6, only few models)(Confirmed to work on Zotac)
- RTX A2000 (GDDR6)
- RTX A4000 (GDDR6)
- RTX A4500 (GDDR6)
- RTX A5000 (GDDR6)

# No HiveOS modifications needed
Please consider this a simple add-on on top of HiveOS.
What it really does, is getting data via API from the miners written above and patching the GPU stats json file that HiveOS collects periodically with the memory temperatures. When GPU data will be reported to HiveOS, it  the logs will have also memory temperatures added to it.

# Installation stable version (latest release 2022-03-31 04:44 UTC)
Simply open a shell on your HiveOS installation or click "Run command" on top and run (copy paste the whole thing and press ENTER):

```
curl https://raw.githubusercontent.com/cryptopoo/hiveos_gddr6x_temps/main/quick-install.sh | bash
```

![image](https://user-images.githubusercontent.com/102094145/159818529-1dadaa6a-542d-4251-9cf4-7bdbe7b9d9a9.png)

Or follow the instructions by watching one of these videos:

<a target="_blank" href="http://www.youtube.com/watch?v=e_Lqo_xFa6I"><img src="http://img.youtube.com/vi/e_Lqo_xFa6I/0.jpg" width="49%"></a>
<a target="_blank" href="http://www.youtube.com/watch?v=RnahyUMcZgY"><img src="http://img.youtube.com/vi/RnahyUMcZgY/0.jpg" width="49%"></a>

# Installation unstable / development version
The development version is updated more often in order to solve bugs or add support for more miners / cards.
Sometimes this version can be broken, so use this installation way only for testing or if you have issues with the stable version.

Simply open a shell on your HiveOS installation or click "Run command" on top and run (copy paste the whole thing and press ENTER):

```
curl https://raw.githubusercontent.com/cryptopoo/hiveos_gddr6x_temps/main/quick-install-unstable.sh | bash
```

# In case of problems / Uninstall instructions
If you face any problems, please create an issue here on github so that I can be aware of it and we can work out together a solution.

Additionally, you may try the unstable version as well (explained above). This version may contain enhancement that are not yet finalized or currently being tested.


You can uninstall the script with (copy paste the whole thing and press ENTER):

```
curl https://raw.githubusercontent.com/cryptopoo/hiveos_gddr6x_temps/main/quick-uninstall.sh | bash
```

Then go seek for help.

# Make autofan work with NVIDIA memory temps

In order for autofan to work with NVIDIA cards memory temperatures, you will need to apply a small patch to the `autofan` HiveOS script.  
Since this is a change to a core file of HiveOS, this hasn't been included in the normal `quick-install.sh` script and you will have to apply it manually after installing this add-on.
The patch is very simple, it passes memory temperatures to the function responsible for adjusting fan speed, just like it does for AMD cards, nothing different than that. There is no real alteration of the behavior of how the `autofan` module works per-se, so you can expect it to work as usual.
Please make sure to run on latest version of HiveOS before applying the patch and bear in mind that updating HiveOS might revert this patch (so you may need to apply it again):

```
curl https://raw.githubusercontent.com/cryptopoo/hiveos_gddr6x_temps/main/patch-autofan.sh | bash; autofan restart
```

The patch will be reverted if you uninstall this module.

# Special thanks
Special thanks to these people that spread the word through their Youtube channels:

- Rabid Miner (https://www.youtube.com/c/RabidMining)
- ChumpChangeXD (https://www.youtube.com/c/ChumpChangeXD)
- Juliano Caju (https://www.youtube.com/c/JulianoCaju)

# Consider donating to support my work
Do you like how this script is so minimally invasive in respect to HiveOS core files and the functionality it provides?  
**Please**, consider donating a small amount to thank me for my time! It will be very much appreciated!

Donations are accepted at the following addresses, in order of preference:

```
BTC    bc1q0xrs5cq7zwrnvz7dkzvgrzya48se6zgkt90sln
ETH    0x9b7A231147c8294cC558F080B26F948Bfd523A79
ETC    0xe9c8F439196fBA21f383AE69e8E4330B1493C335
BNB    0x9b7A231147c8294cC558F080B26F948Bfd523A79
RVN    RB2JTzcSxfZtWcQhYMCgad2M1T8Xi7dgPX
ERGO   9h1DrdXqQP3Aq3rdAPtLH4n5g9mQrLL2W3pYe152CkqPKbimu6w
MATIC  0x9b7A231147c8294cC558F080B26F948Bfd523A79

ZIL    zil13ctkfhgx5tdp48sewtmddtujfgsl87cqz38jug
FLUX   t1HyF9wDivycxNLNRzs9rRoEDwJ6hogDjpd
TRX    TFRKg3FTRbcR79CnpahMzf5yJu1dU4FQGn
FTM    0x9b7A231147c8294cC558F080B26F948Bfd523A79
AE     ak_2ekWFyFHPazAxMHbdGrdd3emVHzDo9iprwAMCw1aaTYg6YZAn
FIRO   aBYiGagsNdZE71bb2uAKKGyixBu6195uE3
DASH   XuuZxRNiK9BzhCDHRci8XBCoiz5GN9xzig
```

! :heart: Thank you :heart: !
