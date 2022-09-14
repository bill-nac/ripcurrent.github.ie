# Powershell Tips
Hints & tips on using Powershell

## General
use the ` character to span across lines
remember boolean is $true/$false and not 'true'/'false' !
arrays @()
objects [type]@{}

Get-Module
Get-Command -module "ModuleName" *searchstring*

simple loop\
`
foreach ($id in Get-CGIPUserPoolList -Select 'UserPools.Id')
{ 
    Write-Output ('Deleting existing pool ' + $id)
    Remove-CGIPUserPool -UserPoolId $id -Force
} 
`
## Startup location
create file profile.ps1 in **Documents\WindowsPowershell**. \
Add the line: \
`
Set-Locations C:\
`

## AWS scripting
Install-Module -name AWS.Tools.CognitoIdentityProvider

Get-AWSCredential -ListProfileDetail
Get-DefaultAWSRegion
Set-AWSCredential -AccessKey [accessKey] -SecretKey [secretKey] default
Set-DefaultAWSRegion us-east-1

## Azure scripting
Install-Module -name Az


## IIS recipes
Excellent backgrounder here:
https://octopus.com/blog/iis-powershell
