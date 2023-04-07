---
title: Evaluate Risk for a Workload
parent: Workload
grand_parent: User Guides
nav_order: 5
layout: default
---

# Evaluate Risk for a Workload
{: .no_toc }

## Workload Risk Summary ##
{: .no_toc }

The Workload Summary displays an assessment toolbar that summarizes the associated risks.

The toolbar can be viewed by all users. Use the following path to see the toolbar. From the top menu bar or from the dashboard:  
Click **Workloads** **>** Select a **Workload** from the list **>** Click the **Compliance Ops** tab **>** from the **Lenses Summary** dialog, click the **Assessment** button for _any lens_ to see the **Assessment** page.

This topic contains:

1. TOC
{:toc}


## Assessment Page and Toolbar Overview ##
====================================

The **Assessment** page evaluates workloads against existing regulations or threat environment policies. Risk framework questions are based on best practices for compliance standards, and regulations for Security and Network. The **toolbar** displays:

* Risk levels: **Unanswered**, **Medium**, **High** and **None** and **Not Applicable**.
    
* The number of questions that fall under each risk.
    
* A graph for percentage of **Assessment Completed**.
    

[![](https://downloads.intercomcdn.com/i/o/498901322/43cd34f370fe0d58e9771a49/image.png)](https://downloads.intercomcdn.com/i/o/498901322/43cd34f370fe0d58e9771a49/image.png)

Each assessment-type contains **section tabs** below the toolbar. The data in the section tabs changes when any risk-type is clicked. See [Section Tabs](#h_d3a7389b98) for more information.

Overview of Assessments
-----------------------

Following is an overview of the different assessment types available through nOps and the pillars (for WAFR) or, section tabs that appear under different Assessment types. Each of the questions in the section tabs are assigned risk levels. Your answers to these impact compliance with Compliance Frameworks such as HIPAA.

|     |     |
| --- | --- |
| Assessment Type | Contains |
| WAFR (AWS) | Security, Cost, Reliability, Operations, Performance and Sustainability pillars. See [AWS](https://docs.aws.amazon.com/wellarchitected/latest/framework/the-pillars-of-the-framework.html) for more information |
| SaaS | Security, Cost, Reliability, Operations and Performance |
| Serverless | Security, Cost, Reliability, Operations and Performance |
| FTR | Security, Reliability, and Operations |

How Risk Levels are Assigned
----------------------------

A risk level is assigned each time a question is answered, and is based on your selections. Each question has sub-questions. Some of which may have a higher risk value than others. Answering them could change the risk or threat level for that question. Ensure that you answer all questions correctly and to the best of your ability, since they impact the safety, security, and threats to your cloud account. Support your answers by uploading and storing documents to ensure compliance.

If any question is **unanswered** it is _not_ flagged with a risk assessment. However any unanswered question may pose a greater risk, as the issues it covers are not mitigated in your environment. You can see which questions are unanswered for a specific section by clicking on the **Unanswered** section. See [How to use the Interactive Assessment toolbar](#h_d97871ba8c) for more information.

The **Not Applicable** section in the toolbar displays a count, for any questions where you have enabled the **Question does not apply to this workload** toggle. Click the toggle _only_ if the question _is not applicable_ for the selected workload. The question is disabled and removed from the assessment. Removing a question _excludes_ it from the **Assessment Completed** percentage. This will impact your overall risk levels.

[![](https://downloads.intercomcdn.com/i/o/499509292/8d2d5c08b63610179d2f8447/image.png)](https://downloads.intercomcdn.com/i/o/499509292/8d2d5c08b63610179d2f8447/image.png)

## The Section Tabs ##
================

Section tabs vary based on the type of assessment. Each tab contains its own set of questions, displays the number of questions in each, and how many of them are answered as seen in the following example.

[![](https://downloads.intercomcdn.com/i/o/498900705/1a537efc42d931ad65116de8/image.png)](https://downloads.intercomcdn.com/i/o/498900705/1a537efc42d931ad65116de8/image.png)

See [How to use the Interactive Assessment toolbar](#h_d97871ba8c) for more information.

## How to use the Interactive Assessment toolbar ##
=============================================

The **Assessments toolbar** is 'clickable'. When a section is clicked, it changes color and displays which section tabs have a related issue.

In the following example, the **Medium** risk section was clicked, and shows that the **Security** assessment tab contains 1 question that was assigned a risk level of **Medium**.  

[![](https://downloads.intercomcdn.com/i/o/498922353/1d52603a26c09279b3078803/image.png)](https://downloads.intercomcdn.com/i/o/498922353/1d52603a26c09279b3078803/image.png)

Click through both the toolbar and the section tabs to see the changes within your workload.

Click a risk level, then click the section that contains the associated risk. The question will be highlighted as shown in the following example. Questions also display whether any answers were **auto-discovered** by nOps.

[![](https://downloads.intercomcdn.com/i/o/498926797/250a4165c8d72de08568f037/image.png)](https://downloads.intercomcdn.com/i/o/498926797/250a4165c8d72de08568f037/image.png)

Related Functionality for the Assessment Summary page
-----------------------------------------------------

* Click the **Expand All /Collapse All** button within each question to view question prompts. These may help you answer the question.
    
* Click the **More** (3 dot) **menu** to see additional functionality such as the ability to **Attach a Document** or **Add a Label**.
    
* Click the **Export Report** button at the top right to export a report-type available in the list.
    
* Click **Exit Assessment** to return to the Workload Summary page.
    

Additional Resources:
---------------

[How to Create Workloads](../create-workloads)

[Viewing and Managing Workloads](../viewing-and-managing-workloads)

[Well-Architected Framework Review](../well-architected-framework-review)