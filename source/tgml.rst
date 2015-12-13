.. _tgml:

TGML
====

Syntax of teletone scripts.

Legend
++++++

0-9,a-d,*,# (standard DTMF tones)

variables: c,r,d,v,>,<,+,w,l,L,loop,%

- c=x Sets the number of channels.
- r=x Sets the sample rate.
- d=x Sets the default tone duration.
- v=x Sets the default volume (-63.0dB to 0.0dB).
- >=x Number of ms per interval for volume decrease.
- <=x Number of ms per interval for volume increase.
- +=x Number of dB to step per interval (used by '<' and '>').
- w=x Default silence after each tone.
- l=x Number of times to repeat each tone in the script.
- L=x Number of times to repeat the the whole script.
- loops=x Like L, but doesn't pre-allocate a buffer for total duration, only one loop worth, then programmatically loops it (more mem efficient).
- %=x A generic tone specified by a duration, a wait and a list of frequencies.

The values for '+' and 'v' may be decimal numbers.

Standard tones can have custom duration per use with the () modifier 7(1000, 500) to generate DTMF 7 for 1 second then pause .5 seconds.

Global varaibles
++++++++++++++++

Predefined global variables with country ringback tone:

- be-ring=%(1000,3000,425)
- ca-ring=%(2000,4000,440,480)
- cn-ring=%(1000,4000,450)
- cy-ring=%(1500,3000,425)
- cz-ring=%(1000,4000,425)
- de-ring=%(1000,4000,425)
- dk-ring=%(1000,4000,425)
- dz-ring=%(1500,3500,425)
- eg-ring=%(2000,1000,475,375)
- es-ring=%(1500,3000,425)
- fi-ring=%(1000,4000,425)
- fr-ring=%(1500,3500,440)
- hk-ring=%(400,200,440,480);%(400,3000,440,480)
- hu-ring=%(1250,3750,425)
- il-ring=%(1000,3000,400)
- in-ring=%(400,200,425,375);%(400,2000,425,375)
- jp-ring=%(1000,2000,420,380)
- ko-ring=%(1000,2000,440,480)
- pk-ring=%(1000,2000,400)
- pl-ring=%(1000,4000,425)
- ro-ring=%(1850,4150,475,425)
- rs-ring=%(1000,4000,425)
- ru-ring=%(800,3200,425)
- sa-ring=%(1200,4600,425)
- tr-ring=%(2000,4000,450)
- uk-ring=%(400,200,400,450);%(400,2000,400,450)
- us-ring=%(2000,4000,440,480)

Examples
++++++++

ITU-T Recommendation Q.35 "Technical Characteristics of Tones for Telephone Service" defines many of these tones. They are provided here for your convenience, and because they make great examples. Additionally, RFC 2833 references ITU-T E.182 "`Application of tones and recorded announcements in telephone services <http://www.itu.int/dms_pub/itu-t/opb/sp/T-SP-E.180-2010-PDF-E.pdf>`_" for when to use certain tones in RTP. You may want to look at ITU-T Recommendation E.180 for different countries, what tones are used, etc.

UK Ring Tone [400+450 Hz on for 400ms off for 200ms then 400+450 Hz on for 400ms off for 2000ms]

::

   %(400,200,400,450);%(400,2000,400,450)

US Ring Tone [440+480 Hz on for 2000ms off for 4000ms]

::

    %(2000,4000,440,480)

ITU E.182 Calling card service tone (AT&T BONG) [volume level -7DB, 941.0Hz +1477.0Hz (DTMF #) for 100ms with no wait. 350.0Hz+440.0Hz (US DIALTONE) for 1400ms with even decay of .1 dB over 2ms

::

    v=-7;%(100,0,941.0,1477.0);v=-7;>=2;+=.1;%(1400,0,350,440)

Russian Busy Tone 425Hz 400ms on 400ms off

::

    %(400,400,425)

Dialtone Deutsche Telekom Germany 425Hz (used for DISA, Callthru)

::

    %(10000,0,425)

Australian ringback tone

::

    %(400,200,400,425);%(400,2000,400,425)

