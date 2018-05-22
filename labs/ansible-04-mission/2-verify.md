## Step 2: Verifying the Solution

Think you've got the mission complete?  Let's find out.  

### Running Your Code

1. Open a terminal and navigate to the root of the code repository.  
1. Change into the Mission directory.  

    ```bash
    cd intro-ansible
    ```

1. Run the mission file.  

    ```bash
    ansible-playbook ansible-04-mission/04-mission.yaml
    ```
### What to Expect

If you successfully completed the mission, the script should complete without errors and show output like this.  
```bash

PLAY [Intro to Ansible Mission] **********************************************************************************************************************

TASK [GATHERING FACTS] *******************************************************************************************************************************
ok: [173.37.56.91]

TASK [display current IOS version] *******************************************************************************************************************
ok: [173.37.56.91] => {
    "ansible_net_version": "16.08.01a"
}

TASK [run show vrf] **********************************************************************************************************************************
ok: [173.37.56.91]

TASK [display value of "myvrf1" variable] ************************************************************************************************************
ok: [173.37.56.91] => {
    "myvrf1[\"stdout_lines\"][0]": [
        ""
    ]
}

TASK [Mission incomplete] ****************************************************************************************************************************

TASK [Mission incomplete] ****************************************************************************************************************************
ok: [173.37.56.91] => {
    "msg": "Please review 04-mission.yaml and add a task to create the required Loopbacks with unique numbers and IPs"
}

TASK [Create loopback from "loops"] ******************************************************************************************************************
changed: [173.37.56.91] => (item=11)
changed: [173.37.56.91] => (item=12)
changed: [173.37.56.91] => (item=13)
changed: [173.37.56.91] => (item=14)

TASK [Create and assign IP to loopback] **************************************************************************************************************
changed: [173.37.56.91] => (item=11)
changed: [173.37.56.91] => (item=12)
changed: [173.37.56.91] => (item=13)
changed: [173.37.56.91] => (item=14)

TASK [Mission incomplete] ****************************************************************************************************************************
ok: [173.37.56.91] => {
    "msg": "Please review 04-mission.yaml and add a task to create the required VRFs"
}

TASK [Create VRFs as defined by local_vrfs] **********************************************************************************************************
changed: [173.37.56.91]

TASK [run show vrf] **********************************************************************************************************************************
ok: [173.37.56.91]

TASK [display value of "myvrf2" variable] ************************************************************************************************************
ok: [173.37.56.91] => {
    "myvrf2['stdout_lines'][0]": [
        "Name                             Default RD            Protocols   Interfaces",
        "  blue                             1:410                 ipv4,ipv6   Lo1210",
        "  green                            1:420                 ipv4,ipv6   Lo1310",
        "  mypod                            1:10                  ipv4,ipv6   Lo1410",
        "  red                              1:400                 ipv4,ipv6   Lo1110"
    ]
}

TASK [Get Webex Teams room list] *********************************************************************************************************************
ok: [173.37.56.91]

TASK [Retrieve the Webex Teams room UUID from the room name] *****************************************************************************************
ok: [173.37.56.91] => (item={'created': '2018-05-10T17:55:44.020Z', 'title': 'myroom2', 'isLocked': False, 'lastActivity': '2018-05-18T23:31:51.974Z', 'creatorId': 'sadfiuk6asdfi7sdyf6y7idsf6sdif76sdoify6sdoicuhkewjus', 'type': 'group', 'id': 'cnkajgh4kwjfgaw7tdgkajhb3kdgwaghubjkhwetdiuywagk2u'})

TASK [Send info to Webex Teams room] *****************************************************************************************************************
ok: [173.37.56.91]

PLAY RECAP *******************************************************************************************************************************************
173.37.56.91               : ok=14   changed=3    unreachable=0    failed=0

```

A message will also be posted to the Spark Room.  

#### Next: Summary

