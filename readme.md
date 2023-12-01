# Linux Command Line (MacOS, Linux or Windows)

Objectives
Run commands to gain knowledge of your current system and current session
Search and run previous bash commands

Task 1: Use SSH to connect to an Amazon Linux EC2 instance
In this task, you will connect to a Amazon Linux EC2 instance. You will use an SSH utility to perform all of these operations. The following instructions vary slightly depending on whether you are using Windows or Mac/Linux.

WINDOWS USERS: USING SSH TO CONNECT
These instructions are specifically for Windows users. If you are using macOS or Linux, skip to the next section.

From the Lab Information pane, select the PPK link and save the file. The file name will be similar to Ec2KeyPair-PPK.ppk. Typically your browser will save it to the Downloads directory.

Make a note of the PublicIP address.

Download PuTTY to SSH into the Amazon EC2 instance. If you do not have PuTTY installed on your computer, download it here .

Open putty.exe

Configure PuTTY timeout to keep the PuTTY session open for a longer period of time.:

Select Connection
Set Seconds between keepalives to

30
Configure your PuTTY session:
Select Session
Host Name (or IP address): Paste the Public DNS or IPv4 address of the instance you made a note of earlier. Alternatively, return to the EC2 Console and select Instances. Check the box next to the instance you want to connect to and in the Description tab copy the IPv4 Public IP value.
Back in PuTTY, in the Connection list, expand SSH
Select Auth (don’t expand it)
Select Browse
Browse to and select the ppk file that you downloaded
Select Open to select it
Select Open again.
Select Yes, to trust and connect to the host.

When prompted login as, enter:

ec2-user
This will connect you to the EC2 instance.

Windows Users, skip ahead to the next task.

MACOS AND LINUX USERS
These instructions are specifically for Mac/Linux users. If you are a Windows user, skip ahead to the next task.

From the Lab Information pane, select the PEM link and save the file. The file name will be similar to Ec2KeyPair-PEM.pem.

Make a note of the PublicIP address.

Open a terminal window, and change directory

cd
to the directory where the pem file was downloaded. For example, if the file was saved to your Downloads directory, run this command:

cd ~/Downloads
Change the permissions on the key file to be read-only, by running this command (replace <ssh-key> with the name of the file you downloaded earlier):

chmod 400 <ssh-key>
For example:

chmod 400 Ec2KeyPair-PEM.pem
Note: Your file name may be different from the example.

Run the below command. (replace <ssh-key> with the name of the file you downloaded earlier, and replace <public-ip> with the PublicIP address you copied earlier):

ssh -i <ssh-key> ec2-user@<public-ip>
Type

yes
when prompted to allow the first connection to this remote SSH server. Because you are using a key pair for authentication, you will not be prompted for a password.
Task 2: Run familiar commands
In this exercise, you run a few commands to gain some general knowledge of the system and session that you are using.

From the terminal, enter

whoa
and press Tab. Notice that the auto complete feature displays the full command,

whoami
.

Press Enter to display your current username.

Enter

hostname -s
and press Enter to display a shortened version of computer’s host name.

Enter

uptime -p
and press Enter to display the uptime of the system in an easily readable format.

The console window shows the command prompt with the following commands: whoami command and the output is ec2-user, hostname -s with the output of ip-10.x.x.x, and uptime -p with the output of however long your linux AMI has been running.

Figure: The whoami, hostname, and uptime commands give basic information about the system you are currently using. This can be useful if you need to find the user, IP address, or how long your system has been running for troubleshooting purposes.

From the terminal, enter

who -H -a
and press Enter to display information about the users who are logged in and some additional information.
who -H -a command shows which users are logged into the system and displays the following information: Name, Line, Time, Idle, PID, Comment, and Exit.

Figure: The who -H -a command displays the information about the user such as the name, line which gives information, time the event occured, idle time of the user, Process Identifier (PID), comment and exit time.

Enter

TZ=America/New_York date
and press Enter. Then enter

TZ=America/Los_Angeles date
These commands identify the date and time of alternate locations in the world.

The terminal window shows the current date and time of New York and Los Angeles.

Figure: The TZ=America/New_York date and TZ=America/Los_Angeles date will give you the output of the current weekday, month, date, time, timezone, and year. In this example the output for Los Angeles is Wed Sep 1 18:27:35 PDT 2021.

Note

If your time on your system is not set properly, you will receive a time that is incorrect.

Some professions use the Julian date to conduct business. The Julian format continues consecutively instead of restarting the date at 1 at the beginning of each month. For example, in the Gregorian calendar format, the day after January 31 is February 1. However, in the Julian format, the day after January 31 is February 32 instead of February 1. You can check this information by entering

cal -j
in your terminal to see the Julian dates for your current month.
The cal -j command has been entered into the command prompt in your terminal outputs Julian dates for the current month.

Figure: The cal -j command will gives the output of the current month in Julian date. In this example, the output given is September 2021, Thursday, day 245.

Enter the

cal -s
or

cal -m
commands to display alternate views of the calendar.
cal -s or cal -m commands to display alternate views of the calendar.

Figure: The cal -s command gives the output of September from Sunday through Saturday. The cal -m command gives the output from Monday through Sunday.

Note

There are many options to display calendars. Check the cal man page for details.

For your last command, enter

id ec2-user
into the terminal, and press Enter to see your unique ID and group information about your specific user.
The command id ec2-user gives specific ID and group information about the current ec2-user of the terminal.

Figure: The output of the id ec2-user gives the user id, group id, and groups that the user is apart of.

Task 3: Improve workflow through history and search
In this task, you attempt to ease your overall workload by reusing commands through search techniques, manual visualization of the bash history log, and reuse of the last command.

Start by viewing the current bash history. Enter

history
and press ENTER. In the output, check if the commands that you see are the commands that you used in task 2.
The history command displays a list of the last commands entered into the console.

Figure: When the history command is entered, you should see a list of all of the commands that were used within this lab.

To search your previous history, press CTRL+R to bring up a reverse history search. In the reverse history search feature of the terminal, enter

TZ
and press Tab. This step brings up an old use of the date command that you can edit. Using your arrow buttons, you can now edit the command inline.
Note

This is a history searching feature that gives you the ability to edit the command that you search for. You must use Tab autocomplete to edit and run the commands.

CTRL+R will bring up a reverse history search

Figure: To run a reverse history search, press CTRL+R. Typing TZ (from the previous steps) then the Tab button will bring up the use of the date command. In this example, the up and down arrows were used to bring up the date command.

Enter

date
into the terminal, and press Enter. Enter

!!
and press Enter. This step gives you the ability to to rerun the most recent command.
The !! command returns the last command entered into the keyboard.

Figure: To run the last command that was entered into the keyboard, !! was used. For this last example, date was the last command that was used. To run this command again, !! was used.

End lab
Follow these steps to close the console and end your lab.

Return to the AWS Management Console.

At the upper-right corner of the page, choose AWSLabsUser, and then choose Sign out.

Choose End lab and then confirm that you want to end your lab.

ABOUT THE AWS COMPONENT
Amazon EC2 provides a wide selection of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity and give you the flexibility to choose the appropriate mix of resources for your applications. Each instance type includes one or more instance sizes so that you can scale your resources to the requirements of your target workload.

This lab uses a t3.micro instance, which should be selected by default. This instance type has 1 virtual CPU and 1 GiB of memory.

Additional Resources
Amazon EC2 Instance Types
Amazon Machine Images (AMI)
Status Checks for Your Instances
Amazon EC2 Service Quotas
Terminate Your Instance
For more information about AWS Training and Certification, see https://aws.amazon.com/training/.

Your feedback is welcome and appreciated. If you would like to share any suggestions or corrections, please provide the details in our AWS Training and Certification Contact Form.

© 2022 Amazon Web Services, Inc. and its affiliates. All rights reserved. This work may not be reproduced or redistributed, in whole or in part, without prior written permission from Amazon Web Services, Inc. Commercial copying, lending, or selling is prohibited.
