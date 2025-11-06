import streamlit as st
import pandas as pd
import plotly.express as px

# -------------------------------
# App Title & Config
# -------------------------------
st.set_page_config(page_title="Investment Portfolio", layout="centered")
st.title("💹 Investment Portfolio Allocation - India")

st.markdown("""
This app displays an example of a **diversified low-to-moderate risk investment portfolio**  
for Indian investors, along with allocations, expected returns, and time horizons.
""")

# -------------------------------
# Portfolio Data
# -------------------------------
data = {
    "Asset class": [
        "Equity (Large cap)",
        "Debt Instrument",
        "Bank deposit",
        "Sovereign gold bond",
        "Real estate",
        "Insurance and pension funds"
    ],
    "Risk level": [
        "Moderate risk",
        "Low risk",
        "Low risk",
        "Low risk",
        "High risk",
        "Low risk"
    ],
    "Expected annual return (%)": [11, 7, 7.5, 5, 17.5, 7],
    "Investment time horizon": [
        "3–5 years",
        "10 years",
        "10 years",
        "10–15 years",
        "3–5 years",
        "5–7 years"
    ],
    "Allocation (%)": [20, 30, 15, 20, 5, 10]
}

df = pd.DataFrame(data)

# -------------------------------
# Display Portfolio Table
# -------------------------------
st.subheader("📊 Portfolio Overview")
st.dataframe(df, use_container_width=True)

# -------------------------------
# Weighted Expected Return
# -------------------------------
weighted_return = (df["Expected annual return (%)"] * df["Allocation (%)"]).sum() / 100
st.metric("📈 Weighted Expected Annual Return", f"{weighted_return:.2f}%")

# -------------------------------
# Charts Section
# -------------------------------
col1, col2 = st.columns(2)

with col1:
    fig1 = px.pie(df, names="Asset class", values="Allocation (%)",
                  title="Portfolio Allocation by Asset Class",
                  color_discrete_sequence=px.colors.qualitative.Set2)
    st.plotly_chart(fig1, use_container_width=True)

with col2:
    fig2 = px.bar(df, x="Asset class", y="Expected annual return (%)",
                  color="Risk level", text="Expected annual return (%)",
                  title="Expected Return vs Risk Level")
    st.plotly_chart(fig2, use_container_width=True)

# -------------------------------
# Portfolio Insights
# -------------------------------
st.subheader("💡 Insights")
st.markdown(f"""
- Total portfolio allocation: **100%**
- **Weighted average return:** approximately **{weighted_return:.2f}% per annum**
- The portfolio has **diversified exposure** to low, moderate, and high-risk assets.
- Debt and deposits (45%) ensure stability, while equity and real estate (25%) provide growth.
- Gold and insurance add **hedging and long-term safety**.
""")

# -------------------------------
# Download Option
# -------------------------------
csv = df.to_csv(index=False).encode('utf-8')
st.download_button("⬇ Download Portfolio Data (CSV)", csv, "portfolio_data.csv", "text/csv")

# -------------------------------
# Footer
# -------------------------------
st.markdown("---")
st.caption("📘 Educational tool created with Streamlit | Author: Harsh")
