# palabras-mas-repetidas
Algoritmo que detecta cuales son las palabras que más se repiten un una cadena de texto, parrafo, etc.


from operator import itemgetter

texto = """
Aqui se debe poner el texto que se quiere analizar para encontrar las palabras mas repetidas en un texto
"""

#############################################################################

# Los caracteres que no contamos como palabras

quitar = [',', ';', ':', '\n', '!', '\', ''', '-', '|', '?', '¿', '¡']
for caracter in quitar:
  texto = texto.replace(caracter, "")
# Remplazarlo por "nada"; es decir, removerlo

# Lo convertimos a minúsculas pues una palabra mayúscula y minúscula cuenta como una sola
texto = texto.lower()
# Las palabras están separadas por un espacio así que convertimos la cadena a arreglo

palabras = texto.split(" ")
# Ahora vamos a contar las palabras creando un diccionario. En este caso la clave del diccionario

# será la palabra, y el valor será el conteo
diccionario_frecuencias = {}
for palabra in palabras:
  if palabra in diccionario_frecuencias:
    diccionario_frecuencias[palabra] += 1
  else:
    diccionario_frecuencias[palabra] = 1

#Aqui ordenamos el diccionario de mayor a menor
ordenado = dict(
  sorted(diccionario_frecuencias.items(), key=itemgetter(1), reverse=True))

#Aqui imprimos en la consola las palabras que mas aparecen en los comentarios
for palabra in ordenado:
  frecuencia = ordenado[palabra]

  print(f" {palabra} = {frecuencia}")
