# How-to-create-Email-Module-In-Mendix.

Sending and receiving email is a crucial part of any Application. But you might be thinking how we can achieve this in step by step manner. This module will cover how to Effectively run and set your own template of email module by using Mendix in your application? Let’s start!

# Prerequisites:
Download following :
•	Mendix 9.24.0 version.
•	“email module with templates”
•	Mx Module Reflection
•	Encryption
•	CK editor for mendix

# Mx Module Reflection:
This module is Used for templates features in Email Template which is used to create tokens to include in your template. Also it will modify the data from your database before sending email.
	
# Encryption:
This module is used to encrypt your SMTP password. The password gets decrypt prior to sending email.

# CK editor for mendix:
CK editor is a widget with an extra button that allows you to create microflow even in your HTML output.CK editor comes with CK editor viewer which preview the look for the template you set. You can design buttons and links or just a text using this widget.

# Note:
 As we know that the widget and module are already present in  the marketplace but for Email module there is no proper Step by Step implementation provided. This Documentation will provide implementation with the proper explanation of Email Module in Mendix.

# Implementation of Email Module In mendix:
1.	Create a App Named “EmailTemplateModule” and then rename a Module Name from MyFirstModule to “EmailCustom”
2.	Create a Page EmailAdministration and Select snippet widget and add the Administration Snippet. (from EmailTemplate.Administration)
 ![image](https://user-images.githubusercontent.com/67953305/235627682-509db7d4-5e07-4110-b051-45e09dc07070.png)

3.	Add EmailAdministration Page to your Navigation Tab.
 ![image](https://user-images.githubusercontent.com/67953305/235627619-d16dc4e0-4909-4a18-8495-f71386786a03.png)

4.	Create a Entity in your Domain Module named “EmailInfo” and add a attribute “EmailAddress” of type String.This attribute will be used to create Email template.
 ![image](https://user-images.githubusercontent.com/67953305/235627589-57f5384d-53e6-4b09-b112-9e0a4402e199.png)

5.	Create a microflow “CreateAndSendEmail” to send an Email. No Worry to build from scratch you can duplicate the Microflow from EmailTemplate Module and replace a order parameter with EmailInfo Parameter also Customer parameter with EmailAddress  parameter as shown below:
 ![image](https://user-images.githubusercontent.com/67953305/235627552-12565aeb-7555-4a39-9b4e-98bd26ecbe94.png)

6.	Once you do that you will get an error in the change activity in this microflow. Open the change activity and change the “To” attribute value to your email address parameter.

7.	Finally create a Microflow named “RetrieveTemplateAndSendEmail” as shown below:
 ![image](https://user-images.githubusercontent.com/67953305/235627518-40768ee7-309a-4130-9d81-3927ac382b4e.png)

This microflow is used to retrieve the Email template checks for empty template and atlast calls “CreateAndSendEmail” microflow.
8.	Now this is not Done yet! Run your Project and setup the MxModuleReflection and Encryption.As displayed below
 ![image](https://user-images.githubusercontent.com/67953305/235627481-35acbff6-ac97-4c91-9d62-fcb7564a96e6.png)

9.	Set the MxModuleReflection Overview Page to Navigation.
 ![image](https://user-images.githubusercontent.com/67953305/235627458-da917630-d951-44cd-82fd-2f79657b1047.png)


10.	After that expand the encryption module and set a value for the constant called “EncryptionKey;” this value needs to be a 32-character string.
 ![image](https://user-images.githubusercontent.com/67953305/235627388-f43d00f6-702a-4161-a7d7-9ab6c630c98d.png)

11.	Now you can run your project. Open the MxModuleReflection and Synchronize Entity and Attributes  by Clicking “ClicktoRefresh” button.

12.	Next, navigate to the email administration page and perform the first-time setup. I like to use a Gmail address to send emails with, but you can use any smtp settings.
•	Gmail SMTP server address: smtp.gmail.com
•	Gmail SMTP username: Your full Gmail address (e.g. emailtestingnagarro@gmail.com)
•	Gmail SMTP password: Your Gmail password(to set this password you need to Turn on your Less Secure App from google settings Or alternative for this method is under 2 factor authentication Go in App Password where you will see a generated password copy and paste it here)
•	Gmail SMTP port (TLS): 587
•	Gmail SMTP port (SSL): 465
 ![image](https://user-images.githubusercontent.com/67953305/235627329-d8491dfa-04f9-4054-a6db-5e8217a22788.png)

13.	Once you have entered your credentials, you can click the “next” button and proceed with sending a test email.
14.	Make Sure you turn on the “Allow Less Secure Apps” setting. If you run into this issue, the error that will be returned will be that your password is incorrect.
15.	Now, setup a template with a token, and then send an email from a microflow.

Setting up the Template For Email Module
1.	The first thing you should do is open the “My First Template” example.
 ![image](https://user-images.githubusercontent.com/67953305/235627281-072bd2fe-c136-4d4e-be61-1b0562b8c787.png)

2.	Then scroll to the bottom and find the ‘tokens” section. Here is where you can link an entity and its attributes from your database to your email templates.
 ![image](https://user-images.githubusercontent.com/67953305/235627226-36935c82-1bf4-4877-b502-606ed593d85e.png)

3.	We have used the “EmailInfo” table in the EmailCustom module.
4.	Select object “emailinfo” and then press “new” to create a token for each attribute in your selected object. We have only one attribute “EmailAddress”.
 ![image](https://user-images.githubusercontent.com/67953305/235627190-0c3fa2ab-7b91-4344-b713-a57dc100d7d8.png)

5.	The “token” field would be the name of your token, the “type” would be attribute, and the “attribute” field is where you would select “info.”
6.	Add token to your body now! token would be “{%TestToken%}"in your HTML.
 ![image](https://user-images.githubusercontent.com/67953305/235627147-0a2af6bf-83d6-4d2a-8127-a4522c0572b9.png)

7.	Create a microflow named “SendEmail” as shown below:
![image](https://user-images.githubusercontent.com/67953305/235627061-114b012c-9e13-42ad-a41c-f839252ea7e3.png)

 
Call this microflow on the button onClick Function.This microflow is used to Send Email Successfully.

8.	Next run your application and then press the button that you just added. There will be a popup message if your email was successful, and you should receive an email in your inbox.
![image](https://user-images.githubusercontent.com/67953305/235626819-03ff1c6f-62f7-4f19-84dd-48fc40b32ce1.png)

 
9.	Congrats! You can now Send Email According to your Designed templates.

This was all about the Sending Email From Mendix.






