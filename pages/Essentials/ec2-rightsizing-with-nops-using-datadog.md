---
title: EC2 Rightsizing with nOps with DataDog integration
keywords: savings, recommendations, datadog, essentials, rightsizing
tags: [essentials]
sidebar: mydoc_sidebar
permalink: ec2-rightsizing-with-nops-using-datadog.html
folder: Essentials
series: [Essentials, Rightsizing]
weight: 2.0
---

## Instructions


1 - To have rightsizing recommendations generated we need to follow the [datadog integration guide](https://help.nops.io/integrate-datadog-with-nops-platform.html). 


2 – To perform rightsizing, you first need to configure EventBridge for Essentials for all your accounts by [following this guide](https://help.nops.io/essentials-storage-configuration.html). 


3 – Once the EventBridge is setup and DataDog is integrated as per Step 1 and Step 2 – you should start seeing recommendations in Rightising page within 24 hours of DataDog Integration


4 – To go to rightsizing Recommendations – Go to Essentials Tab in the Main Menu > Rightsizing.

****

![](https://lh7-us.googleusercontent.com/XATGhgiB7mlZRLBSnw77_4wCIt4qGSFEd4lZCEyPGwBQznXIjHNukTcTK9i30ltj-54SWuII6w3p_BNHL9j6riTbH83UcDItvnCnuMBXGKicwww7neycwTKXzal_Sm5B8dfTC9V8rxWZ2G88r6JSyBs)

****

5 – This is the Recommendations Page. Currently we Support only EC2, in future you can see more tabs for RDS, etc. The page has Columns that show us The Instance ID and Instance Name, ENv, Current size, recommended size, and region. Along with Annual and Monthly Savings. Lastly you’ve Actions button. 

****
 ![](https://lh7-us.googleusercontent.com/ET6a7ZMyTn6XK6Yy7xUWO6lSA-0_TVkz67GyVyA9jYRiP2Wwzcv1OJLAwdlvwkpqOt1vQAKC4W7eiHRCOCZe4kgAZW4q606O5n28myOqGjVKv9UR3-xL7TA-5l0Djuygb_WQluFRuiARFVrrOkcqnzM)
****

6 – To rightsize please click the Actions button for selected Resource or Group of Resources. That leads you to this details page.

****
![](https://lh7-us.googleusercontent.com/YlTrBTzg11fU8xwt5bROTB8xH3bPaM9-5kB5NIggrUI321aoBW_k7o8RaYZ6xkZ6vYlw5sCKKCpKV-7AFGegSO_jcGbxmwexisa8lfPQZ6jMwL-dOGhuvsi-oKTULTY83oA2hKk2l8loSo0tzui1BGE)
****

7 – The details page, you have the account and target selected by default, if you’ve finished the Step 2 successfully. If not you’ll see a message to set up Eventbridge first to select a valid Target. That takes you back to Step 2. If everything is good the only thing needs to be done here is check resource details and click the Rightsize button.

8 – Above step will redirect you to the nSwitch page. Where it has created and scheduled an nSwitch for 10 minutes in future if you selected “Now” as an option or your selected date and time if you choose “Later” as an option.

9 – This is the nSwitch page where you can monitor your scheduled Rightsize trigger. You can delete it before it has run or is scheduled to run. But once it’s triggered you can’t delete it.

****
![](https://lh7-us.googleusercontent.com/t6jnA75NPjpBk1YfiHLd1R3SFXb2ldlZPax3ZOpXpcSaowPi3TAZfq7r2k9L5yzNU-FgKiKosMeeHJGpMGeyupsUqI1eQE-kBW0wDqxUVxgaP3fhSuNw9xX3BTEX6fiHKFQYY65PpyLDvpMOcusCo3k)
****

10 – Next you can move to AWS to check if the Instance has rightsized to the recommended family type.


## Notes & FAQs

- EC2 rightsizing requires a downtime, AWS has no SLA but in our experience it takes 2-3 minutes. It depends on the size of the instance.
- EC2 rightsizing currently has recommendations for only downsizing, however, potentially we can add upsizing recommendations as well in future.
- EC2 rightsizing can fail for instance with Encrypted EBS volumes or instances where hibernation is enabled. Currently we mark those instances on the recommendations page in the UI and disabled them from getting rightsized. We are working on a feature to support those types as well.


<br/><br/>

{% include custom/series_related.html %}