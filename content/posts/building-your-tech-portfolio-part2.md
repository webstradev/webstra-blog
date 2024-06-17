+++
title = 'Building your Tech Portfolio. - Part 2'
description = 'Organizing your existing projects on GitHub'
date = 2022-11-25T20:24:07+02:00
draft = false
tags = ['portfolio', 'coding', 'projects', 'software-engineering']
+++
#### Organizing your existing projects on GitHub.

![image of a laptop](/images/laptop.jpg)
Photo by [Arnold Francisca](https://unsplash.com/@clark_fransa?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/collections/v99L6B0Xnps/programmieren-im-web?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)

---
### Previously on
In the [last article](https://blog.webstra.dev/posts/building-your-tech-portfolio-part1/), we covered why you should put extra effort into your tech portfolio, and which mindset you need to adopt to ensure your projects reflect how good an engineer you actually are.

Now let’s take a look at some simple things we can do to improve and organize our existing hobby projects.

### Please don't overdo it! 
I’ll start by saying that I am a perfectionist and tend to look a little too negatively at my older projects. When I am going over my old work, I have to force myself not to unnecessarily change too much of the existing code and focus on making stuff look more professional and easier to read. It will be hard to find a balance between improving something while not spending too much time on it, but you will get much better at this over time.

---

### Where should we store our projects?
First, we need a place to collect, manage and share all our projects. The obvious choice would be GitHub, the most widely adopted version control system you will find. It’s free, easy to use and offers a lot of features that will help us organize our portfolio. If you don’t have any experience using git as a source control system, I would highly suggest you take a look at [this video](https://www.youtube.com/watch?v=USjZcfj8yxE&ab_channel=ColtSteele) on youtube (or any other resource on the topic).

### Creating an organization
GitHub offers some functionality for organizations. This feature is intended for companies or open-source organizations to group repositories and control access amongst developers, contributors and maintainers. I, however, also use it to group my portfolio projects into one place. This gives me a few benefits:

- I can use one link to share all the code of my portfolio projects.
- I can control access to private repositories more easily. For example, I can give an interviewer access to all my private portfolio projects by simply adding them to a team in the organization.
- It allows for additional high-level documentation about yourself or your portfolio as a whole.

*One additional benefit is that I start to treat my projects more seriously when I treat my portfolio as a company. This is yet another way to show people that you can be a professional software engineer.*

> One cool project that I am working on at the moment is creating all my portfolio projects in one organization and deploying them all to the same kubernetes cluster. That way I not only have all my code grouped but also the actual applications running in production as if it were run by a company. I have just started out and I will be writing about my progress on medium so drop a follow if you want to be notified when these articles are published.

The best thing about GitHub organizations, it’s free for public repositories. That means you won’t need to pay any additional fees for your portfolio projects as long as you are sharing them publicly, which you are likely to be doing anyways. If you want to learn how to set up an organization take a look at the GitHub documentation.

---

### Choosing a name
Before we commit our code we need to think of a name for a project and its repository. We want something clear, descriptive and if at all possible, catchy.
Stay away from **only** using generic terms like `webapp` and `database-querier` and try to think of some sort of product name. If you have multiple repositories for a project it is a common practice to use hyphens and then the component name. For example: `medium-frontend` `medium-backend` `medium-auth` could be a way to differentiate between various repositories in the same project.

### The README File
In addition to version control, one of GitHub’s handy features is that it will allow us to display a nicely styled README file on the front page of our repository. This is generally what engineers use to describe what their project is and how it works. Besides that, you will want to include any instructions or documentation that anyone using your project as a developer might need. Although the chances are slim that a portfolio project is actually used by other developers, it is good practice to write this documentation. If not for yourself then at least to show a future employer that you can write professional documentation.

README files are formatted using markdown which allows you to use symbols, images and rich text formatting. This will allow us to create a nice-looking landing page for our repository, which goes a long way when you are trying to impress a hiring manager.

*A more detailed article on writing good README files can be found here. If you need some inspiration on how to make your documentation look good, I would suggest looking at some of the frequently used open-source projects on GitHub as they will have some nice readme files to explain the ins and outs of a project.
Some examples: [Fiber](https://github.com/gofiber/fiber), [Sequelize](https://github.com/sequelize/sequelize), [Numpy](https://github.com/numpy/numpy), [Go](https://github.com/golang/go), [Ruby on Rails](https://github.com/rails/rails)*

### Licensing a project
> **Small disclaimer:** I am by no means a legal expert and my knowledge of copyright laws and licensing is entirely based on what I have found in [GitHub’s documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/licensing-a-repository) on the matter.

One of the choices when creating a repository will be whether you want it to be publicly accessible. I would suggest that you make your portfolio projects publicly available unless you have a strong reason not to. If the project is the next Whatsapp or Uber, you might wanna consider making it private and only giving interviewers access on-demand. Unfortunately, that means you won’t be able to easily share your portfolio with someone, so there is a trade-off.

One thing to keep in mind is that, according to GitHub's documentation, a public repository **without a license** is still protected under copyright laws.

If you don’t mind people reusing your code, or even making better versions of it then you could also add a LICENSE.md file through the settings and choose a license that is appropriate for you. I suggest carefully reading the abovementioned GitHub documentation and all its resources.

### Adding your code
Now that we have created a repository with a great name and a great README file, we can start importing our code. I would advise first committing whatever work you already have and then making any improvements in new commits. This not only keeps a clear history of what changed (which is exactly what source control is for), but it also shows the world that you have revisited an old project and tried to improve it. This is something that I would be looking for when hiring someone as being able to iterate and improve is just as important as being able to create something new.

---
*In the next article, we will take a look at improving our actual code and making sure there aren’t any security vulnerabilities or outdated dependencies.*



