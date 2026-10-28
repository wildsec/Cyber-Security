## SMTP
The SMTP server listens on TCP port 25 by default.
ome of the commands used by your mail client when it transfers an email to an SMTP server:

- `HELO` or `EHLO` initiates an SMTP session
- `MAIL FROM` specifies the sender’s email address
- `RCPT TO` specifies the recipient’s email address
- `DATA` indicates that the client will begin sending the content of the email message
- `.` is sent on a line by itself to indicate the end of the email message

## POP3
POP3 server listens on TCP port 110 by default
 email client sends its messages by relying on SMTP and retrieves them using POP3.
 Some common POP3 commands are:

- `USER <username>` identifies the user
- `PASS <password>` provides the user’s password
- `STAT` requests the number of messages and total size
- `LIST` lists all messages and their sizes
- `RETR <message_number>` retrieves the specified message
- `DELE <message_number>` marks a message for deletion
- `QUIT` ends the POP3 session applying changes, such as deletions

## IMAP
The IMAP protocol commands are more complicated than the POP3 protocol commands. We list a few examples below:

- `LOGIN <username> <password>` authenticates the user
- `SELECT <mailbox>` selects the mailbox folder to work with
- `FETCH <mail_number> <data_item_name>` Example `fetch 3 body[]` to fetch message number 3, header and body.
- `MOVE <sequence_set> <mailbox>` moves the specified messages to another mailbox
- `COPY <sequence_set> <data_item_name>` copies the specified messages to another mailbox
- `LOGOUT` logs out

Knowing that the IMAP server listens on TCP port 143 by default

## Security

The insecure versions use the default TCP port numbers shown in the table below:

|Protocol|Default Port Number|
|---|---|
|HTTP|80|
|SMTP|25|
|POP3|110|
|IMAP|143|

The secure versions, i.e., over TLS, use the following TCP port numbers by default:

|Protocol|Default Port Number|
|---|---|
|HTTPS|443|
|SMTPS|465 and 587|
|POP3S|995|
|IMAPS|993|