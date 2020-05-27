# How to send e-mails using Python

It can be useful for notifying the end of a simulation

Source: <https://realpython.com/python-send-email/>

1. Create google account and turn *Allow less secure apps to ON*.
   **Do not use your own account**

2. Example of script that uses the account to send e-mails. No need
   to install libraries.

   ```python
   import smtplib, ssl

   port = 465
   e-mail = 'notify.abcpy@gmail.com'
   password = 'XXX'  # TODO

   receiver = 'XXX@XXX'  # TODO
   message = 'Test'

   with smtplib.SMTP_SSL('smtp.gmail.com', port, context=context) as server:
       server.login(e-mail, password)
       server.sendmail(e-mail, receiver, message)
   ```