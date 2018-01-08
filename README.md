
# Architizer Email Builder

This kit will allow Architizer designers, engineers and marketers to generate the HTML for our emails in a controlled and consistent mannerthe need to worry about crazy email HTML table structures and browser consistency. The design team will build templates that "just work" and drop them here for you to build without having to worry about styling at all…just get the content in there.

To use the kit, you first need to download and run the kit. To build an email, open the template example from the 'src/pages' folder in your text editor and replace the placeholder content and links with the new content. You'll notice no tables or any crazy HTML. That's because these are written in a compiler called Inky, which compiles the finished email to the appropriate HTML. Using Inky allows us to read the code more clearly so we can see exactly where to add and edit content without error and allows us to troubleshoot better as well. Don't edit any styles, spacing, color, or anything, all of this should have been setup by the design team, so if you need anything changed then ask them.

Everytime you save your working file, Inky will compile the HTML for you. When you are done adding your content and you are pleased with the way it looks, go to the '/dist' folder and find the .html file of the same name…this is the compiled version of your email. It might look crazy but it will work. Copy this code (make sure its from the /dist folder!) and take it to test in Litmus (these templates have already been tested so if you added the content correctly then you shouldn't have to worry about the tests, but always run them), and then to Eloqua to finalize content and send it out.

Refer to [Foundation for Emails](http://foundation.zurb.com/emails/docs/") for help setting up your environment, learn about writing in Inky and general documentation.

Installation instructions [here](/installation.md)