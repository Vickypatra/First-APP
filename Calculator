# app.py
import streamlit as st

st.set_page_config(page_title="Simple Calculator", page_icon="🧮", layout="centered")

st.title("🧮 Simple Calculator")
st.write("A tiny calculator built with Streamlit — add, subtract, multiply, divide, power, percent.")

# Input
num1 = st.number_input("Number 1", value=0.0, format="%.8f")
num2 = st.number_input("Number 2", value=0.0, format="%.8f")

op = st.selectbox("Operation", ["Add (+)", "Subtract (-)", "Multiply (×)", "Divide (÷)", "Power (^)", "Percent of (a % of b)"])

def calculate(a, b, operation):
    try:
        if operation == "Add (+)":
            return a + b
        if operation == "Subtract (-)":
            return a - b
        if operation == "Multiply (×)":
            return a * b
        if operation == "Divide (÷)":
            return "Undefined (division by zero)" if b == 0 else a / b
        if operation == "Power (^)":
            return a ** b
        if operation == "Percent of (a % of b)":
            # interpret as: what is a% of b -> (a/100)*b
            return (a / 100.0) * b
    except Exception as e:
        return f"Error: {e}"

if st.button("Calculate"):
    result = calculate(num1, num2, op)
    st.markdown("### Result")
    st.success(result)

# Optional: basic history in-session
if "history" not in st.session_state:
    st.session_state.history = []

if st.button("Save to history"):
    st.session_state.history.append(f"{num1} {op} {num2} = {calculate(num1, num2, op)}")

if st.session_state.history:
    st.markdown("#### History (this session)")
    for i, item in enumerate(reversed(st.session_state.history), 1):
        st.write(f"{i}. {item}")

st.caption("Source: simple Streamlit app — save this file as app.py and run `streamlit run app.py`")

