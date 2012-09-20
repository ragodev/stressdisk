StressDisk
==========

This is a program designed to stress test your disks and find failures
in them.

Use it to soak test your new disks / memory cards / USB sticks before
trusting your valuable data to it.

Use it to soak test your new PC hardware also for the same reason.

Note that it turns out to be quite a sensitive memory tester too so
errors can sometimes be caused by bad RAM in your computer rather than
disk errors.

Install
-------

StressDisk is a Go program and comes as a single binary file.

Download the binary and run it.

Usage
-----

Use stressdisk -h to see all the options.

Quickstart
----------

Install your new media in your computer and format it (make a filesystem on it).

Open a terminal (or cmd prompt if running Windows)

To check the disk

  Linux: ./stressdisk -a /media/nameofnewdisk
  Windows: stressdisk.exe -a F:

Let run for 24 hours.  Note whether any errors were reported.  Then use

  Linux: ./stressdisk -d /media/nameofnewdisk
  Windows: stressdisk.exe -d F:

If you find errors, then you can use the -r / -R / -c and -C options
to check further.

  2012/09/20 22:23:20 Exiting after running for > 30s
  2012/09/20 22:23:20 
  Bytes read:         20778 MByte ( 692.59 MByte/s)
  Bytes written:          0 MByte (   0.00 MByte/s)
  Errors:                 0
  Elapsed time:  30.00033s

  2012/09/20 22:23:20 PASSED with no errors

Stress disk can be interrupted after it has written its check files
and it will continue from where it left off.

The default running time for stressdisk is 24h which is a sensible
minimum.  However if you want to run it for longer then use `-duration
48h` for instance.

How it works
------------

Stressdisk fills up your disk with identical large files (1 GB by
default) full of random data.  It then randomly chooses a pair of
these and reads them back checking they are the same.

This causes the disk head to seek backwards and forwards across the
disk surface very quickly which is the worst possible access pattern
for disk drives and flushes out errors.

It seems to work equally well for non-rotating media.

The access patterns are designed so that your computer won't cache the
data being read off the disk so your computer will be forced to read
it off the disk.

However if your computer memory is bigger than the size of the disk
your are testing then you'll be testing your computers RAM rather than
the disk!

History
-------

I wrote the first version of stressdisk in about 1995 after
discovering that the CD I had just written at great expense had bit
errors in it.  I discovered that my very expensive SCSI disk was
returning occasional errors.

It has been used over the years to soak test 1000s of disks, memory
cards, usb sticks and found many with errors.  It has also found quite
a few memory errors (bad RAM).

The original stressdisk was written in C with a perl wrapper but it
was rather awkward to use because of that, so I re-wrote it in Go in
2012 as an exercise in learning Go and so that I could distribute it
in an easy to run single executable format.

License
-------

This is free software under the terms of MIT license (check COPYING file
included in this package).

Contact and support
-------------------

The project website is at:

  https://github.com/ncw/stressdisk

There you can file bug reports, ask for help or contribute patches.

Authors
-------

- Nick Craig-Wood <nick@craig-wood.com>

Contributors
------------

- Your name goes here!

