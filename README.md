import os
from telegram import Update
from telegram.ext import ApplicationBuilder, MessageHandler, ContextTypes, filters
import datetime

# Token Railway se aayega
TOKEN = os.getenv("BOT_TOKEN")

async def jarvis(update: Update, context: ContextTypes.DEFAULT_TYPE):
    text = update.message.text.lower()

    if text in ["hi", "hello", "namaste"]:
        await update.message.reply_text("🤖 Namaste Avish! Main Jarvis hoon.")

    elif "time" in text:
        now = datetime.datetime.now().strftime("%H:%M")
        await update.message.reply_text(f"⏰ Abhi samay hai {now}")

    else:
        await update.message.reply_text("Main abhi seekh raha hoon 😄")

app = ApplicationBuilder().token(TOKEN).build()
app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, jarvis))

print("Jarvis 24x7 online hai...")
app.run_polling()# jarvis-telegram-bot
