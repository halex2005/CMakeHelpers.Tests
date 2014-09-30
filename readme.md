CMakeHelpers.Tests
==================

CMakeHelpers.Tests uses CMakeHelpers repository as submodule and
contains some tests and specific scenarios for CMakeHelpers.
This tests can be used as examples of usage CMakeHelpers scripts.

Usage
-----

After clone of repository, you need initialize submodules:

```
git submodule init
git submodule update
```

Then you need to create some temp folder for cmake builds:

```
mkdir tmp
cd tmp
```

To start testing you should run cmake:

```
cmake ..
```

If cmake have no error output, tests are completed.

You can get errors if you have no installed specific libraries which script will search for:

- [PJSIP](http://www.pjsip.org/)
- [Resiprocate](http://resiprocate.org)

Licensing
---------

CMakeHelpers is distributed under [Apache v2.0 License](LICENSE).

[![PayPal donate button](http://img.shields.io/paypal/donate.png?color=yellow)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=7RR8B7SRHFX5Q "Donate once-off to this project using Paypal")
[![Gittip donate button](http://img.shields.io/gratipay/halex2005.svg)](https://gratipay.com/halex2005/ "Donate weekly to this project using Gratipay")