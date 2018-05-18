# Create loopback with Netconf

### Hands On: 

1. Open a terminal and change to the root of the code samples repository.  
1. Change into the directory for this lab.  

    ```bash
    cd intro-ansible/
    ```

1. Within the directory is a folder called `ansible-03-netconf-config` that contain several sample playbooks. 

    ```bash
    ls ansible-03-netconf-config
    ```

    <details>
    <summary> Expected Output </summary>
    <pre>
    03-loopback_create.yaml
    03-loopback_delete.yaml
    03-ntp_create.yaml
    03-ntp_delete.yaml
    </pre>
    </details>

1. Within the directory is a file called `hosts` that contain both the device inventory, as well as a few key variables. 

    ```bash
    cat hosts
    ```

    <details>
    <summary> Expected Output </summary>
    <pre>
    [iosxe:vars]
    #user_pod: <insert_unique_string>  # Fill in a unique pod name
    # Fill in a unique pod name
    user_pod = mypod
    pod_number = 10

    [iosxe:children]
    sandbox
    #express

    [sandbox]
    ios-xe-mgmt.cisco.com ansible_port=8181

    [express]
    198.18.134.11  # dcloud pod router #1
    198.18.134.12  # dcloud pod router #2
    </pre>
    </details>


1. Edit the hosts file and fill in user_pod with a string for your pod name, and a number for your pod_number between 10 and 250

1. Save and exit the hosts file

1. Execute the following playbook to confirm the new list of Interfaces:

    ```bash
    ansible-playbook ansible-02-ios-modules/02-ios_command_show.yaml
    ```
    <details>
    <summary> Sample Output </summary>
    <pre>

    TASK [GATHERING FACTS] *******************************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [display current IOS version] *******************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com] => {
        "ansible_net_version": "16.08.01"
    }

    TASK [run show ip int brie] **************************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [display value of "myint" variable *************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com] => {
        "myint[\"stdout_lines\"]": [
                "Interface              IP-Address      OK? Method Status                Protocol",
                "GigabitEthernet1       10.10.20.48     YES NVRAM  up                    up      ",
                "GigabitEthernet2       10.255.255.1    YES other  up                    up      ",
                "GigabitEthernet3       unassigned      YES unset  up                    up      ",
                "Port-channel2          unassigned      YES unset  down                  down"
        ]
    }

    TASK [run show users] ********************************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [display value of "shuser" variable] ************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com] => {
        "shuser[\"stdout_lines\"]": [
                "Line       User       Host(s)              Idle       Location",
                "*  1 vty 0     root       idle                 00:00:00 10.24.12.232",
                "",
                "  Interface    User               Mode         Idle     Peer Address",
                "  unknown      a(ONEP)            com.cisco.sy 00:00:20 ",
                "  unknown      NETCONF(ONEP)      com.cisco.ne 00:00:20"
        ]
    }

    PLAY RECAP *******************************************************************************************************************************************
    ios-xe-mgmt.cisco.com      : ok=6    changed=0    unreachable=0    failed=0
    </pre>
    </details>

1. Observe in the output a list of current Interfaces and IPs defined on the router. Make a mental note of which loopbacks currently are defined. 


1. Execute the following playbook to add a new Loopback interface on your router:

    ```bash
    ansible-playbook ansible-03-netconf-config/03-loopback_create.yaml
    ```

    <details>
    <summary> Sample Output </summary>
    <pre>
    PLAY [NETCONF sample 1] ******************************************************************************************************************************

    TASK [set_fact] **************************************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [Create a loopback with NETCONF] ****************************************************************************************************************
    changed: [ios-xe-mgmt.cisco.com]

    PLAY RECAP *******************************************************************************************************************************************
    ios-xe-mgmt.cisco.com      : ok=2    changed=1    unreachable=0    failed=0
    </pre>
    </details>

1. Observe in the output that it shows 2 items as "ok", which means the final state is as you defined in the playbook. You will likely also see "changed=1", meaning the config did not already exist and ansible pushed it to the device. 

1. Execute the following playbook to confirm the new list of Interfaces:

    ```bash
    ansible-playbook ansible-02-ios-modules/02-ios_command_show.yaml
    ```

1. Confirm your Loopback has been added as Loopback<pod_number> with an IP of 10.111.1<pod_number>.1


1. Execute the following playbook again to add the same Loopback interface on your router:

    ```bash
    ansible-playbook ansible-03-netconf-config/03-loopback_create.yaml
    ```

1. What do you expect to happen when you run a second time? What is the term to describe what happened? Feel free to re-run the show_ntp playbook again to verify the current state on the router. 

    <details>
    <summary> Hint </summary>
    <pre>
    Because the modules in use are Idempotent, we expect the script to not make any changes. The output should look very similar to below, with 2 tasks marked ok without 0 changed. 
  
    PLAY [NETCONF sample 1] ******************************************************************************************************************************

    TASK [set_fact] **************************************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [Create a loopback with NETCONF] ****************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    PLAY RECAP *******************************************************************************************************************************************
    ios-xe-mgmt.cisco.com      : ok=2    changed=0    unreachable=0    failed=0    </pre>
    </details>


