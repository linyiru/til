# Puma-dev - an alternative to Pow

## Why puma-dev

``puma-dev``[^puma-dev] is a tool to manage rack apps in development with puma.

If you need the following features, you have to use puma-dev instead of pow:

* Websockets or ActionCable in Rails 5
* Zero-config HTTPs support to your development environment.

## Installation

* Remove your pow first ``$ curl get.pow.cx/uninstall.sh | sh``
* Install via Homebrew: ``brew install puma/puma/puma-dev``
* ``sudo puma-dev -setup`` to configure DNS settings as root.
* Run ``puma-dev -install`` to configure puma-dev and run it in the background on ports both 80 and 443. This step requires root permission again to install certificates for HTTPs.

## Pro tips

* Just move or rename your old ``~/.pow`` directory to ``~/.puma-dev``
* Run ``puma-dev link`` in the rack app directory then it will generate the link automatically

[^puma-dev]: https://github.com/puma/puma-dev
