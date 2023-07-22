# GSM5_IMSICATCHER_HALFMITM_SPOOFING-REAL-OPERATOR-BTS
* [motorola](https://www.youtube.com/watch?v=ZKa86zAWmQY&pp=ygURZ3NtIHNuaWZmaW5nIDI5YzM%3D) documentation
* [spoofing](https://github.com/godfuzz3r/osmo-nitb-scripts/tree/master)
* [phddays](https://sudonull.com/post/97315-MiTM-Mobile-contest-how-they-broke-mobile-communications-at-PHDays-V-Positive-Technologies-blog)
# Half MITM = Fake BTS only
<p align="center">
  <img width="600" height="400" src="https://github.com/SitrakaResearchAndPOC/GSM_IMSICATCHER_HALFMITM_SPOOFING-SMS-WITH-PHYSICAL-MS/blob/main/2G.jpg">
</p>

# Protocol flow
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/GSM5_IMSICATCHER_HALFMITM_SPOOFING-REAL-OPERATOR-BTS/blob/main/imsi-catcher-volte.jpg">
</p>

# Why it is possible ?
* Fake base station with open ciphering named A5/0, and spoof real operator network; the  network could be GSM(sms, call), and GPRS, EDGE

# Attack limitations and advantages 
* local attack but could be targeting (to find local victim)
* victim couldn't be reached on the real network (indeed call and sms)
* could be detectable with rooted phone and application like imsi-catcher detector, snoopsnitch because of open network
# Devices  
* USRP

# Pratices
* Install DragonOS 29 or 30 for USRP 
* Create fake bts with more specifications [demos](https://www.youtube.com/watch?v=fQSu9cBaojc&pp=ugMICgJmchABGAHKBRRjaHJpcyBwYWdldCArIGRlZmNvbg%3D%3D) [pdf_en]() [pdf_fr]()
* Open ciphering (A5/0)
* Configure power as big as possible or use power amplifier
* MCC, MNC, band, arfcn, short name and long name like the operator (use network signal guru to find the configuration)
* LAC not like the operator (the phone think it makes handover)
* Use jamming or redirection attack for more advanced attack
* creating selective denied of service attack (imsi) by using lur (location update reject) [demos](https://www.youtube.com/watch?v=OcYl_NH_e4E&t=436s) [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_IMSICATCHER_HALFMITM_SPOOFING-REAL-OPERATOR-BTS/blob/main/Nuevos%20escenarios%20de%20ataque%20con%20estaci%C3%B3n%20base%20falsa%20GSM_GPRS.pdf)
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/GSM5_IMSICATCHER_HALFMITM_SPOOFING-REAL-OPERATOR-BTS/blob/main/lur_gsm_dangereous.jpg">
</p>

# Proposition of solution :
In openbsc.cfg
```
network country code 001
mobile network code 1
short name dragonOS
long name dragonOS
band GSM1900
arfcn 526
nominal power 100
```
In osmo-bts.cfg 
```
band 1900
```
For denied of service change location update reject cause, the default cause is numbered 13
```
location updating reject cause 13
```



