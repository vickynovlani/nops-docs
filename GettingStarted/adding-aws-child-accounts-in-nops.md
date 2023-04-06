---
title: Adding AWS Child Accounts in nOps
parent: Getting Started
nav_order: 4
layout: default
---

# Adding AWS Child Accounts in nOps #

There are three different methods of onboarding a child account:

1.  During Automatic Setup
    
2.  Via your nOps Organization Account
    
3.  With the help of Terraform Multi Account Registration (IaaC)
    

All of these onboarding methods give the child accounts IAM permissions that allow nOps to read metadata, CloudTrail, and everything else about the child accounts. It allows nOps to offer its monitoring and recommendations features for security, operations, reliability, and performance.

## During Automatic Setup ##
======================

You can add child accounts to nOps during the automatic setup process. When you add an AWS Organization Master Payer Account during the automatic process, nOps will automatically pull in child accounts associated with the Parent account. nOps learns about these accounts with the help of your Cost and Usage Report (CUR).

During the Automatic Setup process, you need to set up an _AWS Organization_ account and add an _AWS Master Payer Account_:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895415/6410f127c02f91318f5a9eb2/Z1FGFEHzggKPQ70kgi-1EkFjqUQ2nUEXuF0wl6JHYY-tvthgE5URCXE2Zr5ZDA_P-kDaDMdmIKpsu-9sftk6UIgh0bceM_DTs0-k10oLcV94i-cqeCtXXBfTp9bNa2wqaoMJBNrxyZAEIFaRGCQucnk_jT8cjakdj81MY55LRjC3ON9i00oB2abtWQ)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895415/6410f127c02f91318f5a9eb2/Z1FGFEHzggKPQ70kgi-1EkFjqUQ2nUEXuF0wl6JHYY-tvthgE5URCXE2Zr5ZDA_P-kDaDMdmIKpsu-9sftk6UIgh0bceM_DTs0-k10oLcV94i-cqeCtXXBfTp9bNa2wqaoMJBNrxyZAEIFaRGCQucnk_jT8cjakdj81MY55LRjC3ON9i00oB2abtWQ)

After your Master Payer Account is linked successfully, the automatic setup will then ask you if you want to onboard the child account(s) right now. You can click on **Automatic Setup** against each child account to start the child account onboarding process:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895421/6b38f2a10add4fec4849bd46/AlFSJ0hHSz_EU95l430iWQe66rJhNSJvhTNKi48aVRYr9_7kECYghkrJf0t51B-wLcEuqx6qnVD3dxjryVIPOCuxMt85GqW8aW-VG2X4ocNEctXzZ5yI7Bmvvo83llaSlHPeanAgx4K-K-kfNVmryoV34pHt5EuhZel61E3UaYYdkvrkj6P07-LRAA)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895421/6b38f2a10add4fec4849bd46/AlFSJ0hHSz_EU95l430iWQe66rJhNSJvhTNKi48aVRYr9_7kECYghkrJf0t51B-wLcEuqx6qnVD3dxjryVIPOCuxMt85GqW8aW-VG2X4ocNEctXzZ5yI7Bmvvo83llaSlHPeanAgx4K-K-kfNVmryoV34pHt5EuhZel61E3UaYYdkvrkj6P07-LRAA)

If you click on **Automatic Setup**, it will redirect you to the respective AWS account for you to create a stack that nOps will use to access the child account. Please ensure that you are logged into the respective child AWS account when you click **Proceed**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895430/776063b618014caf5bfe21b5/2jGHW-fmRiQRRBcuxCuLrSU4WowFJFJdi5VuBFrOFycH8jZEAZHLrGuKUodWaLYDevMkW-xc9zEr0JadV1cmYoJLadY4DH7RS1_iXBzc-3JMQqOq98y7B0ajQjVdDvml6s_UQnEAONZ68SDGIVNuBHST-5gFanLlHH07rsbHBTZU2nvhOUv7wW_0sg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895430/776063b618014caf5bfe21b5/2jGHW-fmRiQRRBcuxCuLrSU4WowFJFJdi5VuBFrOFycH8jZEAZHLrGuKUodWaLYDevMkW-xc9zEr0JadV1cmYoJLadY4DH7RS1_iXBzc-3JMQqOq98y7B0ajQjVdDvml6s_UQnEAONZ68SDGIVNuBHST-5gFanLlHH07rsbHBTZU2nvhOUv7wW_0sg)

When you click on Proceed, you will be redirected to **AWS > CloudFormation > Stacks > Create stack > Quick create stack** page, with most of the information pre-filled. Click on **Create Stack** to start the onboarding process.

During the onboarding process of child accounts, nOps will not ask for the CUR since it has already been added with the AWS Organization Master Payer Account.

The setup process can take 1-2 hours to pull in data from AWS.

You can skip the onboarding of child accounts during this setup and add the accounts later.

## nOps Organization Account ##
=========================

If you decided to skip onboarding of the child accounts during the Automatic Setup, you can still onboard your child accounts via your nOps Organization Account.

Click on your account at the top right corner of the page and go to **Organization Settings > Cloud Accounts,** there you will see a list of child accounts that nOps detected with the help of your **Cost and Usage Report (CUR)**.

You can onboard each child account with _Manual Setup_ or _Automatic Setup_:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895434/415d028eb6048e5ce4dbbb1a/S-mHUrSyb3iNocAvz4FOUeEBl1YvJ6F07ia1ev28JE24APzFRTybgbiWJiZDhCriH99WPnDGB5mwTOSkIMh5N75MW28UkBIeRMU0ssh3qGheTnl-79JGUYNQFjBohFNzMEw4tFEglzL17DF4zle75f_pIMvtBsu1c1sJFbQhpCtZSejD2w_fhyDOhg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895434/415d028eb6048e5ce4dbbb1a/S-mHUrSyb3iNocAvz4FOUeEBl1YvJ6F07ia1ev28JE24APzFRTybgbiWJiZDhCriH99WPnDGB5mwTOSkIMh5N75MW28UkBIeRMU0ssh3qGheTnl-79JGUYNQFjBohFNzMEw4tFEglzL17DF4zle75f_pIMvtBsu1c1sJFbQhpCtZSejD2w_fhyDOhg)

Click **Automatic Setup** or **Manual Setup** to start the onboarding process.

If you click **Automatic Setup**, it will redirect you to the respective AWS account for you to create a stack that nOps will use to access the child account. Please ensure that you are logged into the respective child AWS account when you click **Proceed**:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895438/d9896d61a7d56dfed7d67cda/2jGHW-fmRiQRRBcuxCuLrSU4WowFJFJdi5VuBFrOFycH8jZEAZHLrGuKUodWaLYDevMkW-xc9zEr0JadV1cmYoJLadY4DH7RS1_iXBzc-3JMQqOq98y7B0ajQjVdDvml6s_UQnEAONZ68SDGIVNuBHST-5gFanLlHH07rsbHBTZU2nvhOUv7wW_0sg)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895438/d9896d61a7d56dfed7d67cda/2jGHW-fmRiQRRBcuxCuLrSU4WowFJFJdi5VuBFrOFycH8jZEAZHLrGuKUodWaLYDevMkW-xc9zEr0JadV1cmYoJLadY4DH7RS1_iXBzc-3JMQqOq98y7B0ajQjVdDvml6s_UQnEAONZ68SDGIVNuBHST-5gFanLlHH07rsbHBTZU2nvhOUv7wW_0sg)

When you click on Proceed, you will be redirected to **AWS > CloudFormation > Stacks > Create stack > Quick create stack** page, with most of the information pre-filled. Click on **Create Stack** to start the onboarding process.

If you click **Manual Setup**, you will be redirected to the Account Details (Manual Setup) page. Since nOps already has the information for S3 bucket that houses the CUR, the field for the S3 bucket will be locked. Click **Update Account** to start the onboarding process:

[![](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895442/8d8b0d88c95bd1302e210570/VjC5oLeLLTCOzlaSMOgbFtMYpnBj26O5kEK71-byzEY-ft8zGezFC62ojLM29ZyxD3GLz9YPR5lIt7QegL2JjDifeOmDxJ_sE2j8_tIgSEAXWXpLF7-PcFhw3nJE97fvuFVpYMx7WqNpP8rSpNgZ3UIEBhlk4GRsD0toe5EnOw9LM7e7bh5GvkXYRw)](https://nops-b92747f563e0.intercom-attachments-7.com/i/o/573895442/8d8b0d88c95bd1302e210570/VjC5oLeLLTCOzlaSMOgbFtMYpnBj26O5kEK71-byzEY-ft8zGezFC62ojLM29ZyxD3GLz9YPR5lIt7QegL2JjDifeOmDxJ_sE2j8_tIgSEAXWXpLF7-PcFhw3nJE97fvuFVpYMx7WqNpP8rSpNgZ3UIEBhlk4GRsD0toe5EnOw9LM7e7bh5GvkXYRw)

During the onboarding process of child accounts, nOps will not ask for the CUR since it has already been added with the AWS Organization Master Payer Account.

The setup process can take 1-2 hours to pull in data from AWS.

## Terraform Multi Account Registration (IaaC) ##
===========================================

Use the Terraform Multi Account Registration process when, along with your AWS Organization Master Payer Account, you have numerous child accounts that you want to onboard in nOps. This process makes it easier for you to onboard your child accounts with minimal effort.

You can simply provide the Organizational Unit IDs (OUs) of your child accounts during this setup and nOps will take care of the rest.

To learn about this onboarding process, see [Adding Multiple AWS Accounts to nOps with Terraform](adding-aws-accounts-to-nops-with-terraform.md).