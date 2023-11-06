# PortfolioDigital
Criação de portfólio digital com Python, Streamlit e CSS

Olá, Buenas? Aqui vou detalhar passo a passo de como realizar um portfólio digital igual ao meu!

BORA CODAR?
#------------------------------------------------ Iniciando o App.py ------------------------------------------------------------#

#AQUI VAMOS COMEÇAR A IMPORTAR AS BIBLIOTECAS

from pathlib import Path
import streamlit as st
from PIL import Image

#--------- Configurações de Localização dos arquivos -------------#

caminho_Atual = Path(__file__).parent if "__file__" in locals () else Path.cwd()

Arq_css = caminho_Atual / "estilos" / "estilo.css"
curriculo = caminho_Atual / "arquivos"/ "Erik Marta Garcia.pdf"
foto = caminho_Atual / "arquivos"/ "ft5.png"

# -----------------CONFIGURAÇÕES GERAIS---------------------- # 
PAGE_TITLE = "Cúrriculo Digital | Erik Marta Garcia"
PAGE_ICON = ":wave"
NAME = "Erik Garcia"
DESCRIPTION = """ Ciêntista de Dados - Ajudando as empresas a tomar decisões com base em fundamentos estatísticos."""
EMAIL = "erik.martaneva@gmail.com"
SOCIAL_MEDIA = {
        "GitHub" : "https://github.com/erikssfd",
        "Medium" : "https://medium.com/@erik.martaneva",
        "LinkedIn" : "https://www.linkedin.com/in/erikmartagarcia/"
}

PROJECTS = {
        "💻 Amazon Dashboard - Comparação de produtos amazon" : "https://github.com/erikssfd/AmzonDashboard",
        "💻 Coursera Dashboard - Comparações de Preços e Avaliações" : "https://github.com/erikssfd/CourseraDashboard"
}

st.set_page_config(page_title = PAGE_TITLE, page_icon = PAGE_ICON)


# ----------------- Carregando CSS, PDF & FOTO DE PERFIL --------------------- #

with open(Arq_css) as f:
    st.markdown("<style>{}</style>".format(f.read()), unsafe_allow_html = True)
    
with open(curriculo, "rb") as curriculo_pdf:
    PDFbyte = curriculo_pdf.read()
    
foto_perfil = Image.open(foto)

# -------------------------- Colunas ------------------------------------------ #

coluna1, coluna2 = st.columns(2, gap = "small")

with coluna1:
    st.image(foto_perfil, width = 230)
    
with coluna2:
    st.title(NAME)
    st.write(DESCRIPTION)
    st.download_button(
        label = "Baixe meu Cúrriculo Aqui ✅",
        data = PDFbyte,
        file_name = curriculo.name,
        mime = "application/octet-stream",
    )
    st.write("📧", EMAIL)

# ---------------------------- Links de Mídias Sociais ------------------------- #

st.write("#")
cols = st.columns(len(SOCIAL_MEDIA))

#Neste for ele está buscando os itens que foram descritos na primeira parte do código#
for index, (platform, link) in enumerate(SOCIAL_MEDIA.items()):
    cols[index].write(f"[{platform}]({link})")

# --------------------------- Experiência e Qualificações ---------------------- #
 
st.write("#")
st.subheader("Experiência & Qualificações")
st.write("""
         - ✔ Experiência 1
         - ✔ Experiência 2
         - ✔ Experiência 3
         - ✔ Experiência 4
         - ✔ Experiência 5
         """)

# --------------------------- Habilidades ------------------------------------- #
st.write("#")
st.subheader("Habilidades")
st.write("""
         - ✔ 💻 Habilidade 1
         - ✔ 💻 Habilidade 2
         - ✔ 📊 Habilidade 3
         - ✔ 🔍 Habilidade 4
         - ✔ 📋 Habilidade 5
         - ✔ 🎲 Habilidade 6
         - ✔ ♟ Habilidade 7
         """)

# --------------------------- Histórico de Trabalho ---------------------------- #
st.write("#")
st.subheader("Histórico de Trabalho")
st.write("-----")
 
 
st.write("Coloque um ícone", "** Nome do seu Cargo | Nome da Empresa **")
st.write("(01/2023) - (08/2023)")
st.write("""
         - Primeiro feito no emprego;
         - Segundo feito no emprego;
         - Terceiro feito no emprego.
         """)

# --------------------------- Projetos & Conquistas ---------------------------- #
st.write("#")
st.subheader("Projetos e Conquistas")
st.write("-----")


#Neste for ele está buscando os itens que foram descritos na primeira parte do código#
for project, link in PROJECTS.items():
    st.write(f"[{project}]({link})")
