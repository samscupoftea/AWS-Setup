# AWS-Setup
AWS Setup Guide 


* 	Update Your System:
* 		Update your system packages to ensure everything is up to date. This is a good practice before installing new software. bash  Copy code sudo yum update -y   
* 		Install Node.js and npm:
* 		Install Node.js and npm, which are required to run your Discord bot. Amazon Linux might have these in its repositories. bash  Copy code sudo yum install nodejs npm -y   
* 		Install Git (if not already installed):
* 		Git is required to clone your repository. bash  Copy code sudo yum install git -y   
* 		Clone Your Discord Bot Repository:
* 		Use Git to clone your Discord bot repository. Replace https://your-repository-url.git with the actual URL of your repository. bash  Copy code git clone https://your-repository-url.git    This will create a directory with your bot's code in it.
* 		Navigate to Your Bot's Directory:
* 		Change into the directory that was created when you cloned your repository. bash  Copy code cd name-of-your-bot-directory    Replace name-of-your-bot-directory with the actual directory name.
* 		Install Bot Dependencies:
* 		Install the necessary Node.js packages specified in your bot's package.json. bash  Copy code npm install   
* 		Configure Environment Variables:
* 		If your bot requires environment variables (like a bot token), set them up. You might want to use a .env file or directly export them in the shell.
* 		Run Your Bot:
* 		Start your Discord bot using Node.js. The command will depend on your bot's entry file (commonly index.js or bot.js). bash  Copy code node your-bot-main-file.js    Replace your-bot-main-file.js with the name of your bot's main file.
* 		Ensure Long-Term Running:
* 		To keep your bot running after you exit the SSH session, consider using a process manager like pm2. bash  Copy code sudo npm install pm2 -g pm2 start your-bot-main-file.js pm2 save pm2 startup    Replace your-bot-main-file.js with your bot's main file name. This will keep your bot running in the background.


When you're deploying a Discord bot or any application to a server like an EC2 instance, and it relies on environment variables (like API keys) stored in a .env file, you need to ensure those variables are correctly set up on the server. Since the .env file is typically not included in version control for security reasons, you won't have it automatically when you clone the repository. Here's how you can set it up:
* 		Create the .env File on Your EC2 Instance:
    * Navigate to your bot's directory (if you're not already there).
    * Use a text editor to create a .env file. You can use nano, vi, or any other editor available on your system. For example:bash  Copy code nano .env   
    * In the .env file, add your environment variables in the format VARIABLE_NAME=value. For example:makefile  Copy code DISCORD_BOT_TOKEN=your_bot_token_here    Replace your_bot_token_here with your actual bot token.
* 		Save the File:
    * In nano, you can save the file by pressing Ctrl + O, then Enter, and exit with Ctrl + X.
    * In vi, you can save and exit by pressing Esc, typing :wq, and then pressing Enter.
* 		Load the Environment Variables:
    * Before running your bot, make sure your application loads the environment variables from the .env file.
    * If your bot is written in Node.js and you are using a package like dotenv, it should automatically load the variables when you start your bot, as long as the .env file is in the root directory of your project.javascript  Copy code require('dotenv').config();    This line is typically placed at the top of your main bot file.
* 		Run Your Bot:
    * Start your bot as you usually would. For example:bash  Copy code node your-bot-main-file.js 


