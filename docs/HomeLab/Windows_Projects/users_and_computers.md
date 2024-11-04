## Active Directory Users and Computers

Our first Stop in Active Directory will be **Active Directory Users and Computers**. If you have or will get a job within IT Operations. **Active Directory Users and Computers** will probably be the one tool you will use the most, if not everyday. This tool is crucial to most IT Operations and it's where we create most objects of Active Directory. This tool can be launched from any **Domain Controller** and can be used to manage and configure Active Directory Domain. This means it doesn't matter if you're logged on to DC-01 or DC-02, whatever action you perform will be replicated over the other domain controller. There is also a client tool you can use on either a Windows 10 or Windows 11 machine. If you're wondering why you would want to do this when you can just logged on to the Domain Controller and perform your work there, well imagine you're the IT Manager for your IT Department and you've recently hired a Junior System Administrator or a Desktop Support Technician. You might not want to give him full control of your Domain Controllers on Day 1, but he will still need to be able to create user accounts and perform password resets. So installing the Active Directory tools on his laptop will make more sense than granting him full access to your domain controller. 

## Launching Active Directory Users and Computers

Now time for us to get our hands dirty. To Launch Active Directory Users and Computers, we can do this a few different ways.

### From Server Manager

Inside of Server Manager, I can click **Tools** and from there I can click **Active Directory Users and Computers**

[![Select creation type](images/ad_users_and_comp/ad_users1.jpg)](images/ad_users_and_comp/ad_users1.jpg)

### From the Start Menu

Click on the Start Menu, then look for the **Windows Administrative Tools** folder and from there Open **Active Directory Users and Computers**

[![Select creation type](images/ad_users_and_comp/ad_users2.jpg)](images/ad_users_and_comp/ad_users2.jpg)

### From the Run box

If you press **Win Key + R**, you will launch the run box. From here you can enter, **dsa.msc** then click OK to Launch **Active Directory Users and Computers** 

[![Select creation type](images/ad_users_and_comp/ad_users3.jpg)](images/ad_users_and_comp/ad_users3.jpg)

Similarly, if you're inside of a powershell session, you can also **dsa.msc** and then press enter, to launch **Active Directory Users and Computers**.

[![Select creation type](images/ad_users_and_comp/ad_users4.jpg)](images/ad_users_and_comp/ad_users4.jpg)

All of these methods really accomplishes the same goal, which is to launch **Active Directory Users and Computers**. 

Once the **Active Directory Users and Computers** Microsoft Management Console (MMC) opens, you can now begin to perform your necessary tasks. We've already used this console when we created our User account earlier, but this wil be a bit of a deeper dive into what **Active Directory Users and Computers** is able to do.

[![Select creation type](images/ad_users_and_comp/ad_users5.jpg)](images/ad_users_and_comp/ad_users5.jpg)

At first glance, there are a few things to notice, you can see the name of the console at the top of the Window.

[![Select creation type](images/ad_users_and_comp/ad_users6.jpg)](images/ad_users_and_comp/ad_users6.jpg)

You can you the menu bar right below it:

[![Select creation type](images/ad_users_and_comp/ad_users7.jpg)](images/ad_users_and_comp/ad_users7.jpg)

Below the menu bar is called the tool bar:

[![Select creation type](images/ad_users_and_comp/ad_users8.jpg)](images/ad_users_and_comp/ad_users8.jpg)

And below that, you have the console tree and the navigate pane, where you'll be perform most of your task. 

[![Select creation type](images/ad_users_and_comp/ad_users9.jpg)](images/ad_users_and_comp/ad_users9.jpg)

### Working with Active Directory Users and Computers

First, thing you'll want to do is, expand your domain name, so you can view all of the relevant options. Simply click on the arrow next to your domain name.

[![Select creation type](images/ad_users_and_comp/ad_users10.jpg)](images/ad_users_and_comp/ad_users10.jpg)

[![Select creation type](images/ad_users_and_comp/ad_users11.jpg)](images/ad_users_and_comp/ad_users11.jpg)

You will see that you have a few items that already exist within **Active Directory Users and Computers** which were create during the installation. Although these looks like folders, they are not. These are called **Organizational Units (OU)** and **Containers (CN)**. They they are use to store and organize different objects within **Active Directory Users and Computers**. If you look closely, you'll notice that the icons are different. The icon's that looks like the **Domain Controllers** and **prbUsers** (Note: I created the prbUsers OU during my initial installation of Active Directory on DC-01) are called **Organization Unit (OU)** and the rest of the icons **Builtin**, **Computers**, **Keys** and etc. are called Containers. 

[![Select creation type](images/ad_users_and_comp/ad_users12.jpg)](images/ad_users_and_comp/ad_users12.jpg)

If I were to click on the **BuiltIn** container, I will see in the information pane that have various **Security Groups**. I won't go through what each of these groups are for right now, but know that these groups control access to certain resources within the Active Directory Domain. As we continue on in this project, I will using these groups to grant my user access to various resources and privileges.

[![Select creation type](images/ad_users_and_comp/ad_users13.jpg)](images/ad_users_and_comp/ad_users13.jpg)

The next up is the **Computers** container. If you click on this, you will notice that it's currently empty, unless you've already added a computer to your domain. This Container is the default container used when adding Computers and Servers to our Active Directory Domain. It's empty, but we will add objects to this container in the future.

[![Select creation type](images/ad_users_and_comp/ad_users14.jpg)](images/ad_users_and_comp/ad_users14.jpg)

Next is the **Domain Controllers** Organizational Unit (OU). Notice I said Organization Unit and not container. In this OU we can see DC-01 and DC-02. By default whenever we add a new domain controller to our Domain, the objects for these computers will be added automatically to this OU. 

[![Select creation type](images/ad_users_and_comp/ad_users15.jpg)](images/ad_users_and_comp/ad_users15.jpg)

I will skip the rest and move on to the **Users** container. In here, you will a mix of users and groups. Similar to the **Builtin** container, there are security groups that exist in this container, and these groups will grant you access to different privileges within Active Directory. Be careful when assigning your users to these groups, granting someone too much privileges can cause major damage to your infrastructure, avoid adding users to any security groups that exist here and in the **Built-in** containers, until you understand what permission and privilege will be granted.

[![Select creation type](images/ad_users_and_comp/ad_users16.jpg)](images/ad_users_and_comp/ad_users16.jpg)

### Structuring Active Directory Users and Computers

Although you can use both Organizational Units and Containers to store objects within Active Directory, you can only create Organizational Units, you cannot create Containers, but don't be disappointed there really isn't any different between the two and Organizational Units will more than suffice for what we want to do. Currently our **Active Directory Users and Computers** console looks to be a little empty. If you've ever worked for an Organization that has a well populated **Active Directory Users and Computers**, you might see many different Organizational Units in a tree like structure. Different companies have their own way of organizing their Active Directory Users and Computers, so really there is no one correct way to do it. What works for a large enterprise might not work for a small business. The best way to structure Active Directory Users and Computers is mostly based on your organization size and number of employees. 

Let's say I work for a company called Ontario Biogas and it has 50 employees, below are the list of teams:

- CSuite Leadership - 4 Users 
- Executive Leadership - 5 Users
- Managers - 4 Users
- Accounting Team - 5 users
- HR Team - 4 users
- Field Staff - 10 users
- IT team - 4 users
- Marketing Team - 4 users
- Legal Team - 4 users
- Office team - 6 users

A few ways we can do this, We can create an Organizational Unit for each Team and manage it from there. It will look like this:

[![Select creation type](images/ad_users_and_comp/ad_users17.jpg)](images/ad_users_and_comp/ad_users17.jpg)

Now, this is not a bad way to do it, because later on when we get into **Group Policies** a structure like this will cause is extra work when applying our policies. 

You can also do something like this, to make it simpler: 

[![Select creation type](images/ad_users_and_comp/ad_users18.jpg)](images/ad_users_and_comp/ad_users18.jpg)

This way, we just have one Organization Units for Users and another one for computers, we can also add more OUs to contain things like Security Groups, Distribution groups and Service Accounts.

[![Select creation type](images/ad_users_and_comp/ad_users19.jpg)](images/ad_users_and_comp/ad_users19.jpg)

This way, we can make things a little bit more clean and organization. However, this is designed based on the current state of Ontario Biogas. However, maybe we should plan for the future. Let's say in 5 years Ontario Biogas who has it's head office in Toronto, ON, opens a branch office in Waterloo, ON and buys another Biogas plan in Alberta. Our structure can now look like this.

[![Select creation type](images/ad_users_and_comp/ad_users20.jpg)](images/ad_users_and_comp/ad_users20.jpg)

As you can see, we have a lot of different ways you can organize your Active Directory Users and Computers Structure. A few things to keep in mind when implementing your structure:

- Group Policies – Having a good OU design will make implementing and managing group policies much easier. I’ve seen a drastic decrease in issues with proper OU design.

- Delegate permissions – Being able to delegate rights at a granular level and auditing those rights is a must. A proper OU structure will allow you to easily delegate permissions at a granular level.

- Administrative tasks – Modifying user accounts, using LDAP queries, reporting, and bulk changes are all common administrative tasks.  If Active Directory is a mess, these simple day-to-day tasks can become difficult for the whole team.

I think it is a good start for you. You can follow any one of my examples for it or you can build your own. Since you're probably doing it in a Homelab environment, you can always delete and re-create your Organization units to find the best structure.




