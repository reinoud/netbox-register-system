# netbox-register-system
This is a small python script, that I use for registering virtual machines to netbox. 
It creates the virtual machine, its interfaces and ip addresses.

**You may need to adjust some parameters in order to be able to use it**

## Technial notes
1. Tested on CentOS7 and RHEL7
2. Tested with ```python 2.7```

### Dependencies
- [pynetbox](https://github.com/digitalocean/pynetbox)
- [psutil](https://pypi.org/project/psutil/)
- [terminaltables](https://pypi.org/project/terminaltables/)

## Getting Started
1. Clone this repository
2. Install the dependencies (pip or via rpm)
3. Adjust `HOST` and `TOKEN` in `netbox-register-system.py`

## Usage
Following options are implemented:
- register: Registers the system with at netbox.
- compare: Compares the system parameter with its registration onnetbox
- delete: Deletes the system from netbox.
- update: Updates the system parameter on netbox

## Examples
### register system
```
$ sudo netbox -r
[register system]
Created "pilot-2.dev.int".
Created interface "eth4".
Created IP address "172.X.X.X" for NIC "eth4".
Interface "eth3" is not configured. Skipping.
Interface "eth2" is not configured. Skipping.
Interface "eth1" is not configured. Skipping.
Created interface "eth0".
Created IP address "10.X.X.X" for NIC "eth0".
Successfully registiered "pilot-2.dev.int".

```
### delete system
```
$ sudo netbox -d 
[deleting system]
Deleted "pilot-2.dev.int" from netbox.
```
### comparing system with its netbox config
```
$ sudo netbox -c
[comparing system]

+--------------+----------------------+----------------------+-------+
| Parameter    | System               | Netbox               | Match |
+--------------+----------------------+----------------------+-------+
| vCPUs        | 2                    | 2                    | True  |
| Disk         | 30.0                 | 30                   | True  |
| Memory       | 10240.0              | 10240                | True  |
| IP (eth4)    | XXXX                 | XXXXX                | True  |
| DNS (eth4)   | XXXXX                | XXXXXX               | True  |
| MAC (eth4)   | 00:1A:4A:00:0A:12    | 00:1A:4A:00:0A:12    | True  |
| IP (eth0)    | XXXXXX               | XXXXX                | True  |
| DNS (eth0)   | XXXXX                | XXXXXX               | True  |
| MAC (eth0)   | 00:1A:4A:00:08:09    | 00:1A:4A:00:08:09    | True  |
+--------------+----------------------+----------------------+-------+

No Differences occured.
Exiting.

```

### update system
```
$ sudo netbox -u
[deleting system]
Deleted "pilot-2.dev.int" from netbox.

[register system]
Created "pilot-2.dev.hss.int".
Created interface "eth4".
Created IP address "172.X.X.X" for NIC "eth4".
Interface "eth3" is not configured. Skipping.
Interface "eth2" is not configured. Skipping.
Interface "eth1" is not configured. Skipping.
Created interface "eth0".
Created IP address "10.X.X.X" for NIC "eth0".
Successfully registiered "pilot-2.dev.int".

```
