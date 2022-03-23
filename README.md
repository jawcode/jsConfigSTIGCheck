# jsConfigSTIGCheck
Config File STIG Checking using HTML and JS

This is a self-contained HTML file that has the following embedded JS libraries:
  - JSZip 3.5.0 : https://github.com/Stuk/jszip
  - jQuery 3.4.1 : https://jquery.com/
  - JSON Form : https://github.com/jsonform/jsonform
  - Moment JS : https://momentjs.com/
  - Underscore 1.9.1 : https://underscorejs.org/
  - FileSaver 2.04 : https://github.com/eligrey/FileSaver.js/

# Usage
Open the file in a fairly-modern JavaScript-enabled web browser. Load a JSON version of a STIG checklist, or convert a STIG CKL file to JSON. Load a configuration file that should be checked against the STIG checklist. Save the results as a valid CKL file for further adjustments in a STIG viewer program. If needed, edit the automated checks for each STIG rule and save a new JSON file with those changes.

An example configuration and JSON checklist are included.

# Automated Check Notation
The SCAP Match String uses some basic text matching with REGEX capabilities to operate.

Plain text without '#' symbols will be matched verbatim or by using REGEX and are useful for single-line configuration items. A '!' symbol will result in a finding if the item is found in a configuration.

A '#' symbol is used to find repeated configuration items or groups of configurations. The first # indicates the line to search for, and the '##' indicates the configuration item that must exist or a number-limit value.

When using a '#' symbol, a letter f or c is used to control matching type or number requirements. An '#f' will show a success if each found group has a matching configuration item such as 3 of 3 items.

If using a '#' symbol with a c, such as '#c', this will show a success only if the amount of matches equal the allowed number as defined by the SCAP check text.

Example 1: To search for 'service timestamps log datetime localtime', the SCAP text would be 'service timestamps log datetime localtime' (without single quotes).

Example 2: To check if every applicable interface has 'switchport access vlan 1000', the SCAP text would be '#finterface Gig.*/0/##switchport access vlan 1000'.

Example 3: To ensure that only one local user exists, the SCAP text would be '#c#cusername.*##1' (for two users, the ##1 would be changed to ##2).

# Licensing
This script is Public Domain
