# aws-hash

Calculate Hash needed to store file in AWS glacier

tar zcf $UPLOADDIR/$FILE $F
HASH=`java TreeHash $UPLOADDIR/$FILE`
echo "HASH=$HASH"
aws glacier upload-archive --vault-name $VAULT --account-id - --archive-description $FILE --body $UPLOADDIR/$FILE --checksum $HASH > $LOG
echo "$FILE uploaded, log in $LOG"
