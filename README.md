import discord
from discord.ext import commands
import random

intents = discord.Intents.default()
intents.members = True
intents.message_content = True

bot = commands.Bot(command_prefix="#", intents=intents)

@bot.event
async def on_ready():
    print(f"Has iniciado sesión como: {bot.user} (ID: {bot.user.id})")

@bot.command()
async def hola(ctx):
    await ctx.send("Hola, en qué puedo ayudarte hoy?")

@bot.command()
async def ayuda(ctx):
    await ctx.send("Comandos disponibles: \n #hola \n #ayuda \n #reciclaje \n #info \n #consejo \n #que_reciclar \n #ecologia \n #manualidades")

@bot.command()
async def reciclaje(ctx):
    await ctx.send("El reciclaje es importante para el medio ambiente. Ayuda a reducir la cantidad de residuos y a conservar recursos naturales.")

@bot.command()
async def consejo(ctx):
    consejos = [
        "Apaga las luces cuando salgas de una habitación.",
        "Usa bolsas reutilizables en lugar de bolsas de plástico.",
        "Reduce el uso de agua al ducharte y al lavar los platos.",
        "Recicla el papel, plástico y vidrio siempre que sea posible.",
        "Planta un árbol o cuida de las plantas en tu área."
    ]
    await ctx.send(random.choice(consejos))

@bot.command()
async def que_reciclar(ctx):
    reciclables = "Puedes reciclar: \n- Papel y cartón \n- Plástico (botellas, envases) \n- Vidrio (botellas, frascos) \n- Metales (latas de aluminio, latas de acero)"
    no_reciclables = "No se deben reciclar: \n- Plásticos no etiquetados como reciclables \n- Comida o residuos orgánicos \n- Cartón sucio o húmedo \n- Plásticos de un solo uso (como bolsas de supermercado)"
    await ctx.send(f"{reciclables}\n\n{no_reciclables}")

@bot.command()
async def info(ctx):
    with open('imagenes/info.webp', 'rb') as f:
        picture = discord.File(f)
    await ctx.send(file=picture)

@bot.command()
async def ecologia(ctx):
    concepto = (
        "La ecología es la ciencia que estudia las interacciones entre los organismos y su entorno. "
        "Es fundamental para entender cómo nuestras acciones afectan el medio ambiente y cómo podemos "
        "vivir de manera más sostenible."
    )
    await ctx.send(concepto)

@bot.command()
async def manualidades(ctx):
    ejemplos = (
        "Aquí tienes algunas ideas de manualidades con material reciclado:\n"
        "- Hacer macetas con botellas de plástico.\n"
        "- Crear un organizador de escritorio con cajas de cartón.\n"
        "- Hacer adornos navideños con papel reciclado.\n"
        "- Crear juguetes para mascotas con rollos de papel higiénico.\n"
        "- Hacer bolsas reutilizables con camisetas viejas."
    )
    await ctx.send(ejemplos)

@bot.command()
async def beneficios_reciclaje(ctx):
    beneficios = (
        "Beneficios de reciclar:\n"
        "- Reduce la cantidad de residuos en vertederos.\n"
        "- Conserva recursos naturales y energía.\n"
        "- Disminuye la contaminación del aire y el agua.\n"
        "- Fomenta la economía circular y la creación de empleos.\n"
        "- Ayuda a combatir el cambio climático."
    )
    await ctx.send(beneficios)

bot.run("TU_TOKEN_AQUI")  # Reemplaza 'TU_TOKEN_AQUI' con tu token real# Ambiente
