# Define an NTP server

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

1. Execute the following playbook to confirm the list of NTP servers:

    ```bash
    ansible-playbook ansible-02-ios-modules/02-ios_command_show_ntp.yaml
    ```
    <details>
    <summary> Sample Output </summary>
    <pre>
    PLAY [Sample IOS show ntp for Ansible 2.5] *******************************************************************************************************

    TASK [run show ntp associations] *********************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com]

    TASK [display value of "myint" variable] *************************************************************************************************************
    ok: [ios-xe-mgmt.cisco.com] => {
        "myntp[\"stdout_lines\"][0]": [
            "address         ref clock       st   when   poll reach  delay  offset   disp",
            " ~10.34.45.56     .INIT.          16      -   1024     0  0.000   0.000 15937.",
            " ~1.1.1.2         .INIT.          16      -   1024     0  0.000   0.000 15937.",
            " * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured"
        ]
    }

    PLAY RECAP *******************************************************************************************************************************************
    ios-xe-mgmt.cisco.com      : ok=2    changed=0    unreachable=0    failed=0
    </pre>
    </details>

1. Observe in the output a list of current NTP servers defined on the router. Make a mental note of which servers currently are defined. 

1. Execute the following playbook to add a new NTP server on your router:

    ```bash
    ansible-playbook ansible-02-ios-modules/02-ntp_create.yaml
    ```

    <details>
    <summary> Sample Output </summary>
    <pre>
    PLAY [Sample IOS NTP config for Ansible 2.5] *********************************************************************************************************

    TASK [set ntp server 10.111.10.65 via CLI] ***********************************************************************************************************
    changed: [ios-xe-mgmt.cisco.com]

    PLAY RECAP *******************************************************************************************************************************************
    ios-xe-mgmt.cisco.com      : ok=1    changed=1    unreachable=0    failed=0

    </pre>
    </details>

1. Execute the following playbook to confirm the new list of NTP servers:

    ```bash
    ansible-playbook ansible-02-ios-modules/02-ios_command_show_ntp.yaml
    ```

1. Confirm your NTP server has been added as 10.111.<pod_number>.65

1. Open up ansible-02-ios-modules/02-ntp_create.yaml in a text editor and review the contents. 
 * Can you identify which module was used to configure NTP on the server? 
    <details>
    <summary> Answer </summary>
    <pre>
    This lab used the ios_config module to execute specific config commands directly onto the device
    </pre>
    </details>
 * If you wanted to use that module to make configuration changes, where would you go for information about mandatory and optional parameters, as well as examples of usage? 
    <details>
    <summary> Answer </summary>
    <pre>
    1. https://docs.ansible.com/ansible/2.5/modules/ios_config_module.html#ios-config-module
    2. execute "ansible-doc ios_config" on your ansible workstation
    </pre>
    </details>



#### Next: [Creating a loopback](3-create-loopback.md)
