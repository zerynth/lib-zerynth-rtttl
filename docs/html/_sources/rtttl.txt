*************
RTTTL Module:
*************

.. module:: rtttl

This module contains class definitions for the "RTTTL" melody player to be used for driving buzzers or speakers connected to PWM pins.

Ring Tone Text Transfer Language (RTTTL) was developed by Nokia to be used to transfer ringtones to cellphone by Nokia.

The RTTTL format is a string divided into three sections: name, default value, and data.

The name section consists of a string describing the name of the ringtone. It can be no longer than 10 characters, and cannot contain a colon ":" character. (However, since the Smart Messaging specification allows names up to 15 characters in length, some applications processing RTTTL also do so.)
The default value section is a set of values separated by commas, where each value contains a key and a value separated by an = character, which describes certain defaults which should be adhered to during the execution of the ringtone. Possible names are

* d - duration
* o - octave
* b - beat, tempo

The data section consists of a set of character strings separated by commas, where each string contains a duration, pitch, octave and optional dotting (which increases the duration of the note by one half).
The format of RTTTL notation is similar to the Music Macro Language found in BASIC implementations present on many early microcomputers.
Various RTTTL melodies can be downloaded from http://ez4mobile.com/nokiatone/rtttf.htm and many other websites.
    
.. class:: tune(txt)

    This is the class for creating the melody to be played by the RTTTL player.
    The melody is passed as string
.. method:: play(pin,callback=None,restart=False)

    Start playing the melody actuating the PWM on the selected pin.

    It is also possible to pass a function as callback that will be called every time a note is played. 
    The callback passes the played note to the called function.

    Moreover, loop play is also possible by setting the restart parameter to True.
    
    * pin: Dx.PWM, it is the pin where the buzzer is connected.
    * callback: the function to be called every time a note is played. Played note will be passed to the called function.
    * restart: it activates the playloop.
.. method:: setbpm(bpm)

    Change the melody speed.

    bpm: RTTTL melodies include tempo definition in BPM, however through this function it is possible to manually change the melody speed.
