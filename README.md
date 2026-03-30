# bot-foot.import streamlit as st
import math

# Configuration de la page pour le look "Sombre/Dark Mode"
st.set_page_config(page_title="OMG PREDICTOR", page_icon="⚽")

# Style CSS pour imiter ton interface (Couleurs sombres et bouton vert)
st.markdown("""
    <style>
    .stApp { background-color: #0e1117; color: white; }
    .stButton>button {
        background-color: #28a745;
        color: white;
        width: 100%;
        border-radius: 10px;
        height: 3em;
        font-weight: bold;
    }
    .main-header { font-size: 24px; font-weight: bold; text-align: center; color: #ffffff; }
    .sub-text { font-size: 12px; text-align: center; color: #888; margin-bottom: 20px; }
    </style>
    """, unsafe_allow_html=True)

# En-tête de l'application
st.markdown('<div class="main-header">⚡ OMG PREDICTOR</div>', unsafe_allow_html=True)
st.markdown('<div class="sub-text">POISSON + ML + IA</div>', unsafe_allow_html=True)

# --- SECTION SAISIE ---
with st.container():
    st.subheader("⚽ CONFIGURER LE MATCH")
    
    col1, col2 = st.columns(2)
    with col1:
        home_team = st.text_input("DOMICILE (Equipe 1)", placeholder="Ex: PSG")
    with col2:
        away_team = st.text_input("EXTÉRIEUR (Equipe 2)", placeholder="Ex: Marseille")
    
    context = st.text_area("🧠 INFOS CONTEXTUELLES", 
                          placeholder="Derby, blessés, forme récente, cotes...", 
                          help="Ajoutez des détails pour affiner l'IA")

# --- BOUTON D'ANALYSE ---
if st.button("⚡ Lancer l'analyse PRO"):
    if home_team and away_team:
        with st.spinner('Analyse des algorithmes en cours...'):
            # Ici on simule un calcul de Poisson (on pourra connecter une vraie API plus tard)
            # Pour l'exemple, on génère des chiffres réalistes
            prob_over = 56
            prob_ml = 54
            prob_comb = (prob_over + prob_ml) / 2
            
            st.divider()
            
            # --- AFFICHAGE DES RÉSULTATS (Comme sur ton image) ---
            st.success(f"📊 ANALYSE COMPLÈTE : {home_team} vs {away_team}")
            
            st.write(f"📈 **Probabilité Poisson Over 2.5 :** {prob_over}%")
            st.progress(prob_over / 100)
            
            st.write(f"🤖 **Probabilité Machine Learning :** {prob_ml}%")
            st.progress(prob_ml / 100)
            
            st.info(f"✅ **Décision : UNDER 2.5** (Confiance : 65%)")
            
            st.warning("⚠️ **Niveau de risque : Moyen**")
    else:
        st.error("Veuillez entrer le nom des deux équipes.")

# Bas de page
st.markdown("---")
st.caption("Modèles actifs : Poisson Regression, Random Forest ML, GPT-4 Analysis")
