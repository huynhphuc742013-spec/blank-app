import streamlit as st
import random

st.title("🎮 Trò Chơi Oản Tù Tì")

# Biểu tượng cảm xúc minh họa
emoji_map = {
    "Búa": "✊ Búa",
    "Kéo": "✌️ Kéo",
    "Bao": "✋ Bao"
}

choices = ["Búa", "Kéo", "Bao"]

# Tạo 3 cột tương ứng với 3 nút bấm
col1, col2, col3 = st.columns(3)

user_choice = None
if col1.button("✊ Búa"):
    user_choice = "Búa"
if col2.button("✌️ Kéo"):
    user_choice = "Kéo"
if col3.button("✋ Bao"):
    user_choice = "Bao"

# Xử lý khi người dùng bấm chọn
if user_choice:
    computer_choice = random.choice(choices)

    st.write(f"**Bạn chọn:** {emoji_map[user_choice]}")
    st.write(f"**Máy tính chọn:** {emoji_map[computer_choice]}")

    st.markdown("---")

    # So sánh kết quả
    if user_choice == computer_choice:
        st.warning("🤝 Kết quả: Hòa nhau!")
    elif (user_choice == "Búa" and computer_choice == "Kéo") or \
         (user_choice == "Kéo" and computer_choice == "Bao") or \
         (user_choice == "Bao" and computer_choice == "Búa"):
        st.success("🎉 Kết quả: Bạn đã chiến thắng!")
        st.balloons()  # Bắn bóng bay mừng chiến thắng
    else:
        st.error("🤖 Kết quả: Máy tính thắng rồi!")
