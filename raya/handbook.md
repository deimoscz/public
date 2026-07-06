## Glossary:
- Tailscale - secure "your own network"
	- Allows you to connect to other machines in your network as you were on the same wifi
		- Even if you're in a different country
- iTerm2 - a better terminal app
- ZSH - a better terminal shell (first thing you see when you run iTerm)
	- Arrows up/down go through history
		- If you start writing and use arrow up it will show commands you ran before starting on what you already wrote
	- Start writing + tab = autocomplete
	- All setup in .zsrhc (but don't bother with it yet)
- Oh my zsh - beautifuler ZSH
- Tmux - saves terminal sessions when you drop remote connections or close terminal
	- tmux will create a new session
	- tmux a will attach to existing session
	- if you created new session instead of connecting to one, just write exit
	- Prefix command: ctrl + b, then 1-letter command, e.g. ctrl+b c = creates new window
		- c - create new window
		- n - go to the next window
		- w - overview of all sessions and windows (if you're lost)
- SSH - way to secure connect to remote machine
	- e.g. from ipad/iphone to mac-mini and work in mac-mini terminal remotely
	- webssh on ipad/iphone is the app to connect to mac mini from ipad
- Claude
	- superpowers brainstorming
		- 
	- claude rc - runs lasting claude code remote control app that you can use claude with
		- you can use claude app code section - just make sure you choose remote machine when you start session
	- ./.claude/settings.local.json - file in your repo folder to set up claude code work with deepseek (or any other cloud or local models)
		- make sure it's in .gitignore
		- to modify in terminal use 
			- mkdir .claude
			- nano .claude/settings.local.json
			- paste your config there

Flow after mac-mini was off:
- Open terminal
- Run tmux (this will create new session) -- so it survives disconnects and closed terminal
- Add tabs with ctrl+b c
- First tab:
	- Go to your projects folder (documents/claudecode)
	- Run claude rc -- runs claude remote control so you can use it on ipad app
- Second tab: Continue your work

Flow when you connect from ssh or open terminal with mac-mini running tmux (first step will last until it's powered off)
 - Open terminal or connect via ssh (e.g. )
 - Continue your work

Flow for new app:
 - Run claude chat to discuss the idea
 - In the end:
	 - now let's wrap up the idea so i could use it in claude code superpowers brainstorming, bundle whatever I need into a zip file
		 - optionally: tell me if anything is not clear to proceed to claude code
 - move to claude code section 
	 - when creating session make sure you have remote machine
	 - ask it to create a private repo in your github
	 - attach files
	 - write: Let's start superpowers brainstorming session based on attached files
	 - if too technical - let it know that you need some guidance what different options mean, always suggest recommendation and tell me why you recommend it
	 - after brainstorming is done, it will ask you if it can create specs - approve
	 - after specs it asks if it can create plans - approve
	 - after plans it will ask whether you prefer subagent or in-thread development - STOP!
	 - instead ask:
		 - print the prompt i could run sdd implementation in another thread. it should be as autonomous as possible and only stop if it requires explicit answers from me or there is a critical reason for that
	 - it gives you the prompt - better check
 - now back to terminal
	 - create a .claude/settings.local.json and put there configs for deepseek
	 - make sure you updated token (or just copy the file from another folder)
	 - and it should be in gitignore (you can add it using claude)
	 - start claude
		 - rotate shift-tab until it's in auto mode
		 - paste prompt and chill
	 - after it's done, ask for a command to run it:
		 - create a shell script to run and stop the app and give me instruction how to do that and how to access that. make it accessible from all machines in my network
		 - it should give you a command to run
	 - go to the next window in tmux
		 - make sure you're in repo folder and run the command
		 - enjoy or debug
- notes:
	- you can run brainstorming in deepseek (but first save the claude settings with deepseek api)


```json
{
    "env": {
		"ANTHROPIC_BASE_URL": "https://api.deepseek.com/anthropic",  
		"ANTHROPIC_AUTH_TOKEN": "DEEPSEEK_TOKEN",  
		"ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",  
		"ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",  
		"ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro[1m]",  
		"ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash",  
		"CLAUDE_CODE_SUBAGENT_MODEL": "deepseek-v4-pro[1m]",  
		"CLAUDE_CODE_EFFORT_LEVEL": "max" 
    },
    "permissions": {
        "allow": [
            "Bash(npx vitest *)",
            "Bash(npm test *)",
            "Bash(git add *)",
            "Bash(git commit *)",
            "Bash(git merge *)",
            "Bash(git pull *)",
            "Bash(git push *)"
        ]
    }
}
```
