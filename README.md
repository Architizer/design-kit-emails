
# Architizer Email Builder

This kit will allow Architizer designers, engineers and marketers to generate the HTML for our emails in a controlled and consistent mannerthe need to worry about crazy email HTML table structures and browser consistency. The design team will build templates that "just work" and drop them here for you to build without having to worry about styling at all…just get the content in there.

To use the kit, you first need to download and run the kit. To build an email, open the template example from the 'src/pages' folder in your text editor and replace the placeholder content and links with the new content. You'll notice no tables or any crazy HTML. That's because these are written in a compiler called Inky, which compiles the finished email to the appropriate HTML. Using Inky allows us to read the code more clearly so we can see exactly where to add and edit content without error and allows us to troubleshoot better as well. Don't edit any styles, spacing, color, or anything, all of this should have been setup by the design team, so if you need anything changed then ask them.

Everytime you save your working file, Inky will compile the HTML for you. When you are done adding your content and you are pleased with the way it looks, go to the '/dist' folder and find the .html file of the same name…this is the compiled version of your email. It might look crazy but it will work. Copy this code (make sure its from the /dist folder!) and take it to test in Litmus (these templates have already been tested so if you added the content correctly then you shouldn't have to worry about the tests, but always run them), and then to Eloqua to finalize content and send it out.

Refer to [Foundation for Emails](http://foundation.zurb.com/emails/docs/") for help setting up your environment, learn about writing in Inky and general documentation.

Installation instructions [here](/installation.md)

## Foundation for Emails Template

[![devDependency Status](https://david-dm.org/zurb/foundation-emails-template/dev-status.svg)](https://david-dm.org/zurb/foundation-emails-template#info=devDependencies)

**Please open all issues with this template on the main [Foundation for Emails](http://github.com/zurb/foundation-emails/issues) repo.**

This is the official starter project for [Foundation for Emails](http://foundation.zurb.com/emails), a framework for creating responsive HTML devices that work in any email client. It has a Gulp-powered build system with these features:

- Handlebars HTML templates with [Panini](http://github.com/zurb/panini)
- Simplified HTML email syntax with [Inky](http://github.com/zurb/inky)
- Sass compilation
- Image compression
- Built-in BrowserSync server
- Full email inlining process

## Installation

To use this template, your computer needs [Node.js](https://nodejs.org/en/) 0.12 or greater. The template can be installed with the Foundation CLI, or downloaded and set up manually.

### Using the CLI

Install the Foundation CLI with this command:

```bash
npm install foundation-cli --global
```

Use this command to set up a blank Foundation for Emails project:

```bash
foundation new --framework emails
```

The CLI will prompt you to give your project a name. The template will be downloaded into a folder with this name.

### Manual Setup

To manually set up the template, first download it with Git:

```bash
git clone https://github.com/zurb/foundation-emails-template projectname
```

Then open the folder in your command line, and install the needed dependencies:

```bash
cd projectname
npm install
```

## Build Commands

Run `npm start` to kick off the build process. A new browser tab will open with a server pointing to your project files.

Run `npm run build` to inline your CSS into your HTML along with the rest of the build process.

Run `npm run litmus` to build as above, then submit to litmus for testing. *AWS S3 Account details required (config.json)*

Run `npm run mail` to build as above, then send to specified email address for testing. *SMTP server details required (config.json)*

Run `npm run zip` to build as above, then zip HTML and images for easy deployment to email marketing services. 

### Speeding Up Your Build

If you create a lot of emails, your build can start to slow down, as each build rebuilds all of the emails in the
repository. A simple way to keep it fast is to archive emails you no longer need by moving the pages into `src/pages/archive`.
You can also move images that are no longer needed into `src/assets/img/archive`. The build will ignore pages and images that
are inside the archive folder.

## Litmus Tests (config.json)

Testing in Litmus requires the images to be hosted publicly. The provided gulp task handles this by automating hosting to an AWS S3 account. Provide your Litmus and AWS S3 account details in the `example.config.json` and then rename to `config.json`. Litmus config, and `aws.url` are required, however if you follow the [aws-sdk suggestions](http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-configuring.html) you don't need to supply the AWS credentials into this JSON.

```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
  "litmus": {
    "username": "YOUR_LITMUS@EMAIL.com",
    "password": "YOUR_ACCOUNT_PASSWORD",
    "url": "https://YOUR_ACCOUNT.litmus.com",
    "applications": ["ol2003","ol2007","ol2010","ol2011","ol2013","chromegmailnew","chromeyahoo","appmail9","iphone5s","ipad","android4","androidgmailapp"]
  }
}
```

## Manual email tests (config.json)

Similar to the Litmus tests, you can have the emails sent to a specified email address. Just like with the Litmus tests, you will need to provide AWS S3 account details in `config.json`. You will also need to specify to details of an SMTP server. The email address to send to emails to can either by configured in the `package.json` file or added as a parameter like so: `npm run mail -- --to="example.com"`

```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
  "mail": {
    "to": [
      "example@domain.com"
    ],
    "from": "Company name <info@company.com",
    "smtp": {
      "auth": {
        "user": "example@domain.com",
        "pass": "12345678"
      },
      "host": "smtp.domain.com",
      "secureConnection": true,
      "port": 465
    }
  }
}
```

For a full list of Litmus' supported test clients(applications) see their [client list](https://litmus.com/emails/clients.xml).

**Caution:** AWS Service Fees will result, however, are usually very low do to minimal traffic. Use at your own discretion.

