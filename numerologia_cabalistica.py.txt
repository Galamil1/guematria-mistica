import streamlit as st

guematria = {
    'א': 1, 'ב': 2, 'ג': 3, 'ד': 4, 'ה': 5,
    'ו': 6, 'ז': 7, 'ח': 8, 'ט': 9, 'י': 10,
    'כ': 20, 'ך': 20, 'ל': 30, 'מ': 40, 'ם': 40,
    'נ': 50, 'ן': 50, 'ס': 60, 'ע': 70, 'פ': 80,
    'ף': 80, 'צ': 90, 'ץ': 90, 'ק': 100, 'ר': 200,
    'ש': 300, 'ת': 400
}

def reducir_numero(n):
    while n >= 10:
        n = sum(int(d) for d in str(n))
    return n

def interpretar_numero(n):
    interpretaciones = {
        1: "Unidad, inicio, Dios.",
        2: "Dualidad, polaridad, unión.",
        3: "Expansión, creación, expresión.",
        4: "Fundamento, estabilidad.",
        5: "Movimiento, cambio, libertad.",
        6: "Armonía, belleza.",
        7: "Misticismo, introspección.",
        8: "Poder, realización.",
        9: "Sabiduría, finalización."
    }
    return interpretaciones.get(n, "Desconocido")

st.set_page_config(page_title="Guematria Mística", page_icon="🕯️")

st.title("🔢 Guematria Mística")
st.markdown("Introduce una palabra en hebreo para analizarla según la **guematria cabalística**.")

palabra = st.text_input("✍️ Palabra en hebreo:")

if palabra:
    st.markdown("## 📖 Análisis letra por letra:")
    total = 0
    for letra in palabra:
        valor = guematria.get(letra, 0)
        st.write(f"{letra} = {valor}")
        total += valor

    reduccion = reducir_numero(total)

    st.markdown("---")
    st.markdown(f"### 🔢 Valor total: `{total}`")
    st.markdown(f"### ✨ Reducción teosófica: `{reduccion}`")
    st.markdown(f"### 🧠 Interpretación simbólica: *{interpretar_numero(reduccion)}*")
