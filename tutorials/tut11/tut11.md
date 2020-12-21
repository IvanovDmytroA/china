---
title: Awesome tutorial
description: Handle the message execution in case of errors.
auto_validation: true
time: 15
tags: [ tutorial>intermediate, products>sap-cloud-platform]
primary_tag: products>sap-cloud-platform-integration-for-process-services
---
## Details
### You will learn
  - How to induce an artificial error or exception in your message pipeline
  - How to handle exceptions through _Exception Sub-process_
  - How to use different end events to manage errors
  - What is a send step
In this exercise, we will induce an artificial exception situation via a script.
An _Exception Sub-process_ will be added to handle the artificial exception.
We will also play with the different End Events to see how they differ.
---
[ACCORDION-BEGIN [Step 1: ](Switch to Escalation End Event)]
In this exercise, we shall change the __Error End Event__ to __Escalation End Event__ and understand how the processing differs. As we shall see, the processing is unchanged - the __Escalation End Event__ gives us a way to set the message execution status to a different value: __Escalated__.
1. Delete the __Error End Event__ step in the __Exception Sub-process__ and replace it with an __Escalation End Event__ step:
    * Hover over the __Error End Event__ step and click on the __Delete__ speed button:
      ![Delete End](Delete End 2.png)
    * Click on the design palette.
    * Choose __Events__.
    * Choose __Escalation End Event__.
        ![Choose Error End Event](Choose Escalation End Event.png)
    * Drag it within the __Exception Sub-process__ and connect it to the __Send__ step.
        ![Add Error End Event](Add Escalation End Event.png)
        ![Add Error End Event](Add Escalation End Event 2.png)
2. Save, deploy and execute the integration flow.
     * Go to the __Monitoring view__ and look for an entry for the message just processed.  The status of the message should be __Escalated__ - this message status indicates that the exception was raised, caught by the Exception Sub-process and finally set by the __Escalation End Event__.   
        ![Error View With Error End Event](Escalation message status.png)    
        The __Error Details__ section gives more information about the exception.
    * To get additional information about the exception, scroll down to the __logs__ section (or click on the __Logs__ tab) and click on __Info__.
    ![Error Details](Escalation details.png)
    A graphical viewer opens up and provides a visual representation of the exception location on the message execution pipeline. The graphical viewer shows that the exception thrown by the __Script__ step was caught in the __Exception Sub-process__. A mail was send and the message execution status was set to __Escalated__.
3. The mail received is also exactly the same as with the __Error End Event__:
    Check your configured inbox. You should get the following email:
    ![Error email](Error email.png)   
[VALIDATE_1]
[ACCORDION-END]
---