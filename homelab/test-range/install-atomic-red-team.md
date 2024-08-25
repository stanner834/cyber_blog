# Install Atomic Red team

The Atomic Red Team framework is a powerful, open-source toolset for simulating cyberattacks to test and improve security defenses. It provides predefined atomic tests that mimic real-world attack techniques, allowing security teams to evaluate their detection and response capabilities effectively. With simple installation and easy-to-run tests, it is a great tool to run locally and on your home network.

## Install the execution framework

`Install-Module -Name invoke-atomicredteam, powershell-yaml -Scope CurrentUser`&#x20;

## Install the execution framework and atomics folder

`IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics`

## Import the module

`IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicsfolder.ps1' -UseBasicParsing); Install-AtomicsFolder to install the folder only. Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force`&#x20;

## Commands

List atomic tests that can be run from the current platform (Windows, Linux, macOS):

`Invoke-AtomicTest T1003 -ShowDetailsBrief`&#x20;

List all atomic tests regardless of which platform it can be executed from:

&#x20;`Invoke-AtomicTest T1003 -ShowDetailsBrief -anyOS`&#x20;

List atomic tests that can be run from the current platform (Windows, Linux, macOS):&#x20;

`Invoke-AtomicTest All -ShowDetailsBrief`&#x20;

List all atomic tests regardless of which platform it can be executed from:

&#x20;`Invoke-AtomicTest -ShowDetailsBrief -anyOS Invoke-AtomicTest T1218.010 -TestNumbers 1,2`&#x20;

Run an atomic red team test

`Invoke-AtomicTest T1016`&#x20;

Cleanup an atomic red team test

`Invoke-AtomicTest T1016 -cleanup`

Log and run an atomic red team test to the current directory in json format

`Invoke-AtomicTest T1016 -LoggingModule "Attire-ExecutionLogger" -ExecutionLogPath T1016-Windows.json`

## References:

{% embed url="https://github.com/redcanaryco/atomic-red-team" %}

{% embed url="https://github.com/redcanaryco/invoke-atomicredteam" %}
