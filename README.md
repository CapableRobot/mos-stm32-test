# mos-stm32-test

Testing Mongoose OS on STM32.  This repository was created to report build issues to Mongoose OS.

Steps to reproduce:

* Clone repository
* `mos build --local`
* This will fail, complaining about the mongoose dependency not having any source nor a library file.  The mongoose dependency for mongoose-os specifies that there is source, but there is none in the shim repo.  See [https://github.com/cesanta/mongoose-os/issues/442]().
* Add the missing source file via:
	`cd deps/mongoose && mkdir src && cd src`
	`wget https://raw.githubusercontent.com/cesanta/mongoose/master/mongoose.c`
	`cd ../../../`
* Build again (`mos build --local`).  This time the repo will fail, with errors reported in [https://github.com/cesanta/mongoose-os/issues/443]()