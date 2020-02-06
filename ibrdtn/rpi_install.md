# Compile and install IBR-DTN on Raspberry pi 3

- ##### update & upgrade the rpi
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
- ##### Install required packages

```
$ sudo apt-get install build-essential libssl-dev libz-dev libsqlite3-dev \
                            libcurl4-gnutls-dev libdaemon-dev automake autoconf pkg-config libtool libcppunit-dev \
                            libnl-3-dev libnl-cli-3-dev libnl-genl-3-dev libnl-nf-3-dev libnl-route-3-dev libarchive-dev \
                            libarchive-dev
```
- ##### Install git & clone repo
```
$ sudo apt-get install git
$ git clone https://github.com/destmaxi/ibrdtn ibrdtn-repo
```
- ##### Compile and install IBR-DTN
```
$ cd ibrdtn-repo/ibrdtn
$ bash autogen.sh
$ ./configure --without-vmime
$ make
$ sudo make install
```

- ##### Test ibrdtn daemon
```
$ dtnd -i wlan0
$ dtnping dtn://$hostname/echo
```

## Troubleshooting
In case some libraries could not be found (ex: ibrdtn/ibrdtn/.libs/libibrdtn.so.1) just
copy them to **/usr/lib**

```
$ sudo cp ibrdtn-repo/[path_to_missing_lib]/.libs/[missing_lib].so.1 /usr/lib
```