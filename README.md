<h1>SOAR EDR Project | Part 1</h1>

<p align="center">
<img src="https://snipboard.io/S3c17g.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Description</h2>
<br />
<p align="center">
Welcome to part one of five for the series on the SOAR EDR project. The goal of this project is to get some hands-on experience with an EDR and SOAR, by using LimaCharlie and Tines. You don't want to miss out on this, because this will allow you to learn how to create your own detection and response rules and create playbooks for automation. For those who complete this project, this is definitely something that you can talk about during your interviews, just like the other project series that I have on my channel. I am certain that there will be some errors popping up for some when tackling these labs and if that happens I would love for you to build up your research skills. 
<br />
<br />
<br />
  For part one of the series, we will be focusing on creating our playbook workflow and brainstorming what actions we want our playbook to take. The main reason why we want to build out our workflow is to help organize our thoughts and then see what steps our playbook should take to accomplish our objective.
<br />
<br />
<br />
<img src="https://snipboard.io/EyKXda.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
The objective for this playbook will be to send a slack message and an email containing important information about the detection that LimaCharlie had generated. Tines will then prompt the user if they want to isolate the machine. If the user selects "yes", LimaCharlie would then automatically isolate the machine to create a workflow. I'll be using a site called draw.io, as it is free to use and and quick to access. One thing to keep in mind is that these workflows do not need to be pretty, you just need to do it and build it out. Later down the road you can make it look pretty, especially if you are presenting this to a client. If it's just between you and I, I'd rather you focus on doing it, versus spending hours on making it look visually appealing.
<br />
<br />
<br />
<img src="https://snipboard.io/yJhCqA.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
  Now I'll be using draw.io to create our Playbook workflow. If you have never seen draw.io before, well let me give you a quick introduction here. Over to the left-hand side, these are the icons that you can select and drag. On the right, we have our diagram settings so we can have our styles if we want to.
<br />
<br />
<img src="https://snipboard.io/DEKN7H.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://snipboard.io/xt24Mq.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  We can change the grid, we can also have it as a grid or not. There are some other miscellaneous settings that you can play around with. 
<br />
<br />
<img src="https://snipboard.io/2hRrFf.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  So first and foremost, let's draw a square right here. I'll type "SOAR EDR Playbook". So this is going to signify the beginning of our Playbook workflow. So what exactly do we want our Playbook to do? I'll go ahead and open up a Notepad.
<br />
<br />
<img src="https://snipboard.io/1dVaLW.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<img src="https://snipboard.io/VCzoIZ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Let's type "story" because a story is another name for a playbook. Essentially, we want to create a detection in LimaCharlie. First, this will detect, let's just say, Hacktool for now. Then, once LimaCharlie detects the Hacktool, we want to push it over to Tines. 
<br />
<br />
<img src="https://snipboard.io/k3l0pi.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  We'll want to send important information to our Slack and email. So the Slack and email will contain, let's say, the time, the computer name, the source IP, the command line, and the file path. Just like with any EDRs, you'll likely have a sensor ID of some sort.
<br />
<br />
<img src="https://snipboard.io/I9Ub7r.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  So we'll include the sensor ID and maybe even a link to the detection (if applicable). Once the message has been sent to Slack and an email has been sent as well, Tines will prompt the user to isolate the machine and give them a yes or no option.
<br />
<br />
<img src="https://snipboard.io/vNu0xT.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  If the user selects yes. LimaCharlie should automatically isolate the machine and a new message should be sent to Slack. This message will contain the isolation status, with a note of that the computer has been isolated.
<br />
<br />
<img src="https://snipboard.io/3LMwmt.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Now, if the user selects no, Lima will not isolate, and the message will contain the isolation status, with a note that the computer is not being isolated; please investigate. Everything sounds about right.
<br />
<br />
<img src="https://snipboard.io/6hyNUD.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Now obviously we can change the wording later on. It doesn't need to be this exactly, but this is a pretty good rough draft. It's good to put down your thoughts and then have a reference. So let's go ahead and build this out in draw.io.
<br />
<br />
<img src="https://snipboard.io/bKATHo.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  All righty, so on draw.io. We have our "SOAR EDR Playbook". We know for a fact that we want Slack, LimaCharlie, and an email. So what I'll do is use this rounded rectangle to signify Slack. We could just duplicate this and I'll say "Email". Then another for LimaCharlie.
<br />
<br />
<img src="https://snipboard.io/KyDU6v.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Let's add some color here. I'm going to select purple for SOAR. Email is going to be green, and LimaCharlie is going to be blue. So how this is going to work is that we first need to create a detection in LimaCharlie.
<br />
<br />
<img src="https://snipboard.io/HnsDtI.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  So we are going to assume that the detection is going to be sent over to Tines. Which makes me remember, I need to add in Tines. Tines is going to be purple and Slack can be red. Finally, let's leave some space in between.
<br />
<br />
<img src="https://snipboard.io/sa7YXj.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  So first and foremost, LimaCharlie will send a detection over to Tines. Double-click and type "Detection". So our detection sends over to Tines. Tines will then send a message over to Slack, with the details and email.
<br />
<br />
<img src="https://snipboard.io/0Unxep.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  I don't like how these lines look, so I'll just select this option right here on the right. Select straight. That looks a lot better. Let's create a new message saying, "Message with details contains the time, computer name, Source IP, process command line, file path, sensor ID, and the link to the detection (If applicable)".
<br />
<br />
<img src="https://snipboard.io/EJSw4b.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Let me go ahead and format this just a bit. There you go. So LimaCharlie detects the tool, and sends the detection (alert) over to Tines. Tines will then send a message with details" over to Slack and Tines will then send a message with details as well over to email.
<br />
<br />
<img src="https://snipboard.io/e392aV.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  What we're missing is the user input. So let's create a rectangle and say "User Prompt". Aswell as "Does the user want to isolate the machine".
<br />
<br />
<img src="https://snipboard.io/mo1jkQ.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Then let's create a two dimes. Let's create one for "NO" and "YES". I'll color "YES" as green and I'll color "NO" as red. If yes, then LimaCharlie should automatically isolate the machine.
<br />
<br />
<img src="https://snipboard.io/iBqjly.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  So what that means is that LimaCharlie is going to isolate the computer if it is infected. So what we're going to is create two computer icons to signify an infected machine and an isolated machine.
<br />
<br />  
<img src="https://snipboard.io/djeCsY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Let's run this back real quick. The user double-clicks the hack tool, and the computer then gets infected. Lima charlie detects the hack tool and then ships the detection over to Tines. 
<br />
<br />
<img src="https://snipboard.io/djeCsY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  Tines will then send a message with details over to Slack. Tines will also send a message with details via email and it would ask the user if they wish to isolate the machine from the user's prompt. 
<br />
<br />
<img src="https://snipboard.io/djeCsY.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  If the user selects yes, then LimaCharlie will go out and isolate the machine automatically. Afterward, a message will then be sent over to Slack containing the isolation status. Now if the user selects no, then it'll just send a message over to Slack saying the computer was not isolated and to please investigate. 
<br />
<br />
<img src="https://snipboard.io/nX4G1B.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
  I think that's pretty good for now. We can change this up later on down the road and just remember that this does not need to be pretty. That's it, now we have our workflow ready to go. We will be referencing this going forward and in part two, we will go over how to install and set up LimaCharlie so we can get ready for the exciting stuff later on. That is it for this part and I hope you are as excited as I am to work together on another project. Remember to stay curious and do things differently.
<br />
<br />
<img src="https://snipboard.io/nX4G1B.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<br />
<br />
