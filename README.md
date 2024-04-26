- 👋 Hi, I’m @Cleitinho1
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
from telegram.ext import Updater, MessageHandler, Filters

# Função para responder mensagens
def responder_mensagem(update, context):
    # Obtém o objeto de mensagem do update
    message = update.message
    # Obtém o texto da mensagem
    text = message.text
    # Responde com uma mensagem pré-definida
    message.reply_text("Olá! Eu sou o seu bot. Você disse: {}".format(text))

def main():
    # Substitua "TOKEN_DO_SEU_BOT" pelo seu token de acesso
    token = "7194498887:AAGjbUB1OqWfY3Qus7tbGNsWsPL0URF9BfE"
    # Cria um updater passando o token do seu bot
    updater = Updater(token, use_context=True)

    # Obtém o despachante para registrar handlers
    dispatcher = updater.dispatcher

    # Cria um handler para responder mensagens de texto
    mensagem_handler = MessageHandler(Filters.text & ~Filters.command, responder_mensagem)

    # Registra o handler no despachante
    dispatcher.add_handler(mensagem_handler)

    # Inicia o bot
    updater.start_polling()

    # Mantém o bot em execução até que Ctrl+C seja pressionado
    updater.idle()

if __name__ == "__main__":
    main()
