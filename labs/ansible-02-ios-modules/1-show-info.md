# Showing device information

### Hands On: 

1. Open a terminal and change to the root of the code samples repository.  
1. Change into the directory for this lab.  

    ```bash
    cd intro-ansible/
    ```

1. Within the directory is a folder called `ansible-02-ios-modules` that contain several sample playbooks. 

    ```bash
    ls ansible-02-ios-modules
    ```

    <details>
    <summary> Expected Output </summary>
    <pre>
    02-ios_command_show.yaml
    02-ios_command_show_ntp.yaml
    02-loopback_create.yaml
    02-loopback_delete.yaml
    02-ntp_create.yaml
    02-ntp_delete.yaml
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

1. Execute the following playbook to check various show outputs:

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

1. Observe in the output of the ios_facts task that we get a very specific variable value back, whereas with the ios_command tasks we get the equivalent of CLI output back. While that data could be further parsed to extract what we want, it is generally preferable to use more specific modules if they are available, and reserve general modules like ios_command and ios_config for scenarios where there is no more specific module available. 

1. Open up ansible-02-ios-modules/02-ios_command_show.yaml in a text editor and review the contents. 
 * Are you able to identify the module that is used for each task? 
    <details>
    <summary> Answer </summary>
    <pre>
    This playbook leverages ios_facts and ios_command modules.
    </pre>
    </details>
 * Can you identify how the responses for the ios_command module are captured and then displayed?
    <details>
    <summary> Answer </summary>
    <pre>
    In each task that calls ios_command, the output of the command is registered to a variable with the "register:" parameter. For example, "register: myint" stores the output of one task in the "myint" variable. 
    </pre>
    </details>
 * How is that different than how the version from ios_facts is displayed? 
    <details>
    <summary> Answer </summary>
    <pre>
    ios_facts gathers common attributes and stores them directly into variables such as "ansible_net_version". In contrast, ios_command returns the output from the command without parsing it into key/value pairs or variables. 
    </pre>
    </details>


#### Next: [Define an NTP server](2-create-ntp.md)
