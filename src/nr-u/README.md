3GPP NR-U ns-3 module        {#nrureadme}
=====================

This is an [ns-3](https://www.nsnam.org "ns-3 Website") NR-U module for the
simulation of NR-U non-standalone cellular networks. ns-3 is used as a base network simulator,
on top of which we will add NR and NR-U modules as plugins.

## ns-3 + NR prerequisites

### ns-3 prerequisites

Make sure to install all [ns-3 preresquisites](https://www.nsnam.org/wiki/Installation#Prerequisites).

### NR prerequisites

Install libc6-dev (it provides `semaphore.h` header file):

```
sudo apt-get install libc6-dev
```

Install sqlite:

```
apt-get install sqlite sqlite3 libsqlite3-dev
```

Notice that ns-3 and nr prerequisites are required (otherwise you will get an error, e.g: `fatal error: ns3/sqlite-output.h`).

## Installation of ns-3 with nr and nr-u

Download `ns-3` and check out its release branch that is compatible with the current NR-U module, and that is `ns-3.35`:

```
git clone https://gitlab.com/nsnam/ns-3-dev.git
cd ns-3-dev
git checkout ns-3.35
```

Download the `nr` module and check out its release branch that is compatible with the current NR-U module, and that is `5g-lena-v1.2.y`:

```
cd contrib
git clone https://gitlab.com/cttc-lena/nr.git
cd nr
git checkout 5g-lena-v1.2.y
```

Download the latest `nr-u` module (`master` branch):

```
cd ..
git clone https://gitlab.com/cttc-lena/nr-u.git
```

Configure ns-3 with nr and nr-u:

```
cd ..
./waf configure --enable-examples --enable-tests
```

In the output you should see: `SQLite stats support: enabled`.

If that is not the case, return to "ns-3 and NR prerequisites" section, and install all prerequisites. After the installation of the missing packages run again `./ns3 configure --enable-tests --enable-examples`. 

Build ns-3 with nr and nr-u:

```
./waf build
```

If the NR and NR-U modules are recognized correctly, you should see `nr` and `nr-u` in the list of
built modules. If that is the case , _Welcome to the NR-U world !_

Run NR + wifi coexistence example (currently, only working example in the NR-U module, because other examples depend on an obsolete version of wigig module that is not available):

```
./waf --run cttc-nr-wifi-interference
```

## Issues

If you find any issue, please report it in 5G-LENA users group.


## Papers

An updated list of published papers that are based on the outcome 
of this module is available [here](https://cttc-lena.gitlab.io/5g-lena-website/papers/).

## Authors ##

In chronological order by contributions:

- Biljana Bojovic
- Natale Patriciello
- Sandra Lagen
- Lorenza Giupponi
- Katerina Koutlia
- Zoraze Ali
- Getachew Redieteab
- Christophe Delahaye

## License ##

This software is licensed under the terms of the GNU GPLv2, as like as ns-3.
See the LICENSE file for more details.
