---
modified: 2022-09-04T16:27:35.571Z
---

# Playbook

In order to use them:

`ansible-playbook -i allhosts setup.yml`

It will install and configure 'monit' for monitoring your hosts as well as alerts via Telegram using 'noti' and email

Example inventory:

```yaml
all:
  vars:
    ansible_connection: ssh
    ansible_ssh_user: root
    autostake: False
    claimsend: False
    backend: "file"

    envvar: ""
    identity: "KEYBASEID"
    monitpath: "/etc/monit/conf.d/"
    notifications: "YOUREMAIL"
    systemdfile: false
    telegramchatid: "FILLME"
    telegramtoken: "Contact @botfather to get it"
    website: "$YOURNODEWEBSITE"
    node: False
    os: "debian"
    gmail: "EMAIL:$PASSFORAPPS"
    prefix: ""  # prefix for all created commands and files that are relevant to networks to allow more than one network per host configurations
    cosmospath: "/root/.chainfolder/"
    diskusagewarning: "80%"
    workingdir: /root/folder to enter to run
    customcommand: customcommand to run in workingdir
    passphrase: "eateggs"
    createcommands: True
    validator: False
    serviceport: 26656
    rpcport: 26657
    grpcport: 9090
    grpcwebport: 9091
    rpcbind: "tcp://127.0.0.1"
    monit: True
    extrabin: ""
    extratxbin: "" # parameters to append when interacting with transactions (f.e. -b block)
    monitorothers: True
    envvar: []  # Environment variables to define in /root/.cosmos.env file
    gas: "" # Set to values to use in case minfee is set to False

    multiplier: 1 # set to higher values to define more readable safety and minclaim values
    monitorwallet: [] # Wallets to monitor for balance under safety

  children:
    nym:
      hosts: myFancyHostname.com
      vars:
        address: "wallet address"
        backend: False
        chaincommand: "/root/.nymd/nymd" # Command to run the cosmos chain
        chainid: "testnet-milhon"
        details: "High in the sky, setting the path to follow!" # Your validator 'signature to create the validator account and edit
        envvar: "LD_LIBRARY_PATH=/root/.nymd/" # Extra environment varas
        extrabin: ""
        node: "tcp://testnet-milhon-validator1.nymtech.net:26657" # Node to use
        from: "mywallet" # Your wallet name
        minfee: 5000
        monitpath: "/etc/monit.d/" # Path for monit, depends on OS, default in above section is for Debian, this one for Fedora
        operaddress: "YOUR OPERADDRESS"
        safety: "200000"
        token: "upunk"
        systemdfile: true
        os: "fedora" # Default is ubuntu, change for others
        commissionrate: "0.1"
        commissionmaxrate: "1"
        commissionmaxchange: "0.01"
        minselfdelegation: "1"
```
