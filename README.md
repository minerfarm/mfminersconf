# mf-miners-conf

## Purpose

This file is used by the MFOS OS 3.x applications including `confgen` and `benchtest`, Miner.farm DevOps (minerbuilder, jenkins)
It is written by multiple automation tools. It is not meant to be user-editable.

On MFOS Rigs, it is central to the operation of the applications and miners. It gets overwritten and updated periodically with updates.

## Structure

Example Snippet:

```
"120": [
		{
			"info": "teamredminer",
			"platform": "amd",
			"repotype": "binary",
			"repo": "https://update.getpimp.org/pimpup/miners/pimpm-teamredminer-0.7.21-2.24.tgz",
			"folder": "teamredminer",
			"binary": "teamredminer",
			"configure": "none",
			"menu": "(amd) teamredminer: cryptonights/phi2/lyra2z [teamredminer.pcfg]",
			"postexec": "none",
			"profiles": [
				{
					"id": "1",
					"name": "(amd) teamredminer: cryptonights/phi2/lyra2z",
					"cfile": "teamredminer.pcfg",
					"Config": [
						{
							"FLAGS": "--log_file=/var/log/teamredminer.log",
							"CONF": "p1:o,u1:u,l1:p,a1:a",
							"API": "-api_listen=127.0.0.1:",
							"POOL_TITLE": "Ethash",
							"TYPE": "GPU",
							"EXTRA": "",
							"NOTES": "",
							"TEMPLATE": "pimp1.tmpl"
						}
					]
				}
			],
			"MainVersion": "0.3.8",
			"DevelVersion": "0.5.5",
			"PageURL": "https://github.com/todxx/teamredminer/releases",
			"PageURLRegex": "(/\\S*\\-linux\\.tgz)",
			"SupportedAlgos": [
				{
					"cn_conceal": "CryptoNightConceal",
					"cn_haven": "CryptoNightHaven",
					"cn_heavy": "CryptoNightHeavy",
					"cn_saber": "CryptoNightSaber",
					"cnr": "CryptoNightR",
					"cnv8": "CryptoNightV8",
					"cnv8_dbl": "",
					"cnv8_half": "",
					"cnv8_rwz": "CNReverseWaltz",
					"cnv8_trtl": "CryptoNightTurtle",
					"cnv8_upx2": "CryptoNightUPX2",
					"cuckarood29_grin": "cuckARood29",
					"cuckatoo31_grin": "cuckAToo31",
					"ethash": "Ethash",
					"kawpow": "KAWPOW",
					"lyra2rev3": "",
					"lyra2z": "",
					"mtp": "",
					"phi2": "PHI2",
					"trtl_ckukwa": "",
					"x16r": "",
					"x16rt": "",
					"x16rv2": "",
					"x16s": ""
				}
			],
			"BtcTalk": "https://bitcointalk.org/index.php?topic=5059817.0"
		}
	],
```


each miner has a miner id number that corresponds with a 4-digit mining profile, starting with 3 digits. the last digit is the profile id number. In the above example, sgminer + sgminer.multi.conf profile is 1101. 


info: miner short name used as unique identifier and usually the dir name.

platform: supported hardware.  amd, nvi, cpu, asic, or mixed

repotype: git (legacy/deprecated) or binary. git means pull source and build directly on the rig. binary means download and deploy.

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

Config: this contains fields that are used by confgen tool to generate new pimp pcfg files from templates.

MainVersion: the version of the miner available in the main pimp3 repo.

DevelVersion: the version of the miner available in the devel (beta) pimp3 repo.

PageURL: URL of the website where releases can be downloaded.

PageURLRegex: Regex to find latest linux release of the download on the PageURL.

SupportedAlgos: array of names of algorithms that this miner supports.

BtcTalk: URL of official BTCtalk forum thread for the miner, if available.

