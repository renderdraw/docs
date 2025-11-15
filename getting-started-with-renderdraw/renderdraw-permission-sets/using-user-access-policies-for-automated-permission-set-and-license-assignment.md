---
description: >-
  Your users will need licenses and permission sets to use underlying features
  of RenderDraw. This can be automated based off of profile or user types. Let's
  take a look at how that works.
---

# Using user access policies for automated permission set & License Assignment

All RenderDraw users need to be licensed to access underlying functionality. Granular permissions, based on functionality and user type, are designed to ensure smooth interactions as you onboard users.



{% embed url="https://app.tango.us/app/embed/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6" %}

## [Configuring RenderDraw User Access Policies in Salesforce](https://app.tango.us/app/workflow/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6?utm_source=markdown\&utm_medium=markdown\&utm_campaign=workflow%20export%20links)

[View most recent version](https://app.tango.us/app/workflow/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6?utm_source=markdown\&utm_medium=markdown\&utm_campaign=workflow%20export%20links)

***

### # Salesforce

#### 1. The point of the following steps is to ensure new users of given types are provided with the needed permission sets and licenses to run RenderDraw platform. We're taking a profile based approach for this guide, but you can also use other filtering criteria to ensure specified users have the ability to view an interact with RenderDraw on a regular basis without having to manually install or assigned permission sets.

#### 2. To begin navigate to <mark style="color:blue;">"Setup"</mark> in your org from there search for <mark style="color:blue;">"User Management Settings"</mark>. This is to ensure that user access policies are enabled for the org.

#### 3. Click on <mark style="color:blue;">"User Management Settings"</mark>

![Step 3 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/bc1295be-445a-4d05-a2eb-93ced5d0b616/9d089600-d606-4993-b0d6-04e024cb0d65.png?crop=focalpoint\&fit=crop\&fp-x=0.0737\&fp-y=0.3678\&fp-z=2.5415\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=82\&mark-y=353\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yODUmaD00MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 4. Scroll down in the pane and ensure that "<mark style="color:blue;">User Access Policies"</mark> are enabled if they are not toggle to enable

![Step 4 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/7979bcb0-db29-45b5-b444-ef78007c5f8b/66387c5b-e890-416d-af04-ff10c783b811.png?crop=focalpoint\&fit=crop\&fp-x=0.5671\&fp-y=0.5567\&fp-z=1.1990\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=23\&mark-y=351\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMTU0Jmg9NDUmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

#### 5. Now that user access policies are enabled in the org, navigate to the quick search box and type in <mark style="color:blue;">"User Access"</mark> and you'll see <mark style="color:blue;">"User Access Policies"</mark> display on the left in the results

![Step 5 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/e54a85b0-0d7e-463a-8e72-54a8db997545/fc2801e2-fbe4-41a4-bbc1-aace36b737bb.png?crop=focalpoint\&fit=crop\&fp-x=0.0662\&fp-y=0.1058\&fp-z=2.3717\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=15\&mark-y=150\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zNDYmaD03NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 6. Click on <mark style="color:blue;">"User Access Policies"</mark>

![Step 6 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/665600ea-5799-4230-9469-ff636559d446/56d21f28-d9ff-4d15-a01d-8e743a44f3f2.png?crop=focalpoint\&fit=crop\&fp-x=0.0629\&fp-y=0.1861\&fp-z=2.6889\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=87\&mark-y=352\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yMzImaD00NCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 7. From here, let's create a new user access policy for the RenderDraw users. Click <mark style="color:blue;">"New User Access Policy"</mark>.

![Step 7 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/9471ee43-336c-4962-a93b-c7b2621e93b0/0b04f07b-4ce8-4a0c-a4d9-6a68b77b7334.png?crop=focalpoint\&fit=crop\&fp-x=0.9380\&fp-y=0.1096\&fp-z=2.9885\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=796\&mark-y=206\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zNjMmaD03NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 8. Type <mark style="color:blue;">"RenderDraw User"</mark> as the Policy Name.

![Step 8 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/258ea9f6-2336-4aad-a80c-368e4e74657f/c4c52d6c-496d-4c08-95a1-f664da3d77c3.png?crop=focalpoint\&fit=crop\&fp-x=0.4179\&fp-y=0.4144\&fp-z=2.1969\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=395\&mark-y=345\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MDkmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 9. Click on <mark style="color:blue;">"Order"</mark> field.

![Step 9 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/4da7f246-e88b-4262-88d3-c007b1917aa4/1f0fae00-59b5-4e3c-9222-d4450f1802dc.png?crop=focalpoint\&fit=crop\&fp-x=0.4179\&fp-y=0.4885\&fp-z=2.1969\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=395\&mark-y=345\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MDkmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 10. Type <mark style="color:blue;">"1"</mark> if you have no other user access policies. Otherwise, put in the number where you want this to run if you have other policies that should run prior to this. Make sure this comes after those.

![Step 10 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/926395b7-cd8a-4c11-be85-8b92fd7b9044/f0633fff-4339-403c-975a-65908bc7b06c.png?crop=focalpoint\&fit=crop\&fp-x=0.4179\&fp-y=0.4885\&fp-z=2.1969\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=395\&mark-y=345\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MDkmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 11. Now we have to apply a description so we understand what this does in the future. Type <mark style="color:blue;">"A user that will need RenderDraw Permission Sets and Licenses"</mark> in the Description field.

![Step 11 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/24eb8cc1-82e9-424e-9077-b9ec210225a5/37e8c753-ec08-4727-a81e-c7a7c9ac610e.png?crop=focalpoint\&fit=crop\&fp-x=0.5000\&fp-y=0.5659\&fp-z=1.6146\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=291\&mark-y=345\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz02MTkmaD01NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 12. Click <mark style="color:blue;">"Save".</mark>

![Step 12 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/494003c9-a674-4615-9908-4de941e2db47/5face4ea-ce2a-4d2e-b006-11a4380fc305.png?crop=focalpoint\&fit=crop\&fp-x=0.6462\&fp-y=0.6375\&fp-z=2.9608\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=533\&mark-y=336\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMzQmaD03NyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 13. Click on <mark style="color:blue;">"RenderDraw\_User"</mark> under API Name column

![Step 13 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/d6b69f6d-f59d-408a-a455-f612140955a1/00fbd8bd-8984-44d5-941a-e97e745b7e22.png?crop=focalpoint\&fit=crop\&fp-x=0.3394\&fp-y=0.2654\&fp-z=2.7555\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=496\&mark-y=354\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yMDgmaD00MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 14. From the screen, this is where we're going to be able to edit the criteria or the details of the given policy. The criteria is going to be the selection on which we're going to be applying. In this case we are applying to certain profiles for a given user.

![Step 14 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/7a22e7b8-e7bf-41e7-a3a8-4738d4ae22fb/029b99eb-b478-44c2-ae20-df65ef17bb18.png?crop=focalpoint\&fit=crop\&fp-x=0.8886\&fp-y=0.1096\&fp-z=3.1325\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=405\&mark-y=234\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz03NTImaD00NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 15. One supplied, we can now see the values based off of the profile in operator. We have several different values in this grouping and you'll have to select the ones that makes sense for your org.

![Step 15 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/2604712f-1574-4683-8ac6-10dc309f851f/618f1ec2-5fa6-4493-bfd6-fb08cbb5edbe.png?crop=focalpoint\&fit=crop\&fp-x=0.5671\&fp-y=0.4798\&fp-z=1.1623\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=4\&mark-y=319\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMTkyJmg9MTEwJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

#### 16. Now let's choose what to do for the underlying profiles. Click on the <mark style="color:blue;">"Actions"</mark> tab.

![Step 16 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/d5551efb-766b-49d2-9a0f-3fd58f72ec4d/48834ee4-a0e6-4a83-8f6f-5faf20058436.png?crop=focalpoint\&fit=crop\&fp-x=0.2346\&fp-y=0.4014\&fp-z=2.9296\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=529\&mark-y=329\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xNDEmaD05MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 17. From here you'll see that we granted permission sets in this case the RenderDraw user and a custom permission set. In addition we also granted a package license to the RenderDraw package your set up should look something similar to this, but it might not be identical.

![Step 17 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/84fbc96b-bdca-4822-bf07-820db285d17b/5dc14dc3-0da0-49f7-9fcd-b2f9339beefb.png?crop=focalpoint\&fit=crop\&fp-x=0.5671\&fp-y=0.4788\&fp-z=1.1623\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=4\&mark-y=320\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMTkyJmg9MTA5JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

#### 18. Click on <mark style="color:blue;">"User Access Policy Components".</mark>

![Step 18 screenshot](https://images.tango.us/workflows/97a8f6e1-96bf-49ac-bab5-ee2be0270ec6/steps/bf409540-7820-4bdb-93e9-0e6be4571fcb/c5dded5b-61a8-411b-b441-c98fe75fe1ec.png?crop=focalpoint\&fit=crop\&fp-x=0.5671\&fp-y=0.3274\&fp-z=1.1614\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=3\&mark-y=239\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMTkzJmg9OTEmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

### # Once completed activate and then optionally apply the policy for the given users, you can filter and select the users that you want to apply this to, but this is a quick way to add the necessary permission to a group of users based off of the criteria selected the list of users displayed will be filtered down to meet the criteria and if you press <mark style="color:blue;">"Apply"</mark> this will apply the underlying granted elements to those given users very quickly.
