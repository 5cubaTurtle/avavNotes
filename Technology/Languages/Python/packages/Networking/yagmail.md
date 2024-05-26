#python 
[guide](https://curatedpython.com/p/yagmail-kootenpv-yagmail/index.html)
`import yagmail`
create SMTP mailer:
```python
yag = yagmail.SMTP("yourEmail@domain.com", oauth2_file='path/to/token.json')
```
- to get a *token.json* follow [these instructions](https://blog.macuyiko.com/post/2016/how-to-send-html-mails-with-oauth2-and-gmail-in-python.html)
send an email:
```python
yag.send(to=["john@gmail.com", "jane@yahoo.com"], subject="subject", contents="body")
```
