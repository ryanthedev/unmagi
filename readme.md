## UNMAGI
*ubuntu nitrogen magi*

### Just a cron job that sets a random bg...magik...


first dumb problem i ran into while doing this was wanting to use nvim as
my default editor while using `crontab -e`

did some googlin and found that you can set an editor env var and 
crontab will r3spect it.

heading into my zshrc i added this export for some nvim butter

```
export EDITOR=nvim
```

now when i execute my trusty crontab command, it loads up this lua
based nerd term.

sweet.  you're welcome future self.

---

ok.  lets actually setup the cron job.

first thing you want to do is RTFM.
```
read the fucking manual
```

check out the man pages for crontab && read the help for nitrogen.
don't be that guy...read the manual.

---

i did run into issues running nitrogen as a cron job.  after some 
searching in google i ran across a god tier nerd who said that 
there was no `DISPLAY` env set when the cron job runs.  so...
yea. printing out the display env

```
env | grep DISPLAY
```
copy pasta that output.  you're gonna need it later.

---

now we are going to actually setup the cronjob. now something to notice is this
`--head=0` && `--head=1`.  these are targeting specific monitors.  i believe there
is a way (maybe X) that will treat the entire thing as a single display.

ok.  drumroll please.

ta...daaaaa...

```
* * * * * export DISPLAY=:1 && /usr/bin/nitrogen --head=1 --random /home/ryan/Pictures/bg --set-auto
* * * * * export DISPLAY=:1 && /usr/bin/nitrogen --head=0 --random /home/ryan/Pictures/bg --set-auto 
```
---
magik.

