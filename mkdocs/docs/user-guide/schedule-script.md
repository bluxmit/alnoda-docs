This tutorial shows how to scrap Google news on schedule. We use Python for the demonstration purpose.   

To start, open workspace terminal and install Python package GNews

```
pip install gnews
```

Create python script 

```
nano scraper.py
```

Paste the following code snippet. This is scrapper, that will output results to a file

```py
from gnews import GNews
import json

google_news = GNews()
usa_news = google_news.get_news('USA')
with open('usa_news.json', 'w') as f:
    json.dump(usa_news, f)
```

Save the file with `Ctrl+s` and return to the terminal with `Ctrl+x`.  

Execute the script 

```
python3 scraper.py
```

Navigate to Quickstart and Open file browser. View and download the output file 

![Filebrowser](img/filebrowser-demo.gif)

Schedule daily executions with Cronicle

![Cronicle](img/cronicle-demo.gif)

## Cron 

**Note:** you can also use cron scheduler to schedule executions of your tasks and jobs. Cron is pure terminal-based 
application. It is well-known and a greatly adopted tool. Check out [this tutorial](../ubuntu-workspace/cron-scheduler.md) to learn how 
you can use cron in the workspace.
