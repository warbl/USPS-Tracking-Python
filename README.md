# USPS-Tracking-Python
![PyPI - License](https://img.shields.io/pypi/l/usps-tracking-tool) ![PyPI](https://img.shields.io/pypi/v/usps-tracking-tool)

Track your packages with the USPS Track Request API using Python 3.

A simple CLI package tracking tool with no dependencies required.

IMPORTANT: You must provide your API key in config.json first before using.
Sign up at: https://www.usps.com/business/web-tools-apis/welcome.htm

You may also provide the USPS API key as an environment variable: `USPS_API_KEY`
which can be used if program does not see an API key in the config.json file.

## Installation

Available through PyPI: https://pypi.org/project/usps-tracking-tool/

`pip3 install usps_tracking_tool`

After installing, you can run this program in the command line by using the command `usps_tracking_tool`.

## Usage

If running from the project directory, the program is available in the `usps_tracking_tool` folder. 
In that case, please substitute the `usps-tracking-tool` command in the below examples with `python3 tracking.py`.

You can track single/multiple shipment(s) by executing the program as follows:

```
usps-tracking-tool
usps-tracking-tool ABC1234567890
usps-tracking-tool ABC1234567890 DEF1234567890 GHI1234567890
```

If you run the program without a tracking number, it will prompt you for a tracking number (you may input multiple tracking numbers by separating them with spaces).

## Example

```
user@system:~$ usps-tracking-tool
Enter tracking numbers separated by spaces: ABC1234567890 DEF1234567890 GHI1234567890

Package #1:
 Your item arrived at the PHILADELPHIA, PA 19101 post office at 11:02 am on June 19, 2017 and is ready for pickup.
  ├ Arrived at Unit, June 19, 2017, 10:33 am, PHILADELPHIA, PA 19104
  ├ Departed USPS Facility, June 17, 2017, 2:40 pm, PHILADELPHIA, PA 19116
  ├ Arrived at USPS Facility, June 17, 2017, 2:22 pm, PHILADELPHIA, PA 19116
  ├ Processed Through Facility, June 15, 2017, 1:29 am, ISC NEW YORK NY(USPS)
  ├ Origin Post is Preparing Shipment
  ├ Processed Through Facility, June 10, 2017, 6:00 am, TOKYO INT V BAG 2, JAPAN
  └ Acceptance, June 6, 2017, 1:26 pm, JAPAN

Package #2:
 Your item was delivered at 6:14 pm on July 6, 2017 in PHILADELPHIA, PA 19104.
  ├ Sorting Complete, July 6, 2017, 10:29 am, PHILADELPHIA, PA 19101
  ├ Available for Pickup, July 6, 2017, 8:29 am, PHILADELPHIA, PA 19101
  ├ Arrived at Post Office, July 6, 2017, 8:05 am, PHILADELPHIA, PA 19104
  ├ Arrived at USPS Destination Facility, July 6, 2017, 2:00 am, PHILADELPHIA, PA 19176
  ├ Processed Through Facility, July 5, 2017, 6:41 pm, ISC NEW YORK NY(USPS)
  ├ Origin Post is Preparing Shipment
  ├ Processed Through Facility, July 5, 2017, 6:20 am, TOKYO INT CONTAINER 1, JAPAN
  ├ Processed Through Facility, July 4, 2017, 8:01 pm, TOKYO INT, JAPAN
  └ Acceptance, July 4, 2017, 4:00 pm, JAPAN

Package #3:
 The Postal Service could not locate the tracking information for your request. Please verify your tracking number and try again later.
```

You can use arguments to change the output format, like so:

```
user@system:~$ usps-tracking-tool -h
usage: usps-tracking-tool [-h] [-s] [-n] [-m] [-a]
                   [TRACKING_NUMBER [TRACKING_NUMBER ...]]

Tracks USPS numbers via Python.

positional arguments:
  TRACKING_NUMBER  a tracking number

optional arguments:
  -h, --help       show this help message and exit
  -s               Show tracking number in output
  -n               Hide extended tracking information
  -m               Display tracking information concisely (minimal UI)
  -a               Display the API key currently being used
```

```
user@system:~$ usps-tracking-tool ABC1234567890 -m
Your item was delivered at 6:14 pm on July 6, 2017 in PHILADELPHIA, PA 19104.
  ├ Sorting Complete, July 6, 2017, 10:29 am, PHILADELPHIA, PA 19101
  ├ Available for Pickup, July 6, 2017, 8:29 am, PHILADELPHIA, PA 19101
  ├ Arrived at Post Office, July 6, 2017, 8:05 am, PHILADELPHIA, PA 19104
  ├ Arrived at USPS Destination Facility, July 6, 2017, 2:00 am, PHILADELPHIA, PA 19176
  ├ Processed Through Facility, July 5, 2017, 6:41 pm, ISC NEW YORK NY(USPS)
  ├ Origin Post is Preparing Shipment
  ├ Processed Through Facility, July 5, 2017, 6:20 am, TOKYO INT CONTAINER 1, JAPAN
  ├ Processed Through Facility, July 4, 2017, 8:01 pm, TOKYO INT, JAPAN
  └ Acceptance, July 4, 2017, 4:00 pm, JAPAN
```

```
user@system:~$ usps-tracking-tool ABC1234567890 -mn
Your item was delivered at 6:14 pm on July 6, 2017 in PHILADELPHIA, PA 19104.
```

```
user@system:~$ usps-tracking-tool -a
The current API key being used is: API_KEY_HERE
API key is being sourced from environment variable USPS_API_KEY
```

This program was tested with Python 3.5.3 on Debian 10, Python 3.6.8 on Ubuntu 18.04, and may not be compatible with previous releases.

