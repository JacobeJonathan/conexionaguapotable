# conexionaguapotable

## Nos planteamos las preguntas
- Que conexiones de agua potable estuvieron activas hasta el año 2019?

## Buscamos la base de datos
- en este caso tenemos un csv

## Utilizareos la herramienta de google colaboratory
- cargamos los archivos
  ```py
  from google.colab import files
  uploaded = files.upload()
  ```
- leemos un archivo xlsx y lo llamaos con read_excel
  ```py
  import pandas as pd
  datosagua = pd.read_csv('Numero de Conexiones Activas de Agua Potable.csv')
  print(datosagua)

  ```
- sabemos que region es elq ue tiene mas conexiones
  ```py
  import pandas as pd
  # Supongamos que tienes tu tabla en un DataFrame llamado 'df'
  # Si aún no has importado los datos en un DataFrame, asegúrate de hacerlo primero.
  
  # Agrupar por departamento y calcular la suma de conexiones activas para cada uno
  departamento_conexiones = datosagua.groupby('DEPARTAMENTO')['CONEX_ACTIVAS'].sum()
  
  # Encontrar el departamento con el máximo número de conexiones activas
  departamento_max_conexiones = departamento_conexiones.idxmax()
  
  # Obtener el valor máximo de conexiones activas
  max_conexiones = departamento_conexiones.max()
  
  print(f"El departamento con más conexiones activas es: {departamento_max_conexiones}, con {max_conexiones} conexiones activas.")


  ```
- sacaremos in grafico de barras para saber o para visualziar mejor
  ```py
  import pandas as pd
  import matplotlib.pyplot as plt
  
  # Supongamos que tienes tu tabla en un DataFrame llamado 'df'
  # Si aún no has importado los datos en un DataFrame, asegúrate de hacerlo primero.
  
  # Agrupar por departamento y calcular la suma de conexiones activas para cada uno
  departamento_conexiones = datosagua.groupby('DEPARTAMENTO')['CONEX_ACTIVAS'].sum()
  
  # Crear el gráfico de pastel con etiquetas y porcentajes
  plt.figure(figsize=(8, 8))  # Tamaño del gráfico
  
  # Extraer los valores de conexiones activas y los nombres de los departamentos
  valores = departamento_conexiones.values
  nombres_departamentos = departamento_conexiones.index
  
  # Colores para el gráfico de pastel
  colores = plt.cm.Set3.colors
  
  # Graficar el pastel
  plt.pie(valores, labels=nombres_departamentos, colors=colores, autopct='%1.1f%%', startangle=140)
  
  # Mostrar porcentajes en el centro del gráfico
  plt.gca().set_aspect('equal')  # Para que el gráfico de pastel sea un círculo
  plt.title('Conexiones de agua activas por departamento')  # Título del gráfico
  
  # Mostrar el gráfico
  plt.show()

  ```
- Finalmente ponemos el grafico
  - ![Visualizacio ](/src/1.png)
 
- Interpretacion:
    - Se puede llegar a la conclusion de que el distrito departamento de lima tiene mas conexiones agua
- Otras conclusiones:
- Se puede sacar de  porque o cuales son las conexiones poor distrito y verificar que mantemientos se estan realziando 
  

  
