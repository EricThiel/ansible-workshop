# Step 1: Your Mission, Should you Choose to Accept it!

To complete this mission you will be completing the code samples provided by filling in missing data. The majority of the provided code samples are complete and accurate, you will simply need to fix or update sections indicated in the code by `MISSION` marks.

For example:
```yaml
######### MISSION TODO #########
# Uncomment and update this task to create 4 new Loopbacks numbered [loop_number][pod_number] such that if the loop number
# is 50 and your pod number is 40, it would be loopback5040. Variable "loops" is already defined in group_vars/iosxe.yml
#
#  - name: Create loopback from "loops"
#    ios_interface:
#      name: MISSION
#      enabled: True
#      description: Pod Number {{item}}{{pod_number}}
#    with_items: "{{loops}}"
######### END MISSION SECTION #########
```
* Look for the `# MISSION TODO` indications for the start of sections where you'll need to work.
* Within the code, replace `MISSION` with the correct value
* When you see an `# END MISSION SECTION`, this is the end of this section of work.  
* There maybe more than one `MISSION` section in a code sample
* Each `MISSION` section may have more than one elements to be updated.

### The Goal
1. Complete the tasks to create loopbacks, assign IPs to loopbacks, and to create VRFs. 
1. Apply the lessons learned and prior code examples as needed to solve the mission
1. Successfully execute the `04-mission.yaml` playbook and verify successful output in the Webex Teams room

### Your Starting Point
1. Open `hosts` in a text editor and ensure you have set values for `user_pod`, `pod_number`, `webex_token`, and `webex_room_name`
1. Open `04-mission.yaml` in a text editor
1. Search for `MISSION TODO` to find the sections to update 
1. There are **3** sections needing updates 

### Caveats and Gotchas
1. The only files that need changes are `hosts` and `04-mission.yaml`. The playbook will use variables you define in `hosts` as well as other variables from the group_vars files.
1. Only replace instances of `MISSION` within the code.  Be careful not to replace characters before or after it.  

### Need a Hint... Click to See!
<!-- Clickable Details Pane -->
<details>
<summary>Hints are here...</summary>
<pre>
Just kidding... no hints for you
</pre>
</details>

#### Next: [Verifying the Solution](2-verify.md)

