# DIY-Midi-Controller

## English

This project aims to teach artists, and hobbyists in general, how to build their own MIDI controllers, with little or no prior knowledge in electronics and/or programming.

The "Nerd Musician Pro" is a project created by Gustavo Silveira. Visit the website for more nerd musical related tutorials!

https://www.musiconerd.com/nerd-musician-pro/


## Português

Este projeto tem como objetivo permitir que artistas, e hobbystas em geral, possam aprender a construir os sues próprios controlaodres MIDI, com pouco, ou sem conhecimento prévio em eletrônica e/ou programação.

O "Fazendo Msica com Arduino" é um projeto idealizado por Gustavo Silveira. Acesse o site para mais tutoriais relacionados a mais nerdices musicais!

Conheça o curso completo do FMcA >> https://www.musiconerd.com/curso-completo

www.musiconerd.com
gustavosilveira@muiconerd.com


# Debugging Code Wiki

## Introduction

This sketch reads the Arduino's digital and analog ports and sends MIDI notes and MIDI control change. It was created by Gustavo Silveira in 2023. For more information and other projects, visit the following links:

- [Musiconerd](http://www.musiconerd.com)
- [YouTube](http://www.youtube.com/musiconerd)
- [Facebook](http://facebook.com/musiconerdmusiconerd)
- [Instagram](http://instagram.com/musiconerd/)
- [Gustavo Silveira](http://www.gustavosilveira.net)
- Email: gustavosilveira@musiconerd.com

If you are using this for anything other than personal use, don't forget to give credit.

## Setup Instructions

### Choosing Your Board

Define your board by choosing one of the following options and uncomment the corresponding line:
- `#define ATMEGA328 1` if using ATmega328 (e.g., Uno, Mega, Nano)
- `#define ATMEGA32U4 1` if using ATmega32U4 (e.g., Micro, Pro Micro, Leonardo)
- `#define TEENSY 1` if using a Teensy board
- `#define DEBUG 1` if you just want to debug the code in the serial monitor

### Using Buttons

If you are using buttons, ensure the following line is uncommented:
```cpp
#define USING_BUTTONS 1
```

### Using Potentiometers

If you are using potentiometers, ensure the following line is uncommented:
```cpp
#define USING_POTENTIOMETERS 1
```

### Libraries

Include the appropriate MIDI library based on your board selection.

### Example Connections

**Buttons:**
```cpp
const int N_BUTTONS = 3;
const int BUTTON_ARDUINO_PIN[N_BUTTONS] = { 2, 3, 4 };
```

**Potentiometers:**
```cpp
const int N_POTS = 2;
const int POT_ARDUINO_PIN[N_POTS] = { A0, A1 };
```

### Responsive Analog Read

For potentiometers, include the `ResponsiveAnalogRead` library:
```cpp
#include <ResponsiveAnalogRead.h>
```

## Code Overview

### Setup

In the `setup()` function, initialize the serial communication and configure the pins for buttons and potentiometers.

### Loop

In the `loop()` function, call the `buttons()` and `potentiometers()` functions to handle the input and send the appropriate MIDI messages.

### Buttons

The `buttons()` function reads the state of each button, debounces the input, and sends MIDI note on/off messages.

### Potentiometers

The `potentiometers()` function reads the state of each potentiometer, smooths the input using `ResponsiveAnalogRead`, and sends MIDI control change messages.

## MIDI Functions for ATmega32U4

The following functions handle MIDI messages for the ATmega32U4 board using the MIDIUSB library:
```cpp
void noteOn(byte channel, byte pitch, byte velocity);
void noteOff(byte channel, byte pitch, byte velocity);
void controlChange(byte channel, byte control, byte value);
```

## Troubleshooting

- Ensure the correct board and USB port are selected in the Arduino IDE.
- Check for correct library installations.
- Use the serial monitor to debug and verify the outputs.
- Use a multimeter to check circuit continuity if hardware issues are suspected.

## Conclusion

This sketch allows you to interface with buttons and potentiometers, sending MIDI messages for musical applications. Customize the code as needed for your specific project requirements.

