# pyobimail
mail library and bot mail development

# Bot Code Example
```
import os
import pyobimail.utils
from pyobimail.client import EmailBot,EmailMessage


def onenteremail(bot:EmailBot=None,message:EmailMessage=None):
    text = message.mail_content

    reply_subject_text = ''
    reply_subject_file = ''

    if '/start' in text:
        print('start comand')
        reply = '👋 DeltaFile2Mail 👋\n\n'
        reply+= 'Bot Para Descargar Archivos Desde Internet Directo A Tu Email,'
        reply+= 'Los Archivos Con Mas De 15mb Se Enviaran En Partes\n\n'
        reply+= 'Como Usar?\n'
        reply+= 'Enviar Cualquier 🔗Link De Descarga🔗'
        message.reply_file(file='logo.png',text=reply,subject=reply_subject_text)
        pass


def main():
    natcli = EmailBot(email='file2mailbot@gmail.com',email_password='qffvrlcnfhhvjvdi',type='gmail.com')
    natcli.smtp_port=587
    natcli.imap_port=993
    loged = natcli.login()
    if loged:
        print('DeltaFile2Mail Runing!')
        natcli.dispatch_receiv_emails(onenteremail=onenteremail)

if __name__ == '__main__':main()
```
