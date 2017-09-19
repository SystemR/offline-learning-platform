# Offline Learning Platform

## Background
In 2016 I was volunteering for a few organizations to set up a computer lab in Kisumu, Kenya. I came across [RACHEL Offline](http://dev.worldpossible.org/cgi/rachelmods.pl) (Remote Area Community Hotspot for Education and Learning) for the lab. It's basically a USB or a Raspberry Pi device that spins up a webserver and serves [free learning content](http://dev.worldpossible.org/cgi/rachelmods.pl) for the clients (mobile or desktop) to browse and consume.

RACHEL provides really amazing content for students. [World Map](http://dev.worldpossible.org/cgi/viewmod.pl?module_id=89) helped students understand geography, and be aware where they are in Kenya and in relation to the rest of the world. [CK12 Textbooks](http://dev.worldpossible.org/cgi/viewmod.pl?module_id=21) gave them access to learning Science, Technology, Engineering, and Math. Some content could have better UX though, such as the [TED talks](http://dev.worldpossible.org/mods/en-TED/) module.

## Challenges
We couldn't procure a RACHEL hardware for the lab at the time. So my original plan was to use one of the donated computers as a webserver, and then use Adhoc WIFI to connect to the server in order to access the content. Here are some of the issues I encountered with that solution:

* Most OSes don't remember the adhoc wifi network they have connected to. This means every time the server is restarted, the adhoc network needs to be created again, and the clients would have to search for the new adhoc network and connect to it.
* There were power outages, which means having a 24/7 webserver is impossible (and also the issue of reconnecting to the adhoc network)
* Using one of the computers as a webserver means assigning a static IP for that server and have a bookmark in the clients' browsers to hit that IP to browse the content (unless you want to set up a DNS server and proper networking infrastructure). This is hard for non-techie to set up.
* A RACHEL device can only serve around 20 to 50 simultaneous users (or any webserver in slow hardware).

At the end I ended up copying all the content to each of the computers in the lab and serve them locally with Mongoose, and [Kiwix](http://www.kiwix.org/) for Wiki based content.

## Proposal
I'm proposing an [electron](https://electron.atom.io/) based application for offline learning. Using electron means we can build a great UX for the learning platform without having to support old, legacy browsers that might be installed on the client's computers. We can also push for a UX that can encourage learning, instead of going basic like the TED talks module mentioned above.

The application should also support the following:

* A marketplace for the contents. We can use rsync like RACHEL, or follow the plugin architecture of Atom and Sublime's Package Control. The idea is that someone with a laptop can go on a place with Internet from time to time and sync these contents for offline consumption.
* Peer-to-peer sharing of the synced contents. Once someone has the content in their laptop, it should be able easy for them to share with other laptops ala AirDrop or use mesh networking if the hardware supports it.
* Markdown based. I think this could future-proof them. There are also many existing tools to produce and render markdowns we can re-use. Something like https://readthedocs.org/ and its [Sphinx theme](https://github.com/rtfd/sphinx_rtd_theme) for example.

## Content Consideration
* Quizzes. It is important to have the content requires a degree of interactivity. Even re-typing a Hello World line keeps them engaged. These quizzes might require custom JS to verify answers.

## Notes
This is an idea I have for a side project and want to throw it out there. I'll be growing this document as I test the idea with various NGOs and will start working on it once it's more solid. If you're interested in working on this with me, msg me through github or twitter [@r4ndw](https://twitter.com/r4ndw).
