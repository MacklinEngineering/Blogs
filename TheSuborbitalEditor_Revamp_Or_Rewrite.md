FOUND AT: https://blog.suborbital.dev/the-suborbital-editor-revamp-or-rewrite

![post header](https://user-images.githubusercontent.com/60084237/225018575-78a45152-22e3-4080-9531-58f0586af769.png)

The Suborbital Editor: Revamp or Rewrite?

Nyah Macklin
·
Published Feb 9, 2023
·

5 min read
Table of contents

    Overview: What is the editor?
    The Problem
    The Experiment
    The Findings
    The Solution

Overview: What is the editor?

The Suborbital Extension Engine (SE2) plugin editor is a web application that uses SE2's APIs to provide a low-friction environment for your end-users to write, build, test, and deploy plugins in a variety of programming languages like JavaScript, TypeScript, Rust, or Go. The editor can be easily embedded into any web application via an iframe or with a custom React component.

![Suborbital Dark Theme](https://user-images.githubusercontent.com/60084237/225018276-dfd9de03-8720-4e5f-a2e8-061b5f743d6d.png)

A navy-colored text editor with some sample code inside, and a "Build" button on the top left, with a "Build to deploy" button below it, a text area for entering test data, and a "build to run test" button below that. All those conponents lie in the left panel which sits 1/4 of the way from the left. A "Console" panel lies 1/3 of the way from the bottom, which has the words "Waiting for build" in the console section. There is also a "Test Results" section to the right of the console section.
The Problem

![Screenshot of Suborbital's Editor integrated into a company (Streamdal)'s UI](https://user-images.githubusercontent.com/60084237/225018926-5c16ed13-1ced-4c54-8d71-e026bb758f52.png)

Our editor is the gateway to the Suborbital plugin experience. However, the first generation of the editor does not visually integrate as seamlessly into our customer’s applications as we would like. After seeing how the editor has been used over the past year, we decided to pursue a new iteration of the plugin development experience that is easier to integrate, more powerful, and yet still lightweight. Having a product that is easily themeable, has a more intuitive user interface, and has responsive sizing for smaller screens would make our customers’ experiences much more fluid.

So, should we build something new from scratch or iterate on the current version of the editor? We decided to investigate four different solutions that could fit our needs.
The Experiment

We spent two weeks exploring whether a lightweight IDE (using VSCode or Eclipse Theia) would meet our requirements, or whether we needed to build out an entirely custom editor (using Monaco or CodeMirror) to replace the current product. Our existing editor is built on CodeMirror 5, so we also explored whether upgrading and polishing the current codebase would be sufficient.

VSCode

For VSCode, we created an extension that sends a POST request to a placeholder API.

![Screenshot of Visual Studio Code: which shows 2 panels (one on top and one on the bottom of the screenshot). The one on top shows Typescript code that makes a POST request to a API, and the second (bottom) half of the screenshot shows the Extension running with the desired output](https://user-images.githubusercontent.com/60084237/225020666-8c12daeb-4898-47c0-82a2-e669afcf011e.png)

We also tested whether we could have an output console and a testing panel where users could test inputs and the resulting outputs from the custom code written in the editor.

![A screenshot of Visual Studio Code showing a testing panel on the left 1/3 of the screenshot, and a Output logs section at the bottom of the screenshot](https://user-images.githubusercontent.com/60084237/225021288-eba397bb-ef59-4df2-9ae2-5a9f4a72aec3.png)

The goal of this investigation was to see whether we could create feature parity with our existing editor using VSCode extensions. We were able to replicate most of the editor's current functionality which placed it as a clear front-runner early on in our experimentation process.

Eclipse Theia

We found that Theia provided many of the basic building blocks of a plugin editing experience right out of the box. Theia allowed for more UI customization and was also compatible with VSCode extensions. This allowed our team to build a more custom editor experience than VSCode would allow on its own. Because of this, Theia and VSCode both sprung to the top as possible solutions we should consider implementing.

Monaco

We also looked into Monaco, the editor that powers both VSCode and Theia. We wanted to know whether it was viable to build up from Monaco's basic interface. We found that Monaco had excellent syntax highlighting, auto-complete, built-in documentation and keyboard shortcuts, among many other features. Implementing Monaco would be a relatively low lift, however, this is what we were already doing with CodeMirror 5. Monaco itself didn't provide any additional features that CodeMirror wasn't already implementing that would be useful for our particular use case.

CodeMirror

The last solution we reviewed was CodeMirror 6. The team took two approaches to implement CodeMirror: create a new editor from scratch, or update our current editor from CodeMirror 5.

For the first approach, we built a prototype and analyzed how to implement a few of the core features for the current editor. This approach was beneficial to understand whether it was worth recreating all the UI around the base editor component.

![A screenshot that shows CodeMirror's code editor running in the browser with some demo code and also showcasing the autocomplete properties of CodeMirror](https://user-images.githubusercontent.com/60084237/225021320-eff767f9-e2d4-4c2f-9692-f92b91c92cd6.png)

For the second approach, instead of recreating everything, we upgraded CodeMirror on the current editor and gave it a fresh coat of paint.
The Findings

VSCode extensions and Theia both had several pros that made the process of creating an extension/demo plugin editor as low effort as possible. VSCode is a familiar editing environment for developers, it has thorough documentation, theming is accessible and built into the solution, and it provides all the infrastructure needed out of the box. However, both VSCode and Theia require a server-side runtime environment. This added enough complexity that it outweighed the pros of either solution, especially for customers who need to keep everything on-premises.

Monaco and CodeMirror 6 are both browser-only solutions, without infrastructure requirements or much user interface out of the box. These solutions allow for the most customization, which was something the team found appealing. Between the two, we didn't find sufficiently compelling reasons to invest in switching away from our current, CodeMirror-based solution.
The Solution

We want to have an editor that is as easy for our customers to integrate into an application as possible. That requires forgoing any solution that necessitates an isolated server-side environment. After our investigations, we made a deliberate choice to not reinvent the wheel, and instead iteratively improve our existing editor component. We’ll start with quick wins paring down and clarifying the UI, adjusting for various screen sizes, and then move on to theming, additional logging and debugging capabilities, and more. The end result will be a seamless, secure, and completely client-side plugin authoring experience. We’re already hard at work and we look forward to sharing the results of our endeavors soon!

Stand by for liftoff.

- Suborbital
