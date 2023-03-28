FOUND AT: https://blog.suborbital.dev/the-suborbital-editor-introducing-editor-v2
<img width="960" alt="Suborbital Editor V2 Cover Image" src="https://user-images.githubusercontent.com/60084237/228295579-22be65ec-9aaf-4aec-ad99-456d00fe7cbc.png">

The Suborbital Editor: Introducing Editor V2
Nyah Macklin's photo
Nyah Macklin
·
Mar 28, 2023
·

2 min read

Houston, we are officially in orbit.

The SE2 Plugin Editor:

The Suborbital Extension Engine (SE2) Plugin Editor is an embeddable web application that provides a low-friction environment for your end-users to write, build, test, and deploy plugins for your SaaS application.

![image](https://user-images.githubusercontent.com/60084237/228295809-26201b9f-3ab9-4972-b81c-c60f1a7bc7fe.png)

The Past:

When we began developing the next iteration of the Editor, we first had to tackle our most obvious problem: fitting in. For most customers, our design stuck out like a sore thumb.

![image](https://user-images.githubusercontent.com/60084237/228295965-041c9613-4455-4ea6-91ff-7e5872c74422.png)

We also had trouble with narrow viewports.

![image](https://user-images.githubusercontent.com/60084237/228296085-70c5dc11-c35e-4188-a429-2a5285c21fce.png)

It wasn't great. We went so far as to consider a complete rewrite, but with customers already in production, we decided that an iterative approach would yield a majority of the benefit faster.

To that end, we quickly shipped an initial light theme and set to work on the deeper renovations. We knew we needed to reduce the Editor's complexity and visual footprint. And we did.

Introducing Editor V2:

![image](https://user-images.githubusercontent.com/60084237/228296211-a5a5dc3e-90fa-4571-bd09-6db0e38b613f.png)

Horizontal space is scarce, and our panel-based design simply didn't fit on smaller screens or when framed by our customers' applications. So we completely removed the left action panel and the tab bar.

![image](https://user-images.githubusercontent.com/60084237/228296364-56144681-d014-4f06-a2a4-e937064265cd.png)

We also streamlined our interface and interaction patterns in pursuit of a more intuitive experience:

    All logging has been combined into a single, collapsable panel, rather than being split across multiple tabs.

    Our "Build" step is now implicit when deploying or testing a plugin, instead of requiring manual interaction.

    We now warn if a user tries to navigate away while the Editor contains undeployed changes.

Additionally, our predefined themes have been redesigned to be more neutral and thus fit into a wider variety of contexts.

The Future:

This is a great step, but we're not done. We've begun landing the initial building blocks for customer-provided themes to help the Editor feel right at home in any SaaS application. After that, we'll work on bringing auto-formatting and more robust testing capabilities into the Editor.

We want to provide the best possible experience for our customers and their end-users and we won’t stop until that is true.

Ready to try out SE2 and our next generation editor? Sign up for the SE2 Beta or visit suborbital.dev to learn more!

Hold on to your seats. We are just getting started.

-Suborbital
