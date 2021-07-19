***
**libftdi1isc version 1.5**
***

libftdi1isc has been modified from libftdi by ITDLab.

libftdi1isc - A library (using libusb) to talk to FTDI's UART/FIFO chips
including the popular bitbang mode.

libftdi1isc requires libusb 1.x.

# Changes
## 2021.7.20
 - We have removed some projects from original version of libftdi.  
    - This source contains only libftdi1isc  
	- Removed projects  
	 - examples  
	 - ftdi_eeprom  
	 - ftdipp  
	 - python  
 - Its name has changed from libftdi1 to libftdi1isc.  
 - It has been modified so that writes in transit do not interrupt reception.  
    - file:ftdi_stream.c  
     - function:ftdi_readstream()  
     - modified:add if(activityCount > 10) for  
	 - removed:Calculation of progress  

# Quick start

mkdir build
cd build

cmake -DCMAKE_INSTALL_PREFIX="/usr" ../  
make  
(Copy File src/libftdi1isc.so.2.5.0 to your desired location)  
(Make link sudo ln -s .../libftdi1isc.so.2.5.0 .../libftdi1isc.so.2)  

# Information

We modified the following libftdi to create libftdiiac

You'll find the original version of libftdi at:
https://www.intra2net.com/en/developer/libftdi

--------------------------------------------------------------------
ITD Lab Corp.
--------------------------------------------------------------------


Below is the original libftdi statement on which it was based.
***

--------------------------------------------------------------------
libftdi version 1.5
--------------------------------------------------------------------

libftdi - A library (using libusb) to talk to FTDI's UART/FIFO chips
including the popular bitbang mode.

The following chips are supported:
* FT230X
- FT4232H / FT2232H
- FT232R  / FT245R
- FT2232L / FT2232D / FT2232C
- FT232BM / FT245BM (and the BL/BQ variants)
- FT8U232AM / FT8U245AM

libftdi requires libusb 1.x.

The AUTHORS file contains a list of all the people
that made libftdi possible what it is today.

Changes
-------
* Implement tc[io]flush methods & deprecate broken purge_buffers methods

  Please check your code for ftdi_usb_purge_rx_buffer(),
  ftdi_usb_purge_tx_buffer() and ftdi_usb_purge_buffers()
  and migrate to the new ftdi_tc[io]flush() methods.

  Old code will continue to function, but you'll get
  a deprecation warning during compilation.

* Add program to test buffer flush (purge) functionality
* Add kernel driver auto attach/detach.
  See new AUTO_DETACH_REATACH_SIO_MODULE option
* Add ftdi_setflowctrl_xonxoff()
* ftdi_eeprom / eeprom handling:
  * Unify handling of all boolean eeprom flags
  * Add device release number support
  * Add channel_a_driver support for type xxR chips
  * Add support for group0 drive levels on x232H chips
  * Fix handling of high_current_drive parameter
  * Fix inverted handling of VCP driver field for TYPE_R chips
  * New --verbose option for eeprom decode operation
* Add example code for async mode
* Add SPDX license identifiers to the core library & ftdi_eeprom
* Various python SWIG wrapper improvements
* Various cmake file improvements
* Fix small bugs in error code paths

You'll find the newest version of libftdi at:
https://www.intra2net.com/en/developer/libftdi


Quick start
-----------
mkdir build
cd build

cmake -DCMAKE_INSTALL_PREFIX="/usr" ../
make
make install

More verbose build instructions are in "README.build"

--------------------------------------------------------------------
www.intra2net.com                             2003-2020 Intra2net AG
--------------------------------------------------------------------
