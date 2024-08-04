# Atomic Red team

Install-Module -Name invoke-atomicredteam,powershell-yaml -Scope CurrentUser to just install the execution framework.

IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicredteam.ps1' -UseBasicParsing); Install-AtomicRedTeam -getAtomics to install the execution framework and atomics folder.&#x20;

IEX (IWR 'https://raw.githubusercontent.com/redcanaryco/invoke-atomicredteam/master/install-atomicsfolder.ps1' -UseBasicParsing); Install-AtomicsFolder to install the folder only.&#x20;

Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force to import the module.

Import-Module "C:\AtomicRedTeam\invoke-atomicredteam\Invoke-AtomicRedTeam.psd1" -Force $PSDefaultParameterValues = @{"Invoke-AtomicTest:PathToAtomicsFolder"="C:\AtomicRedTeam\atomics"} add the import to your powershell profile.&#x20;

## List atomic tests that can be run from the current platform (Windows,Linux,macOS)

Invoke-AtomicTest T1003 -ShowDetailsBrief

## List all atomic tests regardless of which platform it can be executed from

Invoke-AtomicTest T1003 -ShowDetailsBrief -anyOS

## List atomic tests that can be run from the current platform (Windows,Linux,macOS)

Invoke-AtomicTest All -ShowDetailsBrief

## List all atomic tests regardless of which platform it can be executed from

Invoke-AtomicTest -ShowDetailsBrief -anyOS

Invoke-AtomicTest T1218.010 -TestNumbers 1,2

## or using the short form ..

Invoke-AtomicTest T1218.010-1,2





References:

{% embed url="https://github.com/redcanaryco/atomic-red-team" %}

{% embed url="https://github.com/redcanaryco/invoke-atomicredteam" %}
