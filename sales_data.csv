import streamlit as st
import pandas as pd

st.title("Sales & Revenue Analysis Dashboard")

# Upload CSV file
uploaded_file = st.file_uploader("Upload your CSV file", type=["csv"])

if uploaded_file is not None:

    df = pd.read_csv(uploaded_file)

    st.subheader("Dataset Preview")
    st.dataframe(df)

    # KPIs
    total_sales = df["Quantity"].sum()
    total_revenue = df["Revenue"].sum()

    col1, col2 = st.columns(2)

    with col1:
        st.metric("Total Sales", total_sales)

    with col2:
        st.metric("Total Revenue", f"₹ {total_revenue}")

    # Top products
    st.subheader("Top Performing Products")

    top_products = (
        df.groupby("Product")["Revenue"]
        .sum()
        .sort_values(ascending=False)
    )

    st.bar_chart(top_products)

    # Revenue Trend
    if "Date" in df.columns:
        st.subheader("Revenue Trend")

        df["Date"] = pd.to_datetime(df["Date"])
        revenue_trend = df.groupby("Date")["Revenue"].sum()

        st.line_chart(revenue_trend)

    # Complete data
    st.subheader("Complete Data")
    st.dataframe(df)