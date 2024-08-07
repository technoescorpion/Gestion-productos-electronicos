# Gestion-productos-electronicos

class Producto:
    def __init__(self, nombre, categoria):
        self.nombre = nombre
        self.categoria = categoria

class Tienda:
    def __init__(self):
        self.productos = []

    def agregar_producto(self, nombre, categoria):
        try:
            nuevo_producto = Producto(nombre, categoria)
            self.productos.append(nuevo_producto)
            print(f"Producto '{nombre}' agregado exitosamente.")
        except Exception as e:
            print(f"Error al agregar el producto: {e}")

    def listar_productos(self):
        if self.productos:
            print("Productos registrados:")
            for producto in self.productos:
                print(f"Nombre: {producto.nombre}, Categoría: {producto.categoria}")
        else:
            print("No hay productos registrados.")

    def buscar_producto(self, nombre):
        productos_encontrados = [producto for producto in self.productos if producto.nombre.lower() == nombre.lower()]
        if productos_encontrados:
            print("Producto(s) encontrado(s):")
            for producto in productos_encontrados:
                print(f"Nombre: {producto.nombre}, Categoría: {producto.categoria}")
        else:
            print("Producto no encontrado.")

    def salir(self):
        print("Saliendo del programa...")
        exit()

def main():
    tienda = Tienda()
    while True:
        print("\nSeleccione una opción:")
        print("1. Agregar nuevos productos (Teléfono, Ordenador, Tablet)")
        print("2. Listar todos los productos registrados")
        print("3. Buscar productos por nombre")
        print("4. Salir del programa")
        opcion = input("Opción: ")

        if opcion == '1':
            nombre = input("Ingrese el nombre del producto: ")
            categoria = input("Ingrese la categoría del producto (Teléfono, Ordenador, Tablet): ")
            tienda.agregar_producto(nombre, categoria)
        elif opcion == '2':
            tienda.listar_productos()
        elif opcion == '3':
            nombre = input("Ingrese el nombre del producto a buscar: ")
            tienda.buscar_producto(nombre)
        elif opcion == '4':
            tienda.salir()
        else:
            print("Opción no válida. Por favor, intente nuevamente.")

if __name__ == "__main__":
    main()
