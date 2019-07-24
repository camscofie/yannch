---
layout: post
title: Rocket Chat Files download
category: gists
description: python auto download
---

```py

import json
import requests
from pathlib import Path

"""
╭──────────────────────────────────────────────╮
│ ◎ ○ ○ ░░░░░░░░░░░░  Usage  ░░░░░░░░░░░░░░░░░░│
├──────────────────────────────────────────────┤
│                                              │
│ This gist is to download all the files from  │
│        the Rocket Chat chat-history.         │
│                                              │
│    Only modify the following when needed:    │
│                                              │
│                                              │
│                   baseUrl;                   │
│desPath(where you want to download files to); │
│      chatPath(where are the chat files);     │
│                X-Auth-Token;                 │
│                  X-User-Id.                  │
│                                              │
├──────────────────────────────────────────────┤
└──────────────────────────────────────────────┘
"""

baseUrl = "https://xxxxxxxxxxxxxxx.chat"


desPath = "/xxxxxxxxxxxxxxx/"
chatPath = "/xxxxxxxxxxxxxxx/"

headers = {
    'X-Auth-Token': 'xxxxxxxxxxxxxxx',
    'X-User-Id': 'xxxxxxxxxxxxxxx',
}




#################################################################
#################################################################


# iterate through files in directory
pathlist = Path(chatPath).glob('*.json')
for file in pathlist:
    filename = str(file)
    # read file
    with open(filename, 'r') as myfile:
        data = myfile.read()
    # parse file
    obj = json.loads(data)
    # iterate messages in json
    for file in obj["messages"]:
        if "attachments" in file:
            for attachment in file["attachments"]:
                if 'title' in attachment:
                    print(attachment["title"])
                    print(attachment["title_link"])
                    response = requests.get(baseUrl + attachment["title_link"], headers=headers)
                    with open(desPath+attachment["title"], 'wb') as f:
                        f.write(response.content)

```

[Yange]:    http://camscofie.github.io  "Yange"
[1]:    {{ page.url}}  ({{ page.title }})
