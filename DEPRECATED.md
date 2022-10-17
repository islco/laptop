Deprecated: Installation Instructions for Intel
----------------------------------------------

:warning: As of Summer 2022, Apple is no longer shipping Intel-based laptops - meaning that all new Xplor hires for the foreseeable future will be shipped M1-based machines. If you are reading this page because you have a work-issued Intel laptop, stop reading this and start a conversation with your manager about procurement of our standard issue development machines for M1 architecture. For more information, see: [Onboarding Guide for Managers - Pre-Reqs](https://github.com/Mariana-Tek/.github-private/wiki/Onboarding-Guide-for-Managers#steps).

Prior Instructions for Intel + Big Sur Machines
-----------------------------------------------

### Big Sur (Intel) Addendum

Since late 2020, with the launch of Apple's Big Sur OS release, there are a number of machine-specific errors one may encounter in relation to Python dependencies that are documented widely in upstream vendor bug tickets and across Github.

As we can't predict either when or if these will be resolved, the following is a rough guide to the post-`laptop` script steps we currently (as of May 2021) recommend:

```sh
# Install Python tools
brew install pyenv
brew install pipenv

# Install Python 3.6.8
# NOTE: 
# This is where the bulk of the issues arise - if you are installing most Python versions > 3.8, you may find that a simple `pyenv install 3.8` or `pyenv install 3.9` is sufficient
# However, for versions < 3.8, additional work is needed for the OS to compile Python properly. Shown below is the command needed as of May 2021 for Python 3.6.8 (our primary Python
# version for the Mariana Django project)
CFLAGS=“-I$(brew --prefix openssl)/include -I$(brew --prefix bzip2)/include -I$(brew --prefix readline)/include -I$(xcrun --show-sdk-path)/usr/include” LDFLAGS=“-L$(brew --prefix openssl)/lib -L$(brew --prefix readline)/lib -L$(brew --prefix zlib)/lib -L$(brew --prefix bzip2)/lib” pyenv install --patch 3.6.8 < <(curl -sSL https://github.com/python/cpython/commit/8ea6353.patch\?full_index\=1)
```

