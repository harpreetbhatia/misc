## UNIX commands
some common UNIX commands

**1. To go to a remote shell**
```bash
ssh /path/to/server/
```
To come out of ssh:

` ↵`
```bash
~.
```

**2. move word-by-word on command line**

`Home` , or  `Ctrl-A`
`End` ,
`Esc-B` ,and
 `Esc-F`  (NOT `Esc-W`).


**3. delete word-by-word on command line**

`Esc-d` 


**4. delete the entire command line **

`Ctrl+F+W`   (The cursor should be at the end of the command line)
`Ctrl+U` deletes everything to the left of cursor
`Ctr+K` deletes everything to the right of cursor


**5. To find what machine (server) I am running on**
```bash
uname -n
```

**6. To find a file:**

The general form of **find** command is:
 find (starting directory) (matching criteria and actions)
```bash
find . -name "regex" -print
```

**7. Send email from the command line**

Perl files cannot be sent. You need to convert to txt files first.
```bash
echo "Sending an attachment." | mutt c_hbhati@qca.qualcomm.com -a backup.zip -s "attachment" 
echo "Sending an attachment." | mutt  $USER -a backup.zip -s "attachment" 
```
or ..
use `sendmail`: 

If the mail text in the form of a **file**, sendmail  will send the text into the message.
```bash
`sendmail c_hbhati@qca.qualcomm.com < email.txt
```

**8. Create a soft link**
```bash
 ln -s existing_file linkname
```

**10. To split a file into section  of files according to regex**
```bash
csplit -s --prefix=logfile  logfileA  '/^From.*/' '{96}' // put any high number
rm logfile00                                             // empty file, i.e. everything uptill the first pattern
```

Advanced options:
```bash
csplit -s --prefix=logfile  logfileA  '/^From.*/' '{96}' -z // removes empty files
csplit -s --prefix=logfile  logfileA  '/^From.*/' '{96}' -z --digits=1 // no 00,01 etc.
```

**11. To split a file into section  of files according to size**
```bash
split --help
```

**12. Cron**

Usage:
```bash
crontab [-u user] file
crontab [-u user] [ -e | -l | -r ]
```
`crontab -e` Edit your crontab file, or create one if it doesn't already exist.

`crontab -l` Display your crontab file.

`crontab -r` Remove your crontab file.

The crontab file should end with an empty line.

**crontab entry**
```bash
m h dom mon dow command
* * * * * command
```

min (0 - 59)

hour (0 - 23)

day of month (1 - 31)

month (1 - 12)

day of week (0 - 6) (Sunday=0)

**To Generate log file:**
```bash
30 18 *** /home/someuser/tmp > /home/someuser/cronlogs/clean_tmp_dir.log
```
**To set the PATH variable**
```bash
PATH=/opt/someApp/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

**To find if cron is running**
```bash
pgrep cron
```
If you don't see a number, then cron is not running

**cron.daily**
The script file-names in cron.d/, cron.daily/, cron.hourly/, etc., should not contain dot(.), otherwise run-parts will skip them.
So, if you have a cron script backup.sh, analyze-logs.pl in cron.daily/ directory, you'd best to remove the extension names.

**To copy files from one machine to another** (SCL to GBC):
```bash
scp c_hbhati@vl-c-hbhati-scl:~/<filename> ~/
```
