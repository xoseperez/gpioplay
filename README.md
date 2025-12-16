# GPIOd Play

Small project to show how to play tunes using the gpiod utility from bash.

## Requirements

The script requires gpiod suite version 2, for instance:

```
$ gpioset -v
gpioset (libgpiod) v2.2.1
Copyright (C) 2017-2023 Bartosz Golaszewski
License: GPL-2.0-or-later
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
```

It also requires `bc`, but it will install it if not found.

## Use

Run the script without parameters to know the availble songs (under the `songs` folder):

```
$ ./gpioplay 

You have to pass at least a song name as argument

Usage: ./gpioplay [-c/--chip <chip_id>] [-g/--gpio <gpio>] <song>

Existing songs:
  * furelise
  * merrychristmas
  * pinkpanther
  * starwars
```

The script uses `gpiochip0` and GPIO `16` by default. Your buzzer will probably be connected to a different GPIO or even to a different chip:

```
./gpioplay -g 23 pinkpanther # buzzer connected to chip 0, GPIO 23
./gpioplay --chip 4 --gpio 6 pinkpanther # buzzer connected to chip 4, GPIO 6 (like would be on a Raspberry Pi 5)
./gpioplay --chip gpiochip4 --gpio 6 pinkpanther # you can also use the full chip name
```

Run the script with the song name as argument to play that specific song:

```
$ ./gpioplay -g 23 pinkpanther

Playing pinkpanther!!
```

Enjoy :)

