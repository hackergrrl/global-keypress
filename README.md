# global-keypress

> Global key press event emitter.

NOTE: requires sudo privileges.

Supports only Linux right now. Patches for Mac OS and Windows welcome!

## About
The program outputs lines to stdout of either the form
```
pressed <KEY>
```
or
```
released <KEY>
```

It can be used to pipe keypress info into another program, which can capture
whatever keys it is interested in.


## Install

```shell
git clone https://github.com/hackergrrl/global-keypress
cd global-keypress
./compile

# sudo bin/globalkeypress
```

## Example

Play a sound effect when the right shift key is pressed.

```shell
#!/bin/bash

IFS="\n"
sudo globalkeypress | while read line; do
  if echo $line | grep -q "pressed <RShift>"; then
    aplay -q sfx.wav
  fi
done
```

## License

MIT
