# Ubuntu-Issues

- 1. dd if/of is too slow

In the future, you should use pv to get a running progress bar.

sudo apt-get install pv

With pv installed, let's assume you want to clone a 20GB drive, /dev/foo, to another drive (20GB or larger!), /dev/baz:

sudo dd if=/dev/foo bs=4M | pv -s 20G | sudo dd of=/dev/baz bs=4M

Important bits to notice: the bs=4M argument sets the blocksize for dd operations to 4MB, which drastically improves the speed of the whole thing. And the -s 20G argument tells pv how big this operation is expected to be, so it can give you an ETA as well as a current speed.

I love pv so hard it should probably be illegal.
