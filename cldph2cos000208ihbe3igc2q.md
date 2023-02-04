# A Study on End-to-End Testing Framework Cypress in comparison to Selenium

# What is Cypress?

Cypress is a new-age end-to-end testing tool. End-to-end testing ensures the application is tested exactly how the users are going to interact. Its installation is effortless, usage is smooth, and it runs very fast.

Let’s discuss more in the following sections.

# Why are we even thinking of Cypress?

For a long time, testing has been an integral part of the software Quality Assurance department. However, the tools supporting this culture were merely doing 100% justification to the capabilities of modern development teams. With the agile way of software development, it is essential now that team members get all tools that can support quick and reliable feedback on the codes.

What if I tell you, that developers would now be able to write automated tests with their existing web technology knowledge using almost zero configuration?

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675484959764/eff13932-9158-47b2-818d-e15874d2d683.gif align="center")

Isn’t that interesting? 😮 Indeed.

“Developers writing automated tests” – this seems unreal, but now it is possible. That is where Cypress comes into the picture. It is a revolution that empowers the whole development team and not only the QA engineers.

Let’s quickly explore the features to find out how painless and swift it can be.

# You will care about the below points as a development team

In this section, we will quickly discuss the unique features that Cypress is offering.

## The Tool is amazing

Let me give you a quick walkthrough of the tool. Imagine you have written some Cypress test cases in a spec file and run the Cypress runner using the following `npx` command.

`npx cypress run`

It will blow up your mind. The UI is so soothing and provides all information needed to start up.

See the screenshot below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675430732466/8a992431-20a7-4e85-8343-e9c0964edaa0.png align="center")

It provides you with two options either *E2E Testing* or *Component Testing*. Even all docs are provided inside the tool, no need to go to google and ask. Refer to the screenshot of the docs section below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675430765546/5083573a-ab1b-4237-b8a3-d352694d41dc.png align="center")

Now, after you select a type, it asks you for a browser. Super user experience, I must say. Here is the capture.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675430799599/a121091f-8cfe-4fec-b0ae-282f643346e3.png align="center")

It is time to see the main screen in action that lists all the test files. See the screenshot below. In this case, it is displaying one test file named [*todo.cy*](http://todo.cy)*.js*.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436541191/24fe8342-8216-4690-a020-227870feb93d.png align="center")

When you click on the test file name, it will try to run all cases written inside the spec file. Let's have a look.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436593803/b04ddbca-68d2-4426-bf75-94df0187e1f7.png align="center")

Oops! We got one error. Notice how a detailed message is given. This error is because I forgot to run my app. So, I will run the app, and then we will explore other features in the following sections.

## An update is instant, no need to rerun Cypress

Once you make any change to the spec file, Cypress detects and reruns the tests for you. Wonderful. 😊

## Direct instant feedback on what Cypress is doing with your cases

Every command like [`cy.click`](http://cy.click)`()` (to trigger the click event of an HTML element), `cy.type()` (to enter some data inside the HTML element) when run by the runner, logs all details about it. It means a lot to the team for debugging. You can go through each step on the left panel and see visually on the right panel how it interacts with the UI with the command.

Refer to the image below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436681430/1945ccb0-9650-42a4-9329-a596055f8053.png align="center")

The left panel has logged all the steps with details. As soon as you hover over any step, you will see the element getting highlighted on the UI on the right side.

## Interactive time-traveling

Imagine that you are going to each command and step to determine what happened on the UI. That is what we always wish to do as developers, right? The interactive time travel feature gives you the flexibility to go back to each step to see what happened at that time of execution. ⏳

## Debugging is not a pain anymore

Any error in the test cases will be properly presented with details about the error along with the line number. See the screenshot below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436741326/4ae03e65-7536-46d6-8953-7975d972c4ea.png align="center")

Surprisingly, it also has a stack trace that can take you to the line number inside the spec file directly. Try that. It is seamless. You will land up on your IDE with the file opened and the cursor at the error line number. 🧑‍💻

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436776033/533c9d5c-8ebe-4919-9025-794efeeb6fd9.png align="center")

## Zero server involvement

With the features like spies, stubs, and clocks, there is no requirement for an actual server. With interceptors, the API calls can be manipulated with a custom response by designing mocks. This is very powerful and promotes TDD. Test case development can be started without a backend.

## **Screenshots and Videos**

Cypress can take screenshots and videos of the test case. It is especially useful when test cases fail.

## Cypress supports any front-end framework or website

As long as the application or website runs inside a browser, Cypress can test your cases beautifully. All modern JavaScript frameworks like *Vue*, *React*, *Angular*, *Elm*, etc. are supported. It can even render any server-rendered apps.

## Real-world Examples

The team has crafted a dedicated website just for learning Cypress and its features with real-world examples. Another reason to cherish. Here is the Link - [https://learn.cypress.io/real-world-examples](https://learn.cypress.io/real-world-examples).

Now, let's see how Cypress stands in comparison to Selenium.

# Cypress Vs Selenium

In this section, we will compare some key features between Cypress and Selenium.

## Getting Started

This is something I care about while evaluating software.

***With Cypress,***

Inside the project directory, just run the following command

`npm install cypress --save-dev`

(NOTE: Assuming Node.js and npm installed)

or download from [https://download.cypress.io/desktop](https://download.cypress.io/desktop). That is it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436827753/5611cd51-2e2f-4111-8870-879a82718acd.png align="center")

***However, with Selenium,***

It is not that easy to start. There is no clear path to getting started. See the screenshot below of the getting started page. There is quite a read and also some concepts you need to grasp.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436900338/afe1ab83-8b4c-4adc-a22c-a46d62255436.png align="center")

Now little below on the same page, on scrolling down, you will see multiple links. Refer to the following screenshot. It makes life more complicated.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675436917191/9164a900-17f6-4b50-8eb6-89f6668e160d.png align="center")

## Language Support

***With Cypress,***

It is just JavaScript. Cypress supports writing test cases in JavaScript. All web developers know JavaScript or might have used it at some point in their projects/careers.

The learning curve for Cypress is shallow, trust me. Personally, I know QA teams have started Cypress in just two days without any external or trainer help.

***However, with Selenium,***

It supports *JavaScript (Node.js), C#, Groovy, Java, Perl, PHP, Python, C#*, etc. This can be treated as an advantage because team members with different skills can contribute.

## End-to-End Tests

***With Cypress,***

The goal is to write and execute end-to-end test cases and not unit test cases for the back-end services. That means testing how the user is going to experience the product.

Writing such tests with Cypress is very engaging. The syntax to fetch HTML elements from the web page is straightforward with selectors similar to JavaScript.

***However, with Selenium,***

End-to-end tests are problematic in Selenium. They tend to encourage the usage of *XPath* which can go wrong for complex HTML structures. Now, imagine the team debugging why certain tests fail. It can be a nightmare to go through these *XPaths* and find out the issues. Maintenance becomes very difficult.

## Debugging

Undoubtedly, Cypress is the winner in this case.

***With Cypress,***

The tests directly run inside the browser. The execution process of each step inside each test case is crystal clear. Cypress grabs snapshots at the moment of test execution. This allows the development team to hover over a specific test to see exactly what happened at each step. The error messages are super concise and to the point.

The browser developer tool can also be leveraged to find out details about the tests. Check out the following video.

[Cypress Vimeo](https://vimeo.com/242961930#t=264s)

%[https://vimeo.com/242961930#t=264s] 

***However, with Selenium,***

Again, this is not straightforward and out of the box. Debugging an *XPath* error can be challenging and time-consuming.

## Cypress is fast

***With Cypress,***

As testing is always an integral part of the development process, it becomes fast because of real-time execution. It is designed to support the simultaneous execution of tests and codes, thanks to the new architecture built from the ground up.

***However, with Selenium,***

It runs as a different component not integrated with the code base. Tough to visualize your test then and there when you develop it. Thus, it is slow and does not contribute to fast-paced environments.

# Known Limitations

With so many jaw-dropping features, it still, Cypress fails in certain scenarios. ☹ Let's find out.

1. Testing for mobile screens is carried out inside a browser, so native device functionality like the camera or fingerprint authentication testing is not possible at this moment.
    
2. Different tabs or window testing are not possible.
    
3. Iframe testing is not possible at this moment, but there is an experiment going on.
    
4. Currently, Cypress supports testing on Chrome, Edge, and Firefox browsers.
    

# Future Improvements

The roadmap can be explored from the [Cypress Priority board](https://github.com/orgs/cypress-io/projects/13/views/1).  One of the features planned is the support for the browsers Safari and Internet Explorer.

# Use Cases of Companies using Cypress

We looked at a lot of features that the development team enjoys while working on Cypress. That is a great reason to adopt this framework.

Moreover, let’s analyze some real use cases with companies that adopted Cypress to improve their development processes.

## The GoDaddy development team wanted to deploy fast and increase test coverage

![GoDaddy Reports Fourth Quarter and Full Year 2021 Results](https://mma.prnewswire.com/media/819539/GoDaddy_Logo.jpg?p=twitter align="left")

In this [recorded session](https://youtu.be/ZSbNT-Fff9A) by the *GoDaddy* team, they touched upon a lot of pain points of testing with *Selenium*. Here is a capture of the video.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675440042578/f26844f5-1666-4cd8-a06b-8d50a49f6513.png align="center")

See how they were struggling with the slow development process due to limitations, flakiness, and very low test coverages.

As a result, they started to evaluate a lot of tools like [*webdriver.io*](http://webdriver.io)*, Nightwatch, Appium*, etc. Finally settled down with Cypress due to the following reasons.

* Community & Docs – The community is mature and Docs have everything well maintained
    
* Smoke Test
    
* Dashboard – That displays all the details about the tests
    
* Live execution – This is amazing as you can see the tests running inside the browser.
    

See the image below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675440261506/93863d24-cc04-47d8-8ab2-55ead09bb7f6.png align="center")

When they surveyed the developers after adoption, it was inspiring. Refer to the image below for some feedback.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675440300209/60479c5c-283e-4252-b451-673dca939d86.png align="center")

The results that the GoDaddy team started to see are mentioned below.

* 70% increase in productivity
    
* 75% decrease in test maintenance
    
* 2,500 tests run daily
    
* 100% new feature test coverage
    

## Monterail switched to Cypress from Nightwatch.js which is a selenium-based testing tool

![We develop and design Web & mobile apps · Monterail](https://www.monterail.com/hubfs/Monterail%20logo/svg/Monterail%20Logo%20Classic.svg align="left")

While they achieved 30% coverage with *Nightwatch.js*, when asked about the stability and security of the application by the client, they faced challenges to improve the coverage. That is because of the following three reasons.

1. Selenium Web Driver is issue-prone – It can throw issues without giving friendly error messages.
    
2. Test stability – Test cases can fail on any random attempt.
    
3. Dissatisfied with the pace of writing new tests – Writing test cases, running, and observation can take an ample amount of time.
    

The detailed case study is documented in this [blog post](https://www.monterail.com/blog/end-to-end-testing-with-cypress).

## Quizlet not only switched to Cypress for language reasons but also due to some critical issues with Capybara – again a selenium-based testing tool

![Quizlet Raises Series C Funding from General Atlantic | General Atlantic](https://www.generalatlantic.com/wp-content/uploads/2020/05/quizlet-logo-indigo-rgb.jpg align="left")

Documented in [this medium blog](https://medium.com/tech-quizlet/cypress-the-future-of-end-to-end-testing-for-web-applications-8ee108c5b255), the explanation is to the point on why they moved from *Capybara* but did not select *Cypress* straight away. They evaluated all options and their study circles around the following points.

1. Language – They wanted to write tests in a language matching what skill set they had.
    
2. Flaky tests – *Capybara* tests were failing with errors.
    
3. Slowness with the runner – Selenium-based testing tools are very slow because they spin up a browser for every test.
    

They spent a good amount of time researching the tools like *Puppeteer* and *TestCafe*. These tools came as somewhat useful but again they fail to convince the management of documentation, cross-browser support, debugging, community support, etc.

Refer to the picture of the chart taken from the blog above.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675441207252/f7e28482-213d-4bdd-9400-91dd52c174db.png align="center")

Eventually, *Cypress* is the winner. 🥇

## Pixelcabin wanted to feel confident every time they deploy

![Pixelcabin - Shopify Plus Agency](https://uploads-ssl.webflow.com/61f54f867e39ff1ef2da097d/62322884637029725ff5f5ed_Pixelcabin-BLK-Logo%E2%80%93LogoType.png align="left")

The goals of *Pixelcabin* were to achieve the following points. The picture is taken from the video of the session by Michael Shannon, (Co-Founder). The [video](https://www.youtube.com/watch?v=kRTma2CztxE) is embedded below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1675441222846/39d39bd4-8250-433c-92ab-22970b74f9f0.png align="center")

In the video embedded below, Michael mentions the motivation behind choosing *Cypress* as the automation tool and *TravisCI* to run the tests in the Continuous Integration environment.

The team was taken aback by the test suite recording with screenshots and videos.

%[https://www.youtube.com/watch?v=kRTma2CztxE] 

More case studies can be found at - [https://www.cypress.io/case-studies/](https://www.cypress.io/case-studies/)

# Should I start in my company/project?

We have seen a lot of proof that Cypress is a magic wand for the development teams. Now here are some suggestions for the software development teams to consider its adoption.

## Getting started is easy

It is not going to hurt the existing team to start up. You can argue that Cypress can be complicated for testers who are into manual testing. However, it is not really. Cypress documentation even makes it more interactive. Some context of JavaScript, and they are good to go. For developers who are into front-end development, it is just the cream on top of the cake. 🏃‍♂️

## Support with widely used language JavaScript

Selenium can be handy in terms of a wide range of technology to write test cases. Still, the problem Cypress is solving is to bring the whole development team together with one universal language. Developers can see their code running inside the browser itself with details about the tests. At the same time, QAs can enjoy working without extra effort on external libraries or drivers.

## End-to-end Tests that give you confidence in User Experience

Think of the front-end development team in your organization who are always looking for UX feedback from product owners or real users. They can now able to get the feedback right there while developing the feature way before it goes to the stakeholders.

Therefore, with minimum configuration, if both Developers and QA engineers can collaborate with simple syntax to imitate user behavior, why not adopt that? 🥂

## Debugging is effortless

We have discussed above how debugging is hassle-free in Cypress. 🤝 For fast development, better debugging gives an edge. Moreover, maintenance becomes hassle free when breaking changes are introduced.

## Superfast Live Test Runner

For a development team, it is always a dream to ship bug-free code, and when it comes to the execution of tests while coding, it contributes a lot to self-satisfaction. 😊

On the other hand, give this tool to an existing QA team with prior automation experience with different frameworks. They will feel more connected to the code base along with the performance.

## Integrations with Continuous Integration Tools

This is a need of this hour and Cypress has it. Comfortable integration with CI like *GitLab CI*, *Azure DevOps*, *TravisCI*, etc provides confidence to deploy fast and iterate.

# Adoption Strategies

To adopt Cypress’s End-to-end Automation framework within the development team, some questions need to be answered first. 🤔Here are they.

1. Do you have a Web UI that is used by users on browsers *Chrome*, *Edge* and *Firefox*, and *Safari*, *IE* can be excluded?
    
2. Do you have iframes implemented inside the web pages and do you need to test them?
    
3. Do you have mobile apps that need to be tested?
    

If your answer is no to the above questions, you can go with Cypress. If you have both web and mobile apps, then better to test the web app with Cypress and select some other framework for the mobile app testing.

Now, to start up, we should do a POC to find out all features. We can take help from the real-world examples website from Cypress. Otherwise, some new and less critical projects can experiment with Cypress to observe its suitability. Then, other project teams can adopt it.

# Final Thoughts

Cypress came as a revolution with an unconventional way to deal with end-to-end automation testing. It is a game-changer for the development teams in terms of delivering quality software in a defined time and it does not add much complexity on top of the development process.

A go-ahead. 🤝👍⏩

# Feedback

Let me know if you liked what you read. Please share with your friends and colleagues. 🙏🙏

# References

* [https://cypress.io/](https://cypress.io/)
    
* [https://learn.cypress.io/real-world-examples](https://learn.cypress.io/real-world-examples)
    
* [https://www.cypress.io/blog/2020/07/08/end-to-end-testing-mobile-apps-with-ionic-and-cypress/](https://www.cypress.io/blog/2020/07/08/end-to-end-testing-mobile-apps-with-ionic-and-cypress/)
    
* [https://www.cypress.io/case-studies/](https://www.cypress.io/case-studies/)
    
* [https://medium.com/tech-quizlet/cypress-the-future-of-end-to-end-testing-for-web-applications-8ee108c5b255](https://medium.com/tech-quizlet/cypress-the-future-of-end-to-end-testing-for-web-applications-8ee108c5b255)
    
* [https://www.monterail.com/blog/end-to-end-testing-with-cypress](https://www.monterail.com/blog/end-to-end-testing-with-cypress)