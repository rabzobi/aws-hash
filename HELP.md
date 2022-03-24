#!/bin/bash
# Quick script to upload files to glacier with the calculated checksum
#  Author: Rob
#  Date: 2019/10/30
#

# -- snip --
    HASH=`java TreeHash $UPLOADDIR/$FILE`
    echo "HASH=$HASH"
    aws glacier upload-archive --vault-name $VAULT --account-id - --archive-description $FILE --body $UPLOADDIR/$FILE --checksum $HASH > $LOG
    echo "$FILE uploaded, log in $LOG"
# -- snip --
