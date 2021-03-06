# TimeRegistration

Just a small tool to check flexTime balance before checking out.

## Install

```bash
$ npm install
$ ./timeReg.js || node timeReg.js || npm start
```

## Example use

Check the `--help` pages for all the options.


```bash
# Normal usage 
$ ./timeReg.js --start-time 07:45
# or equivalent
$ ./timeReg.js -s 07:45

# Possible to supply endTime to check flexTime balance
$ ./timeReg.js --start-time 07:45 --end-time 16:30
# or equivalent
$ ./timeReg.js -s 07:45 -e 16:30
```

## Example output

```bash
$ ./timeReg.js -s 07:30 -e 16:55

*****************************************************
******************* TIME MACHINE ********************
*****************************************************
***            Full day:    7.4 hours             ***
***            Break:      45 minutes             ***
*****************************************************
***            Day started         @ 07:30        ***
***            Half day ends       @ 11:12        ***
***            Full day ends       @ 15:39        ***
*****************************************************
*****************************************************
***                 End @ 16:55                   ***
***            -> Flex time == 01:16              ***
*****************************************************

```

## Example output with warning
```bash
$ ./timeReg.js -s 07:30 -e 13:55

*****************************************************
******************* TIME MACHINE ********************
*****************************************************
***            Full day:    7.4 hours             ***
***            Break:      45 minutes             ***
*****************************************************
***            Day started         @ 07:30        ***
***            Half day ends       @ 11:12        ***
***            Full day ends       @ 15:39        ***
*****************************************************
*****************************************************
***                 End @ 13:55                   ***
***            -> Flex time == -01:44              ***
*****************************************************

!!!!!!!!!!!!!!!!!!!!  WARNING !!!!!!!!!!!!!!!!!!!!!!!
!!!    FlexTime deduction is capped @ -96 min     !!!
!!! 1/2 day will be deducted from total Flextime  !!!
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

```

## Help menu
```bash
$ ./timeReg.js --help
Usage: timeReg [OPTIONS]

Options:
   -s, --start-time        Starting time formatted as hh:mm (ex. 08:53)
                           (default: 08:00)
   -e, --end-time          End time formatted as hh:mm (see above)
                           (default: current time)
   -b, --break             Length of break in minutes
                           (default: 45)
   -m, --max-flextime      Length of the flex-time cap in minutes
                           (default: 96)
```

