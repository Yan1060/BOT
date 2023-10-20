# BOT
from telegram import Update
from telegram.ext import Updater, CallbackContext, Dispatcher, Filters, MessageHandler

TOKEN = ''


class MessageHand:
    pass


def main(do_echo=None):
    updater = Updater(token=TOKEN)
    dispatcher: Dispatcher = updater.dispatcher
    echo_handler = MessageHandler(Filters.test, do_echo)
    dispatcher.add_handler(echo_handler)


def echo(update: Update, context: CallbackContext):
    user_id = update.message.from_user.id
    username = update.message.from_user.username
    text = update.message.text

    print(f'{username} {user_id} вызвал функцию echo')
    answer = f"Твой {user_id=}\nТвой {username=}\n {text}"

    update.message.reply_text(answer)

