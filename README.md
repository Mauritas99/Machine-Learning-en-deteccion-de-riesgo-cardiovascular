<h2>Instanciado de modelos de machine learning para la detección de pacientes con riesgo cardiovascular elevado.</h2>
<hr>
<h4>Descripción del proyecto</h4>
<hr>
<p>Las enfermedades crónicas no transmisibles (ECNT) son la principal causa de <b>muerte y discapacidad</b> en el mundo. Cada año mueren 41 millones de personas, lo que equivale al 71% de las muertes que se producen en el mundo (Organización Panamericana de la Salud [OPS], 2023). Uno de los principales factores de riesgo (FR) de las ECNT es la <b>alimentación inadecuada</b>, junto con el  <b>consumo de tabaco</b>,  <b>el consumo nocivo de alcohol</b> y la  <b>inactividad física</b> (Ministerio de Salud y Desarrollo Social, 2019).</p>
<p>El siguiente proyecto tiene por finalidad emplear datos ambientales, nutricionales y socioecónomicos de pacientes que asisten al Hospital Nacional de Clinicas de la provincia de Córdoba para indagar sobre las variables relacionadas al riesgo cardiovascular e instanciar modelos de aprendizaje automático que logren predecir el nivel de dicho riesgo para cada paciente, basandose en el indice de Salud Cardiovascular Ideal (SCI), creado por la Asociación Americana del Corazón.</p>
<br>
<h4>Tecnologias empleadas:</h4>
<hr>
<p>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Python.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Jupyter.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/HTML.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Pandas.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Matplotlib.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Scikit_learn.png" height=50px>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Xgboost.png" height=50px>
  <img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Buttons_github/Imbalanced_learn.png" height=50px>
</p>
<h4>Antes de clonar el repositorio ⚠️</h4>
<hr>
<ol>
  <li>Recordá instalar todas las librerias necesarias para correr los notebooks (en la linea de comandos del proyecto, o en alguna celda de Jupyter Notebook colocá : <em>pip install -r requirements.txt</em>)</li>
</ol>
<h4>Resultados y principales hallazgos del trabajo</h4>
<hr>
<p>El dataset original está compuesto por <b>344 filas, 463 columnas</b> (una cantidad limitada de datos y una cardinalidad elevada), 18883 datos nulos y ningun valor duplicado.</p>
<p>Se procedió a examinar aquellas variables de interés para el modelo predictivo (limitando a solo <b>21 características</b>), sobre las cuales se procedió a imputar valores nulos (en algunos casos, por <b>media o moda</b>, en otros se emplearon modelos de <b>RandomForest</b>, para conservar la varianza de la variable). Se permitió conservar valores atípicos a aquellas variables donde la posibilidad de encontrar estos rangos de datos es posible (relacionados con datos de laboratorio, como <b>colesterol en sangre o glucemia</b>).</p>
<p>Antes entrenar los modelos, se preprocesaron las variables según su tipo de dato <b>(varCatOrd == OrdinalScaler | varCatNom == OneHotEncoder | varNum == StandarScaler)</b>. Además, se encontró un marcado desbalance de clases entre los posibles valores de la variable a predecir (SCI "Pobre" > SCI "Intermedio"), por lo cual se empleó <b>SMOTE (imbalanced-learn)</b> para generar datos sintéticos que equilibren ambas clases.</p>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Imagenes%20Machine_learning_cardiovascular/Desbalance_clases.PNG" height=300px>
<p>Se instanciaron 2 modelos de clasificación: <b>Regresión Logística (scikit-learn) y XGBoostClassifier</b>. Ambos emplearon los mismos datos de entrenamiento - prueba y fueron sometidos a los mismos criterios de evaluación.</p>
<p>Ambos modelos resultaron robustos para predecir el valor de SCI para los pacientes, con una tasa de predicciones erróneas muy baja(precisión y sensibilidad <b>superior al 90%</b>, area bajo la curva ROC <b>superiores a 0.9</b> y reportes de clasificacion óptimos).</p>
<p>Indagando en las características mas relevantes para las predicciones de los modelos, encontramos que tanto "TBQ_cod" (consumo de tabaco) y "IMC_Kg/m2" tuvieron mayor influencia para predecir la clase 1 (SCI == "Pobre"), y que para la Regresión Logística, "NDVI_clasif_Poca Vegetacion" da sentido a la predicción de la clase 0 "SCI == "Intermedio".</p>
<img src="https://raw.githubusercontent.com/Mauritas99/Proyect_images/refs/heads/main/Imagenes%20Machine_learning_cardiovascular/Coeficiente_log.PNG" height=500px>
<p>No obstante, otras variables como las relacionadas al <b>ambiente, grado de instrucción y ocupación</b> tambien se encontraron asociadas a las predicciones.</p>
<h4>Conclusión</h4>
<hr>
<p>Se logró instanciar de manera eficiente dos modelos que pueden predecir, teniendo en cuenta las variables de interés, si un paciente de determinadas características posee o no un riesgo cardiovascular elevado o no.</p>
<p>Poder implementar modelos predictivos para encontrar con antelación cuando determinados valores puedan sugerir un riesgo cardiovascular a futuro es, no solo una recomendación, sino una necesidad para la población y un compromiso para la salud pública.</p>
