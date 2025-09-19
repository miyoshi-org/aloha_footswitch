[![Build Status](https://github.com/rgerganov/footswitch/workflows/CI/badge.svg)](https://github.com/rgerganov/footswitch/actions)

# Aloha Footswitch

Aloha Footswitch is a utility to configure and use a USB footswitch device on Linux. 
You can assign keys or key combinations to each pedal for controlling applications hands-free.

## Installation

Install required libraries:

```bash
sudo apt update
sudo apt install libhidapi-dev libhidapi-hidraw0 libhidapi-libusb0
````

Clone the repository and initialize submodules:

```bash
git clone git@github.com:miyoshi-org/aloha_footswitch.git
cd aloha_footswitch
git submodule update --init --recursive
```

Add udev rules for device permissions:

```bash
sudo cp 3rd_party/footswitch/19-footswitch.rules /etc/udev/rules.d/
sudo udevadm control --reload-rules
```

Build and install the footswitch utility:

```bash
cd 3rd_party/footswitch/
make
sudo make install
```

## Usage

Run the footswitch with custom key mappings. Example:

```bash
footswitch -1 -k left -2 -m ctrl -k c -3 -k right
```

* `-1 -k left` : map the first pedal to the Left arrow key
* `-2 -m ctrl -k c` : map the second pedal to Ctrl+C
* `-3 -k right` : map the third pedal to the Right arrow key