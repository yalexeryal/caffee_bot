# caffee_bot

Команды пользователя убраны, так как в дальнейшем не понадобятся. Чтоб убрать кнопку меню с ними в вашем боте 
- раскоментируйте на один запуск эти строки в app.py:
""async def main():
    dp.startup.register(on_startup)
    dp.shutdown.register(on_shutdown)

    dp.update.middleware(DataBaseSession(session_pool=session_maker))

    await bot.delete_webhook(drop_pending_updates=True)
    
    ## await bot.delete_my_commands(scope=types.BotCommandScopeAllPrivateChats())    <-ЭТУ
    await bot.set_my_commands(commands=private, scope=types.BotCommandScopeAllPrivateChats())
    await dp.start_polling(bot, allowed_updates=dp.resolve_used_update_types())""

- При запуске этого бота в !первый раз - удалить старые таблицы (нужно раскоментировать на !первый запуск эту строчку кода в файле app.py:
  async def on_startup(bot):
  
  ## await drop_db()  <-ЭТУ

    await create_db()