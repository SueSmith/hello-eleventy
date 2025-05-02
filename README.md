# Hello 11ty!

Oh hi! Welcome to your new blog. 🎡

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/SueSmith/hello-eleventy)

**You can publish this site to Fastly for free!**

This project is a blog powered by [Eleventy](https://www.11ty.dev/), a lightweight static site generator that builds plain HTML files for quick loading by your visitors.

In this guide we'll show you how to deploy your blog to <a href="https://www.fastly.com/products/edge-compute" target="_blank">Fastly Compute</a> for super fast performance – your great posts will immediately be available for everyone, everywhere all at once. 🪄

> You can alternatively deploy your blog to other platforms, like <a href="https://pages.github.com/" target="_blank">GitHub Pages</a>. 

## Remix your own blog

**Fork** your own copy of [this repo](https://github.com/glitchdotcom/fastly-hello-eleventy), click **Code** > **Codespaces** and create a new Codespace to edit the project.

Give the Codespace a minute or two to start up – it'll automatically build and run your new website, opening a preview to see your site update as you edit! 

![The blog in a Codespace](https://github.com/user-attachments/assets/a86b11ed-76d5-4f74-9918-617e164d5c73)

* When your website preview opens, click the **🔎 Split** button at the bottom so that you can see the site side by side with your code.
* _You can close [x] the **Terminal** while you work._

## Get to know your blog

You can make edits in the files by opening them from the left sidebar. Your blog preview will update as you edit!

The files you'll want to edit are mostly in the `source` and `assets` directories:

📝 Edit the post content and add new posts in `source/posts`.

💡 Change your site HTML in the `source/_layouts` files.

ℹ️ Edit the metadata for your site in the `source/_data` folder.

🎨 Change your site style rules in `assets/style.css`.

🖼️ Add images in the `assets/` folder – you'll find an example of adding an image to a post in `source/posts/fourth-post.md`.

> Share your draft site with collaborators by opening **💻 Terminal** > **PORTS**.
>
> Change `private` to `public` by right clicking your running port, then copy the URL 📋.
>
> ![Change the port settings](https://github.com/user-attachments/assets/31802b6e-b766-4b5b-8b59-529d31fdf4ee)

## Deploy your blog to Fastly Compute

Ready to share your site with the world? Deploy it to Fastly to make it available for everyone everywhere all at once!

Grab a Fastly API key from your account and add it to your GitHub repo:

- Sign up for a <strong><a href="https://www.fastly.com/signup/" target="_blank">free Fastly developer account</a></strong>
- Grab an **API Token** from **Account** > **Personal Profile** > **API Tokens** > **Create Token**
  - _Type_: Automation
  - _Role_: Engineer
  - _Scope_: Global (deselect the _Read-only access_ box)
  - _Access_: All services
  - _Expiration_: Never expire
- **Copy the token value into your GitHub repo**
  - Open **Settings** > **Secrets and Variables** > **Codespaces**
  - Create a **New repository secret**
  - Enter the name `FASTLY_API_TOKEN`
  - Paste your token value in and save

Back in your Codespace, you should see a prompt to reload for the new environment variable so go ahead and click that.

Hit the **🚀 Publish** button and watch the Terminal output for your new site address!

Open it in a new tab and tell everyone you know. 📣

🎢 Whenever you update your content, like adding a new blog post, hit the **🚀 Publish** button again to publish to Fastly!

## How this project works 🧐

This project uses the <a href="https://github.com/fastly/compute-js-static-publish" target="_blank">Fastly JavaScript Static Publisher</a> to turn your blog into a serverless application that runs at the network edge, near your users. 

* The 11ty framework builds your posts into the HTML and other files that make up your website, placing them in the `_site` folder.
* The Static Publisher uses those files to scaffold a Compute app that compiles into Webassembly (Wasm) that can run fast and securely on the Fastly network – you'll find the Compute code in `_app` after you deploy.
* When you publish, the project deploys the app to Fastly, creating a service and uploading the Wasm to it.
* It then then publishes your content to a KV Store – a key-value store that also runs on Fastly and that your app can talk to.

Your app only needs deployed to Fastly once, after that we just update the new content to your KV Store and your Compute app will pull your posts from there.

⚙️ The settings we use to create the guided experience in Codespaces are in the `.devcontainer/` folder.

🧰 You'll find the Fastly CLI commands we use under the hood in the `helpers/publish.sh` script.

## Extensions

This project uses the following extensions from the dev community! 🙌

* [VSCode Action Buttons Ext](https://marketplace.visualstudio.com/items?itemName=jkearins.action-buttons-ext)
* [Prettier Code Formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
* [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)

## Keep going! 🛸

**Don't stop there, <a href="https://www.fastly.com/documentation/solutions/tutorials/deliver-your-site/#sending-domain-traffic-to-fastly" target="_blank">add a domain to your new site</a>.**

Check out lots more tips on using the <a href="https://github.com/fastly/compute-js-static-publish" target="_blank">Static Publisher</a> in its repo `README`. Note that if you make changes to the Compute code, you'll need to run a separate command to deploy your changes to Fastly as the **🚀 Publish** button will only deploy once, after that it'll just update your content.

🛟 Get help on the <a href="https://community.fastly.com" target="_blank">community forum</a>.

<img src="https://github.com/user-attachments/assets/17a8af4a-100f-416d-a1cf-f84174262138" width="100px"/>
