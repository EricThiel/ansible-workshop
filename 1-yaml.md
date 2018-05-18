# Introduction to YAML

Before we dive into Ansible, we need a basic understanding of YAML. Ansible uses YAML for defining playbooks and variable files, and understanding the basics of YAML is critical to using Ansible. This lab will focus on a few key compoenents, but students are encouraged to complete [Introduction to Ansible](https://learninglabs.cisco.com/modules/sdx-ansible-intro) prior to this lab to have a more complete understanding. 

## What is YAML?
YAML stands for "YAML Ain't Markup Language", and is a data serialization standard commonly used when storing data to files within multiple programming languages. YAML is popular because it is a human readable way to store data including lists and dictionaries.

**YAML Sample data structure**


```yaml
devicename: Router1
model: ISR4451
serial: FOC27348CR9
interfaces:
  - name: GigabitEthernet1/0/1
    description: Port 1
  - name: GigabitEthernet1/0/2
    description: Port 2
  - name: Loopback1
    description: Management Loopback
location: Beverly Hills
contact: Brandon Walsh
```
In the above example you can see a data structure that describes a router and some of its common attributes. It shows the most common data types used when working with Ansible, which we will explain further below. 


### Scalars
No special characters, such as quotes, are generally required for scalar values. One exception is when a scalar contains a character that YAML interprets as syntax (such as a colon :). In those cases, enclose the entire scalar in double quotes.

```yaml
  key1: "quote string literals when using special characters like : or '"
```

### Sequences
A sequence includes scalars at the same indentation level with a single -. The YAML data following structure would become a Python list with four strings.

```yaml
  - GigabitEthernet1/0/1
  - GigabitEthernet1/0/2
  - GigabitEthernet1/0/3
  - GigabitEthernet1/0/4
```

### Mappings
Mappings are items at the same indentation level with a single colon separator, :, in each key-value pair. The following YAML data structure would become a Python dictionary with four items.

```yaml
  ntp-1: 10.10.10.1
  ntp-2: 10.10.10.2
  ntp-3: 10.10.10.3
  ntp-4: 10.10.10.4
```

### Nested Data Structures
YAML is sensitive to white space. Introducing white space within a sequence or mapping creates a nested data structure. For example, when creating a mapping of mappings, use the following syntax.

```yaml
  GigabitEthernet1/0/1:
    name: GigabitEthernet1/0/1
    state: up
    description: To Core
    type: GigabitEthernet
  GigabitEthernet1/0/2:
    name: GigabitEthernet1/0/2
    state: up
    description: User Access
    type: GigabitEthernet
  GigabitEthernet1/0/3:
    name: GigabitEthernet1/0/3
    state: down
    description: Unused
    type: GigabitEthernet
  GigabitEthernet1/0/4:
    name: GigabitEthernet1/0/4
    state: up
    description: To server1
    type: GigabitEthernet
```

#### Next: Ansible Building Blocks


