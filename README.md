from aiogram import Bot, Dispatcher, executor, types
import random

TOKEN = "5596751604:AAE-kA_Mvso9liG6hqmxmL3JxhyjazfqPuY"
bot = Bot(token=TOKEN, parse_mode='html')
dp = Dispatcher(bot=bot)

tpl = ("π", "π€", "β")

keyb = types.ReplyKeyboardMarkup(resize_keyboard=True)
button1 = types.KeyboardButton(text="π")
button2 = types.KeyboardButton(text="π€")
button3 = types.KeyboardButton(text="β")
keyb.add(button1, button2, button3)


@dp.message_handler(commands="start")
async def start(message: types.Message):
    print(message.from_user.id)
    await message.answer("Hi", reply_markup=keyb)


@dp.message_handler(text="π")
async def stone(message: types.Message):
    global tpl
    random_emo = tpl[random.randint(0, 2)]
    await message.reply(random_emo)
    if random_emo == "π":
        await message.answer("ΠΡΡΠΈΡ")
    elif random_emo == "β":
        await message.answer("you WINπ")
    else:
        await message.answer("you LOSEπ")


@dp.message_handler(text="β")
async def nosh(message: types.Message):
    global tpl
    random_emo = tpl[random.randint(0, 2)]
    await message.reply(random_emo)
    if random_emo == "β":
        await message.answer("ΠΡΡΠΈΡ")
    elif random_emo == "π":
        await message.answer("you LOSEπ")
    else:
        await message.answer("you WINπ")


@dp.message_handler(text="π€")
async def papir(message: types.Message):
    global tpl
    random_emo = tpl[random.randint(0, 2)]
    await message.reply(random_emo)
    if random_emo == "π€":
        await message.answer("ΠΡΡΠΈΡ")
    elif random_emo == "π":
        await message.answer("you WINπ")
    else:
        await message.answer("you LOSEπ")


if __name__ == '__main__':
    executor.start_polling(dp, skip_updates=True)
