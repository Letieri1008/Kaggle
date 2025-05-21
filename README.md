# Kaggle
Heart Disease Cleveland UCI
Resolution: https://www.kaggle.com/datasets/cherngs/heart-disease-cleveland-uci

he data is already presented in https://www.kaggle.com/ronitf/heart-disease-uci but there are some descriptions and values that are wrong as discussed in https://www.kaggle.com/ronitf/heart-disease-uci/discussion/105877. So, here is re-processed dataset that was cross-checked with the original data https://archive.ics.uci.edu/ml/datasets/Heart+Disease.
Content

There are 13 attributes

    age: age in years
    
    sex: sex (1 = male; 0 = female)
    
    cp: chest pain type
    -Value 0: typical angina
    - Value 1: atypical angina
    -Value 2: non-anginal pain
    - Value 3: asymptomatic
    
    trestbps: resting blood pressure (in mm Hg on admission to the hospital)
    chol: serum cholestoral in mg/dl
    fbs: (fasting blood sugar > 120 mg/dl) (1 = true; 0 = false)
    
    restecg: resting electrocardiographic results
    
    - Value 0: normal
    - Value 1: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV)
    - Value 2: showing probable or definite left ventricular hypertrophy by Estes' criteria
    
    thalach: maximum heart rate achieved
    exang: exercise induced angina (1 = yes; 0 = no)
    oldpeak = ST depression induced by exercise relative to rest
    
    slope: the slope of the peak exercise ST segment
    
    - Value 0: upsloping
    - Value 1: flat
    - Value 2: downsloping
    ca: number of major vessels (0-3) colored by flourosopy
    thal: 0 = normal; 1 = fixed defect; 2 = reversable defect
    and the label
    condition: 0 = no disease, 1 = disease

(CODE)

df = pd.read_csv("Downloads/Tour prático de Machine Learning com Scikit-Learn/heart-disease.csv")
df.head()

pd.crosstab(df["target"],df["sex"]).plot(kind="bar",
figsize=(10,6),
color=["salmon","lightblue"])
plt.title("Frequência de doenças cardíacas por sexo")
plt.xlabel("0=Não tem doença, 1=Tem doença")
plt.ylabel("Amostragem")
plt.legend(["Feminino","Masculino"])
plt.xticks(rotation=0)

#plot para valores positivos

plt.figure(figsize=(10,6))
plt.scatter(df["age"][df["target"]==1],
            df["thalach"][df["target"]==1],
            c="salmon")

#plot para valores negativos
plt.scatter(df["age"][df["target"]==0],
            df["thalach"][df["target"]==0],
            c="lightblue")

plt.title("Frequência de doenças cardíacas por idade e frequência cardíaca máxima")
plt.xlabel("Idade")
plt.legend(["Doença","Saudável"])
plt.ylabel("Frequência cardíaca máxima")

pd.crosstab(df["cp"], df["target"]).plot(
    kind="bar",
    figsize=(10, 6),
    color=["salmon", "lightblue"]
)

plt.title("Tipos de dores no peito")
plt.xlabel("0=Não tem doença, 1=Tem doença")
plt.ylabel("Amostragem")
plt.legend(["Feminino", "Masculino"])






