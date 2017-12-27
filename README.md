erGW - 3GPP GGSN and PDN-GW in Erlang
=====================================
[![Build Status][travis badge]][travis]
[![Coverage Status][coveralls badge]][coveralls]
[![Erlang Versions][erlang version badge]][travis]

# ***1. INSTALLATION***
--------------------
## 1. ERLANG:

Download an Erlang source file with an appropriate version and unwrap it:
```
tar -zxf otp_src_20.1.tar.gz						
cd otp_src_20.1
```
Export the working directory
```
export ERL_TOP=`pwd`					      
```
And run configure scripts:
```
sudo ./configure
```						         
If you notice a [crash](http://erlang.org/doc/installation_guide/INSTALL.html) with certain locales try:
```
export LANG=C
```							          

Build Erlang:
```
sudo make
```								                

Optionally build and run tests:
```
make release_tests							    
cd release/tests/test_server						
$ERL_TOP/bin/erl -s ts install -s ts smoke_test batch -s init stop
```
Check if none fail at $ERL_TOP/release/tests/test_server/index.html.

Proceed to install Erlang:
```
cd $ERL_TOP
sudo make install
```			            

Export to $PATH, this is important. Full OTP is needed in PATH environment for Rebar!
```
export PATH=$ERL_TOP/bin:$PATH
```			

--------------------
## 2. REBAR3:

Clone from git:
```
git clone https://github.com/erlang/rebar3			
cd rebar3/
export REBAR3_TOP=`pwd`
export PATH=$REBAR3_TOP:$PATH
```

And install:
```
./bootstrap			
```

Running the rebar3 command the correct rebar and Erlang version should show up!
```
rebar3 version
```							

## 3. ERGW:

Clone from git:
```
git clone https://github.com/travelping/ergw		
cd ergw
```

Compile using rebar3:
```
rebar3 compile
```  							                                             						

# ***2.		Operation:***

Modify the configuration of the erGW at `ergw/ergw.config` and start it (from root):

```
cd ergw/
sudo erl -setcookie secret -sname ergw -config ergw.config
```		

A default ergw.config can be found [here](https://github.com/travelping/ergw.).
Try `regs()` or `i(X,Y,Z)` with a pid in the shell to check if the processes are running properly.

<!-- Badges -->
[travis]: https://travis-ci.org/travelping/ergw
[travis badge]: https://img.shields.io/travis/travelping/ergw/master.svg?style=flat-square
[coveralls]: https://coveralls.io/github/travelping/ergw
[coveralls badge]: https://img.shields.io/coveralls/travelping/ergw/master.svg?style=flat-square
[erlang version badge]: https://img.shields.io/badge/erlang-R19.1%20to%2020.0-blue.svg?style=flat-square
