<h1>SOAR EDR Project | Intro</h1>

<p align="center">
<img src="https://snipboard.io/6rb2ue.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Description</h2>
<br />
<p align="center">
welcome to part one of five for the series on the sore EDR project the goal of this project is to get some hands-on experience with an EDR and sore by using lima charlie and TI you don't want to miss out on this because this will allow you to learn how to create your own detection and response rules and create playbooks for automation for those who complete this project this is definitely something that you can talk about during your interviews just just like the other project series that I have on my channel I am certain that there will be some errors popping up for some when tackling these labs and if that happens I would love for you to build up your researching skills and if you're still unable to find the answer leave it in the comment section down below for part one of the series we will be focusing on creating our Playbook workflow and brainstorming what actions we want our Playbook to take the main reason why we want to build out our workflow is to help organize our thoughts and then see what steps our Playbook should take to accomplish our objective the objective for this Playbook will be to send a slack message and an email containing important information about the detection that lima charlie had generated timeses will then prompt the user if they want to isolate the machine and if the user selects yes lima charlie would then automatically isolate the machine to create a workflow I'll be using a site called draw.io as it is free to use and and quick to access one thing to keep in mind is that these workflows do not need to be pretty you just need to do it and build it out later down the road you can make it look pretty especially if you are presenting this to a client but if it's just between you and I I'd rather you focus on doing it versus spending hours on making it look visually appealing now before I jump into this demo I did release the my dfir sock analyst course which contains 30 plus Hands-On labs and five exclusive sock projects if you or someone you know is interested in particularly the security operations domain this course is designed to help students learn how to ask better questions and investigate Network endpoint M identity and Cloud related Telemetry once you purchase it it is yours for life and updates are free I'll put all of the links in the description if you're interested so I'll be using draw.io to create our Playbook workflow if you have never seen draw the io before well let me give you a quick introduction here over to the left hand side these are the icons that you can select and there's just a lot of shapes that you can choose from on the right we have our diagram settings so we can have our Styles if we wanted to we can change the grid we can have it as a grid or not and there's just some other miscellaneous settings that you can play around with so first and foremost let's draw a square right here and I'll say sore EDR Playbook so this is going to signify the beginning of our Playbook workflow so what exactly do we want our Playbook to do I'll go ahead and open up a notepad editor since I'm using a Mac I'll be using C editor and let's just say stories or story CU 's Playbook is called story and essentially we want to create a detection in Lima Charlie first this will detect let's just say hack tool for now and then once lima charlie detects that hack tool we want to push it over to times we'll want to send important information to our slack and email so the slack and email will contain let's say the time the computer name probably the source IP as well the process command line perhaps the file path as well and just like with any edrs you'll likely have a sensor ID of some sort so perhaps we'll just include the sensor ID and maybe even a link to the detection if applicable now once the message has been sent over to slack and an email has been sent as well tin will then prompt the user to isolate the machine and then they'll give them a yes or no option if the user selects yes lima charlie should automatically isolate the machine and a message should be sent to slack this message will contain the isolation status with a note of the computer computer has been isolated now if the user selects no then Lima will not isolate and the message will contain the isolation status with a note of the computer computer was not isolated please investigate I think that's pretty good now obviously we can change the wording later on it doesn't need to be this exact but this is a pretty good rough draft it's good to put down your thoughts and then have this as a reference so let's go ahead and build this out in draw.io all righty so on draw.io we have our sore EDR Playbook we know for a fact that we want slack Li ma Charli and an email so what I'll do is I'll use this rounded rectangle signify that slack we could actually just duplicate this and I'll say email and do it another one we'll say lima charlie let's add some color here I'm going to select purple email is going to be green and lima charlie is going to be blue so how this is going to work is that we first need to create a detection in Lima Charlie so we are going to assume that the detection is going to be sent over to tines and which makes me remember I need to add in tines well I guess tines is purple so I'll do purple and slack can be red all righty let's move that over there so first and foremost lima charlie will send a detection over to tines just double click that and say detection so our detection sends over to tines tines will then send a message over to slack and I don't like how these lines look so I'll just select it so what I can do is Select this option right here on the right and select straight that looks a lot better so I'll do that and I'll say send message with details and let's do an email as well so this will be sent there I'll change the line to straight and I'll just copy the message here and just as a reminder for ourselves here I'm just going to duplicate this and let's just say message with details contains the time computer name Source IP process command line bile path sensor ID and the link to the detection I'll just bracket this again if applicable and let me go ahead and format this just a bit there you go that looks pretty nice oh my name is wrong at least the a is capitalized there you go so Li Charlie detects the tool sends the detection over to tines or let me bracket this as alert there you go so lima charlie detects the activity and then sends that over to tines tines will then send a message with details over to slack and TI will then send a message with details as well over to email and what we're missing is the user input so let's put this as a rectangle and I'll say user prompt drag that over there and I'll put in does the user want to isolate machine and then let's put in a dime in here so if the user says yes they do and let's put that there I'll duplicate this and if they say no I'll color this as green and I'll color the no as red if it's green then what did they do what do they do so if yes then lima charlie should automatically isolate the machine sowhat that means is that I will go up and duplicate lima charlie oh I noticed I just misspelled lima charlie whoops so Lima not lime Charlie my mistake lima charlie is going to isolate is there a computer here let's search up PC and we do have a computer now again we can always make this is pretty by making the computer red now you might say why you make it red wellthis signifies that it has M installed and the mat Char is there so detects M let's just do that that looks pretty cool and this will say quarantine or isolate isolate machine now if the machine is isolated what color should it be I let's just select uh yellow perfect and I'll just say infected here goes over to Li ma Charlie detects it sends it over to tines tines will then send a message with details it'll also send a user prompt to ask the user if they want to isolate the machine it will also send the message with details via email if the user says yes then lima charlie goes out and isolates the Machine and it also sends a slack message and this message will contain the isolation status and the computer computer has been isolated now if the user selects no it'll send a message over to slack and this particular message is going to say the computer computer was not isolated and it'll say please investigate nice so if I take a look at my notepad here I did put in message isolation status if no I don't think we need that because the user is selecting no anyways we should get our status it's simply no but then when we actually select yes we do want to know the status of it because we want to know if the isolation was successful or not so that looks pretty good to me I should also include detect hack tool and this looks a lot better so let's run this back real quick the user double clicks the hack tool the computer then gets infected lima charlie detects the hack tool then it ships the detection over to tines once the detection gets shipped over to tines tyes will then send a message with details over to slack tin will also send a message with details over via email and it would ask the user do they want to isolate the machine from the user's prompt if the user selects yes then lima charlie will go out and isolate the machine automatically afterwards a message will then be sent over to slack containing the isolation status and the message of the computer computer has been isolated now if the user selects no then it'll just send a message over to slack saying the computer computer was not isolated please investigate I think that's pretty good for now I mean we can change this up later on down the road but just remember that this does not need to be pretty and it does not have to be exactly what our Playbook will do since again it is perfectly normal to realize later on that you don't need a particular action or a logic step just doesn't make any sense you can always change it if needed to save this out we'll click on file and save and that's it now we have our workflow ready to go we will be referencing this going forward and in part two we will go over how to install and set up lima charlie so we can get ready for the exciting stuff later on that is it for the video and I hope you as excited as I am to work together on another project remember to stay curious and do things differently
