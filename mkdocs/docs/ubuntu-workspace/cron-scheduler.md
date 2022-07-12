# Schedule jobs with cron

The cron command-line utility is a job scheduler on Unix-like operating systems. Users who set up and maintain software environments 
use cron to schedule jobs, also known as cron jobs, to run periodically at fixed times, dates, or intervals.

You can schedule execution of any task with cron. Create cron task with

```
crontab -e
```

*(chose [1] nano as editor)*
Go to the end of the opened file, and add the next line  

> `* * * * * echo $(whoami) >> /home/cron.txt`

This will print every minute username to file */home/cron.txt* .  
Hit Ctrl+X to exit nano editor.  

In a minute you can chech if the file `/home/cron.txt` is updated. 

Cron has very flexible scheduler, you can chose different times at which you job should run.  

> ```
> Hint: example of cron job definition:   
> .---------------- minute (0 - 59)   
> |  .------------- hour (0 - 23)
> |  |  .---------- day of month (1 - 31)
> |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
> |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
> |  |  |  |  |
> *  *  *  *  *  command to be executed
> ```

**NOTE** you can disconnect from the image and close terminal. cron will continue working.