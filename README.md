Simply Random
=============
[![Latest Stable Version](https://badge.fury.io/ph/blocktrail%2Fsimply-random.svg)](https://packagist.org/packages/blocktrail/simply-random)
[![Build Status](https://travis-ci.org/blocktrail/simply-random-php.svg?branch=master)](https://travis-ci.org/blocktrail/simply-random-php)

tested on **PHP 5.4**, **5.5**, **5.6** and **HHVM**

## What is this library?
This is a simple library for random number generation using MCRYPT_DEV_URANDOM.  
This library can generate strong, cryptographically secure random numbers.


## Dependencies
This library depends on `ext-mcrypt` as it uses `mcrypt_create_iv($length, \MCRYPT_DEV_URANDOM)` to get random data from `/dev/urandom`.


## Installation
Simply use `composer require blocktrail/simply-random ~1.0`.


## Usage
Please refer to `test.php` for example usage.


## Credits to ircmaxell
Most of the code used in this library was originally written by [ircmaxell](https://github.com/ircmaxell) 
for [random_compat](https://github.com/ircmaxell/random_compat).

I stripped out some complexity from his library, since I'm okay with having a strong dependancy on the mcrypt extension, while his code is written to be able to function without the presence of mcrypt too.  
When using `MCRYPT_DEV_URANDOM` (which is a simple wrapper around `/dev/urandom`) it shouldn't be neccesary to do mixing.


## Why MCRYPT_DEV_URANDOM?
Using MCRYPT_DEV_URANDOM (or using `/dev/urandom` directly) is the right way to generate randomness, there's no better way of doing this.  
The OpenSSL extension has `openssl_random_pseudo_bytes` which also uses `/dev/urandom` but it has had issues in the past and when generating randomness it's generally that "every bit of additional code is something to fail".

see:
http://timoh6.github.io/2013/11/05/Secure-random-numbers-for-PHP-developers.html

and more:
https://news.ycombinator.com/item?id=6216101
http://security.stackexchange.com/questions/3936/is-a-rand-from-dev-urandom-secure-for-a-login-key/3939#3939

