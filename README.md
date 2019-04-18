# pimpminers-conf

## Purpose

This file is used by the PiMP OS 2.x applications `pimp` and `pimpup`, and PiMP Operations.
It is written by multiple automation tools. It is not meant to be user-editable.

On PiMP Rigs, it is central to the operation of the applications and miners. It gets overwritten and updated periodically with updates.

## Structure

Example Snippet:

```
"110": [
		{
			"info": "sgminer-gm",
			"platform": "amd",
			"repotype": "git",
			"repo": "https://github.com/genesismining/sgminer-gm",
			"folder": "sgminer",
			"binary": "sgminer",
			"configure": "none",
			"menu": "(amd) sgminer-gm: multialgo [sgminer.*.conf]",
			"postexec": "none",
			"profiles": [
				{
					"id": "1",
					"name": "(amd) sgminer-gm: multialgo",
					"cfile": "sgminer.multi.conf"
				}
			],
			"MainVersion": "5.5.6-gm-17",
			"DevelVersion": "5.5.6-gm-17",
			"PageURL": "https://github.com/genesismining/sgminer-gm",
			"PageURLRegex": "",
			"SupportedAlgos": null
		}
],
```


each miner has a miner id number that corresponds with a 4-digit mining profile, starting with 3 digits. the last digit is the profile id number. In the above example, sgminer + sgminer.multi.conf profile is 1101. 


info: miner short name used as unique identifier and usually the dir name.

platform: supported hardware.  amd, nvi, cpu, asic, or mixed

repotype: (pimpup 2.x) git or binary. git means pull source and build directly on the rig. binary means download and deploy.

repo: if repotype is git, the git repo url to clone. if repotype is binary, the url of the tarball to download and deploy.

folder: dir to place the miner under /opt/miners/

binary: binary file that is the executable miner application to run

configure: if repotype is git, the configure flags to use during build. otherwise, should be set to none

menu: name of the miner as it should appear in pimp applications (pimpup, pimp --add, etc.)

postexec: if repotype is git, commands to run after make. otherwise, should be set to none

profiles: these are the mining profiles available (different conf/pcfg configuration files):

id: profile id number, 0-9

name: name of the miner profile as it should appear in pimp --add

cfile: configuration filename.

MainVersion: the version of the miner available in the main pimp3 repo.

DevelVersion: the version of the miner available in the devel (beta) pimp3 repo.

PageURL: URL of the website where releases can be downloaded.

PageURLRegex: Regex to find latest linux release of the download on the PageURL.

SupportedAlgos: array of names of algorithms that this miner supports.

