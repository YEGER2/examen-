# Diccionarios de productos y stock

productos = {

  '8475HD': ['HP', 15.6, '8GB', 'DD', '1T', 'Intel Core i5', 'Nvidia GTX1050'],

  '2175HD': ['Acer', 14, '4GB', 'SSD', '512GB', 'Intel Core i5', 'Nvidia GTX1050'],

  'JjfFHD': ['Asus', 14, '16GB', 'SSD', '256GB', 'Intel Core i7', 'Nvidia RTX2080Ti'],

  'fgdxFHD': ['HP', 15.6, '12GB', 'DD', '1T', 'Intel Core i3', 'integrada'],

  'GF75HD': ['Asus', 15.6, '12GB', 'DD', '1T', 'Intel Core i7', 'Nvidia GTX1050'],

  '123FHD': ['Acer', 14, '6GB', 'DD', '1T', 'AMD Ryzen 5', 'integrada'],

  '342FHD': ['Acer', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 7', 'Nvidia GTX1050'],

  'UWU131HD': ['Dell', 15.6, '8GB', 'DD', '1T', 'AMD Ryzen 3', 'Nvidia GTX1050']

}



stock = {

  '8475HD': [387990, 10], '2175HD': [327990, 4], 'JjfFHD': [424990, 1],

  'fgdxFHD': [664990, 21], '123FHD': [290890, 32], '342FHD': [444990, 7],

  'GF75HD': [749990, 2], 'UWU131HD': [349990, 1], 'FS1230HD': [249990, 0]

}



# FUNCIONES

def stock_marca(marca):

  total = 0

  for modelo, datos in productos.items():

    if datos[0].lower() == marca.lower():

      if modelo in stock:

        total += stock[modelo][1]

  print(f"El stock es: {total}")



def busqueda_precio(p_min, p_max):

  resultado = []

  for modelo, datos in stock.items():

    precio = datos[0]

    cantidad = datos[1]

    if p_min <= precio <= p_max and cantidad > 0:

      marca = productos[modelo][0]

      resultado.append(f"{marca}--{modelo}")

  if len(resultado) == 0:

    print("No hay notebooks en ese rango de precios.")

  else:

    resultado.sort()

    print("Los notebooks entre los precios consultados son:", resultado)



def eliminar_producto(modelo):

  if modelo in productos and modelo in stock:

    del productos[modelo]

    del stock[modelo]

    return True

  else:

    return False



# MAIN

while True:

  print("\n*** MENU PRINCIPAL ***")

  print("1. Stock marca.")

  print("2. Busqueda por precio.")

  print("3. Eliminar producto.")

  print("4. Salir.")

  op = input("Ingrese opcion: ")



  if op == "1":

    marca = input("Ingrese marca a consultar: ")

    stock_marca(marca)



  elif op == "2":

    while True:

      try:

        p_min = int(input("Ingrese precio minimo: "))

        p_max = int(input("Ingrese precio maximo: "))

        break

      except:

        print("Debe ingresar valores enteros!!")

    busqueda_precio(p_min, p_max)



  elif op == "3":

    while True:

      modelo = input("Ingrese modelo a eliminar: ")

      resultado = eliminar_producto(modelo)

      if resultado:

        print("Producto eliminado!!")

      else:

        print("El modelo no existe!!")

      seguir = input("Desea eliminar otro producto (si/no)?: ").lower()

      if seguir != "si":

        break



  elif op == "4":

    print("Programa finalizado.")

    break

  else:

    print("Debe seleccionar una opcion valida!!")

