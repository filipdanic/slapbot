# Slapbot

Do you remember that great IRC times when you can just type
```
/slap Josh
```

..and it will slap him real good!

Well why not recreate that joyfull momements again in a modern IRC service Slack!

## Installation

* Clone the repo
* Run `npm install`
* Run `node server.js` 

Ok, great job, but this is not that usefull since you will need to host this somewhere in order to configure Slack to use it.

I recommend running the server with PM2 and frontend it with Nginx or similar. 

PM2 configuration .json should look like this one:
```
{
  "name" : "slapbot",
  "script" : "server.js",
  "cwd" : "<path_to_cloned_repo>",
  "env" :
   {
        "PORT":8090,
   }
}
```

## Configuration

* Go to Slack services section https://<your_slack_team>.slack.com/services/new. 
* From there find Slash Command and add a command like `/slap [username]`. Put in the URL your service url or you can use ours -> `http://slapbot.spfr.co/slap`.

Now you have a working bot with whom you can interact, but it is a private communication between you and him, so you could say that it is not that fun. Let's make it more fun!

* Go to All Integrations screen again and add Incoming Webhook 
* Choose any channel to post to (don't worry, bot will use the channel you type in when you do your slapping)
* Copy and paste tha token part of the URL that you got (it will be something like : `https://hooks.slack.com/services/sadaUSh12/s218jS/ajd123`
* Take the part after `services`, as in the above example it will be -> `/sadaUSh12/s218jS/ajd123`
* Go back to Slash Command and edit the URL to add the token part from above so it should be at the end something like  `http://slapbot.spfr.co/slap?callback=/sadaUSh12/s218jS/ajd123`.

BTW replace `slapbot.spfr.co` with your url, or feel free to use this one.

Congratulations, enjoy slapping!
