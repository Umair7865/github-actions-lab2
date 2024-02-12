# lab2
installing python through workflow using matrix strategy

# KodeKloud python-installation.yml

name: Installing Python
'on':
- push
jobs:
build:
runs-on: '${{ matrix.os }}'
strategy:
  matrix:
    os:
      - ubuntu-latest
      - macos-latest
      - windows-latest
    py-version:
      - 3.7
      - 3.8
      - 3.9
    exclude: #added
      - os: macos-latest #added
        py-version: 3.9 #added
steps:
  - name: Set up Python
    uses: actions/setup-python@v4
    with:
      python-version: '${{ matrix.py-version }}'
