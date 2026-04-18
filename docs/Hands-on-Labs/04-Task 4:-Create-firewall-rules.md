# Task 4: Modify Firewall Rules to Permit North-South Traffic
![](images/image55.png)
Now that we have peered our VNets and built our routing tables everything is ready, right? Not quite! Remember, we pointed the UDR towards the load balancer, which then passes traffic to the FortiGate for inspection. We need to set a policy in the firewall to permit traffic. Let’s start with North-South traffic like traffic destined to the Internet.

1.	First, let’s refresh our memories of which port is connected to the Public and Private subnets. This will help us to write our firewall rules.
2.	Use the picture below to help you map your interfaces.
    ![](images/FirewallPolicy1.png)
3.  Navigate to your hub-studentXX-lab-rg resource group. Use the search bar at the top if needed. 
4.	Click on azlab-FGT-A.
5.	Scroll down until you see the public IP address on the right-hand side. Note your IP address will be different from the one below.
    ![](images/FirewallPolicy2.png)
6.  Copy the address, go to a new tab in your browser and enter https:// then paste the IP address of FortiGate-A. Hit enter on the keyboard.
7.	Log in with username: fortinetuser Password PizzaDay12345!
8.	On the left-hand side, navigate to Network and then Click on Interfaces. 
    ![](images/FirewallPolicy3.png)
 Question 1: using the diagram at the start of this task, which interface is connected to the public subnet?

 Question 2: Which port is connected to the internal or private subnet?

Now that we know our interface mappings, let’s create our policy.

1. Navigate to Policy & Objects > Firewall Policy.
2. Click Create new.
    ![](images/FirewallPolicy4.png)
3. Make your policy match the settings in the screenshot below.
    ![](images/FirewallPolicy5.png)
4. Click OK.

    Does this mean we are done?!

    ![](images/Arewedone.gif)

    Remember, the FortiGates don’t know where to send traffic, so we need to provide static routes. First, let’s follow best practice and create some address objects for our two spokes. 

5. In the left-hand menu, click on Policy & Objects then Addresses.
6. Click the Create New button.
    ![](images/FirewallPolicy6.png)
7. Enter the configuration as shown below.

    !!! Note
        Ensure you toggle on the Static Route Configuration button.

    ![](images/FirewallPolicy7.png)

8. Click OK.
9. Repeat this process for the Backend subnet.
    ![](images/FirewallPolicy8.png)
   We are now going to create two static routes. One to the frontend VNet and the other to the backend VNet.

10. Return to your FortiGate A browser tab. 
11. On the left-hand menu, click on Network then Static Routes.
    ![](images/FirewallPolicy9.png)
12. Click Create new.
13. Ensure your configuration looks like the screenshot below.
    ![](images/to_frontend_fixed.png)
14. Click OK 
15. Repeat this process to create a static route for the backend.
    ![](images/to_backend_fixed.png)

## Testing North-South Traffic
Now for some fun, let’s test our north-south traffic.
Remember back in the beginning we created a bastion? We are going to use that now to access our “apps”.

1. Return to the browser tab with your Azure portal.
2.	Navigate to hub-studentXX-lab-rg. 
3. Scroll down until you find vm-frontend-app1 and click on it.
    ![](images/TestingNorthSouth1.png)
4.  Click on the Connect drop down.
5.	Click Connect via Bastion.
    ![](images/TestingNorthSouth2.png)
6.  Enter the username of azureuser
7.	Enter the password of HappyChicken123!
8.	Click Connect.
    ![](images/TestingNorthSouth3.png)

    !!! Note
        Notice the checkmark for open window in new tab, if nothing opens make sure your browser’s pop-up blocker isn’t preventing the window from opening it.

9. Your screen will look similar to the screenshot below.
    ![](images/TestingNorthSouth4.png)
10. Type curl www.google.com and then press enter. This will connect with google.com, do not be surprised if a bunch of text pops up on your screen, that means you were successful in accessing the internet!
    ![](images/TestingNorthSouth5.png)
11. Repeat this testing on the backend virtual machine. 
12. Now let’s test if we can ping our front-end server. Go back to the tab that has the Azure portal open and find your resource group. Locate the vm-frontend-app1 in the list of resources and open it. Scroll down to find the private IP address and copy it.
13. Go back to your backend server and ping that IP address. 
14. It will fail!
15. Why? Because we need to permit this traffic in the firewall. (Remember the UDR we created? We now know they are working to direct traffic through our Fortigate! Because the UDR forces the traffic through the firewall!)


## Enabling East-West Traffic and Testing

Modify Firewall Rules to permit East-West Traffic

Now we need to permit traffic to go from one spoke to the other, or East-West. We need to create the firewall policies first.

1.	Navigate back to your browser tab that has the admin interface for FortiGate-A open.
2.	Navigate to Policy & Objects then click on Firewall Policy. 
3.	Click Create new.
    ![](images/EastWestPolicy.png)
4.  We are going to create the first policy to permit frontend to backend traffic. Make your configuration match the screenshot below.
    ![](images/EastWestTraffic2.png)
5.  Click OK when done. 
6.  Now let’s create another policy to permit traffic from the backend to the front end. 
7.	Click Create new.
8.	Make your configuration match the screenshot below, then click OK.
    ![](images/EastWestTraffic3.png)

Testing East-West Traffic

1.	If you don’t already have bastion sessions connected to the Frontend and Backend VM’s. Please reopen them in a separate tab. 
2.	On the Backend VM type ping the ip address of your Frontend App.
3.	The command will now work as the policy permits it. 
4.	Hit Ctrl C to stop the ping.
    ![](images/TestingRound1.png)
5.  Repeat this process on the Frontend machine, but ping find the IP address of your virtual machine like you did for the first time. 
6.	The ping is successful! 
7.	Hit Ctrl C to stop the ping.
8.	Please move to the Clean up task to tear down your lab resources — if you leave them running, they will continue to incur charges on your Azure subscription!

## Clean up!

The fastest way to stop all charges is to delete every resource inside the resource group in a single action.

1.	In the Azure portal, navigate to your hub-studentXX-lab-rg resource group.
2.	At the bottom of the page, change the Display count to 100. This way we can delete everything at once!
3.	In the **Resources** list, click the checkbox in the header row (next to **Name**) to select all resources.
4.	Click **Delete** at the top of the resource list.
5.	Type the confirmation text in the prompt and click **Delete** to confirm.
6.	Azure will now remove all virtual machines, networks, load balancers, and FortiGates that were created during this lab. This may take several minutes.

![](images/cleanup_fixed.png)

!!! warning
    Deletion is irreversible. Make sure you have saved anything you want to keep before proceeding.

## You have Completed your Quest!!!
 ![](images/Congrats.png)

