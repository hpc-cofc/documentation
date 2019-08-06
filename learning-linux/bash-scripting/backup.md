# Script: Backup

```bash
#!/bin/bash

SRC_DIR="/home/$USER/Documents/my_work/"

DEST_DIR="/home/$USER/Backups/"

FILENAME=Backup-$(date +%-Y%-m%-d)-$(date +%-T).tgz

tar --create --gzip --file=$DEST_DIR$FILENAME $SRC_DIR
```

Back to [Essential Commands](./)

