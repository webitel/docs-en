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

