import openai
from telegram import Update
from telegram.ext import ApplicationBuilder, MessageHandler, filters, ContextTypes

# API keys
TELEGRAM_TOKEN = "8344010103:AAFRJHcm1BfI3TEWf4emhN9_y3AE8O1YaL0"
OPENAI_API_KEY = "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"

openai.api_key = OPENAI_API_KEY

async def reply(update: Update, context: ContextTypes.DEFAULT_TYPE):
    user_message = update.message.text

    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",
        messages=[{"role": "user", "content": user_message}]
    )

    bot_reply = response["choices"][0]["message"]["content"]

    await update.message.reply_text(bot_reply)

app = ApplicationBuilder().token(TELEGRAM_TOKEN).build()

app.add_handler(MessageHandler(filters.TEXT & ~filters.COMMAND, reply))

app.run_polling()
