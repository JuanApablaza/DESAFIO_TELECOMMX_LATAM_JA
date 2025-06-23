# DESAFIO_TELECOMMX_LATAM_JA


[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JuanApablaza/DESAFIO_TELECOMMX_LATAM_JA/blob/main/mi_notebook.ipynb)

📌 Descripción del Proyecto
Este proyecto analiza datos de clientes de telecomunicaciones para identificar patrones de evasión (Churn) y desarrollar estrategias de retención efectivas.

🛠️ Tecnologías Utilizadas
Python 3

Pandas

Requests

Matplotlib

Seaborn

📂 Estructura del Proyecto
text
telecom-churn-analysis/
├── data/
│   └── TelecomX_Data.json (fuente remota)
├── notebooks/
│   └── Analisis_Churn_Telecom.ipynb
└── README.md
🔍 Métodología
1. Extracción y Transformación de Datos
python
# Importar bibliotecas
import pandas as pd
import requests
from pandas import json_normalize

# Cargar datos desde URL JSON
url = 'https://raw.githubusercontent.com/JuanApablaza/DESAFIO_TELECOMMX_LATAM_JA/refs/heads/main/TelecomX_Data.json'
response = requests.get(url)
data = response.json()

# Crear y normalizar DataFrame
df = pd.DataFrame(data)
df_normalized = pd.concat([
    df[['customerID', 'Churn']],
    json_normalize(df['customer']),
    json_normalize(df['phone']),
    json_normalize(df['internet']),
    json_normalize(df['account'])
], axis=1)
2. Limpieza de Datos
Normalización de valores categóricos (ej: "No phone service" → "No")

Conversión de variables a tipos adecuados

Manejo de valores nulos

3. Análisis Exploratorio
Estadísticas descriptivas

Distribución de variables clave

Análisis comparativo entre grupos (Churn vs No Churn)

📊 Principales Hallazgos
Factores de Alto Riesgo (Churn > 30%)
Método de pago: Electronic check (45.3%)

Tipo de contrato: Mes a mes (42.7%)

Servicio de internet: Fibra óptica (41.9%)

Servicios adicionales: Sin seguridad online (41.8%) o soporte técnico (41.6%)

Segmentos Estables (Churn < 10%)
Contratos anuales/bianuales

Clientes con pagos automáticos

Usuarios con múltiples servicios contratados

💡 Recomendaciones Estratégicas
Programa de fidelización para clientes con contratos mensuales

Incentivos para migrar a pagos automáticos

Paquetes combinados que incluyan servicios de seguridad y soporte

Revisión de la experiencia con fibra óptica

Programas especiales para adultos mayores

📈 Impacto Esperado
Variable	Churn Actual	Meta con Acciones
Contrato mes a mes	42.7%	30-35%
Electronic check	45.3%	25-30%
Sin seguridad online	41.8%	20-25%
Beneficio estimado: Reducción del 10-15% en la tasa general de Churn.

▶️ Próximos Pasos
Implementar programas piloto basados en los insights

Monitorear impacto en tasas de retención

Desarrollar modelo predictivo de Churn

📚 Recursos
Diccionario de datos

Dataset original: TelecomX_Data.json
