# 📘 Streamlit – Simple English Notes (Chai aur Streamlit)

These notes convert the full Hindi tutorial into **simple, clear English**, with **important ideas + minimal code snippets** wherever needed.

---

## 1️⃣ Why Streamlit?

### Problem

* Many Python developers are **not comfortable with HTML, CSS, JS**
* They want to give **UI to Python scripts** (Data Science, RAG, GenAI apps)

### Solution → Streamlit

* Build **web apps using only Python**
* No HTML / CSS / JS required
* Very fast to build & share

👉 Best for:

* Data Science apps
* RAG & GenAI demos
* Dashboards
* Internal tools

---

## 2️⃣ What is Streamlit?

> Streamlit is a **Python-first framework** to turn scripts into **interactive web apps**.

Key points:

* Runs on **pure Python**
* Uses **declarative style** (you declare what you want)
* Automatic UI refresh

---

## 3️⃣ Project Setup (Using UV or pip)

### Create project

```bash
uv init chai-stream
cd chai-stream
```

### Install Streamlit

```bash
uv add streamlit
# OR
pip install streamlit
```

### Run app

```bash
streamlit run main.py
```

---

## 4️⃣ First Streamlit App (Hello Chai)

```python
import streamlit as st

st.title("☕ Hello Chai App")
st.subheader("Brewed with Streamlit")
st.text("Welcome to your first interactive app")
st.write("Choose your favorite tea")
```

---

## 5️⃣ Dropdown (Selectbox)

```python
tea = st.selectbox(
    "Your favorite tea:",
    ["Masala Chai", "Lemon Tea", "Ginger Tea", "Saffron Tea"]
)

st.write(f"You chose {tea}. Excellent choice!")
```

---

## 6️⃣ Buttons & Conditions

```python
if st.button("Make Tea"):
    st.success("Your tea is being brewed ☕")
```

---

## 7️⃣ Checkboxes

```python
add_masala = st.checkbox("Add Masala")

if add_masala:
    st.write("Masala added to your tea")
```

---

## 8️⃣ Radio Buttons

```python
base = st.radio(
    "Pick tea base:",
    ["Milk", "Water", "Almond Milk"]
)

st.write("Selected base:", base)
```

---

## 9️⃣ Sliders

```python
sugar = st.slider("Sugar level (spoons)", 0, 5, 2)
st.write("Sugar spoons:", sugar)
```

---

## 🔟 Number Input

```python
cups = st.number_input(
    "How many cups?",
    min_value=1,
    max_value=10,
    step=1
)
```

---

## 1️⃣1️⃣ Text Input

```python
name = st.text_input("Enter your name")

if name:
    st.write(f"Welcome {name}, your tea is on the way ☕")
```

---

## 1️⃣2️⃣ Date Input

```python
dob = st.date_input("Select your date of birth")
st.write("Your DOB:", dob)
```

---

## 1️⃣3️⃣ Columns (Layouts)

```python
col1, col2 = st.columns(2)

with col1:
    st.header("Masala Tea")
    if st.button("Vote Masala"):
        st.success("Thanks for voting Masala Tea")

with col2:
    st.header("Ginger Tea")
    if st.button("Vote Ginger"):
        st.success("Thanks for voting Ginger Tea")
```

---

## 1️⃣4️⃣ Images

```python
st.image(
    "https://images.pexels.com/photos/1417945/pexels-photo-1417945.jpeg",
    width=200
)
```

---

## 1️⃣5️⃣ Sidebar

```python
name = st.sidebar.text_input("Enter your name")
tea = st.sidebar.selectbox(
    "Choose your tea",
    ["Masala", "Ginger", "Saffron"]
)

st.write(f"{name}'s {tea} tea is getting ready ☕")
```

---

## 1️⃣6️⃣ Expander

```python
with st.expander("Show tea making steps"):
    st.write("""
    1. Boil water with tea leaves
    2. Add milk & spices
    3. Serve hot
    """)
```

---

## 1️⃣7️⃣ Markdown

````python
st.markdown("""
## ☕ Welcome to Chai App
> Best tea is freshly brewed

```python
print("Enjoy your tea")
````

""")

````

---

## 1️⃣8️⃣ File Upload + Pandas

```python
import pandas as pd

file = st.file_uploader("Upload CSV", type=["csv"])

if file:
    df = pd.read_csv(file)
    st.subheader("Data Preview")
    st.dataframe(df)

    st.subheader("Summary Stats")
    st.write(df.describe())
````

---

## 1️⃣9️⃣ Filter Data using Selectbox

```python
city = st.selectbox("Filter by city", df['City'].unique())
filtered_df = df[df['City'] == city]
st.dataframe(filtered_df)
```

---

## 2️⃣0️⃣ API Call Example (Currency Converter)

```python
import requests

amount = st.number_input("Amount in INR", min_value=1)
target = st.selectbox("Convert to", ["USD", "EUR", "GBP"])

if st.button("Convert"):
    res = requests.get("https://api.exchangerate-api.com/v4/latest/INR")
    if res.status_code == 200:
        rate = res.json()['rates'][target]
        converted = amount * rate
        st.success(f"₹{amount} = {converted:.2f} {target}")
    else:
        st.error("Failed to fetch rates")
```

---

## 2️⃣1️⃣ What You Can Build with Streamlit

* RAG chatbots UI
* Data dashboards
* ML model demos
* Admin panels
* KPI dashboards

---

## 2️⃣2️⃣ Deployment

* Streamlit Cloud (1-click deploy)
* HuggingFace Spaces
* Docker + Cloud

---

## ✅ Final Summary

* Streamlit = **Fast UI for Python**
* Minimal learning curve
* Perfect for **AI / ML / Data Science / GenAI**
* Write logic → UI appears automatically

---

🎯 **Assignment Ideas**

* Age Calculator (DOB → Age)
* Tea ordering app
* CSV dashboard
* ML model UI

---

💡 You now have **enough Streamlit knowledge to build real projects** 🚀
