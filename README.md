📘 Coffee_Sales_Dashboard

----- 

Descripción
Este proyecto utiliza Excel avanzado para gestionar y analizar pedidos de café. Se implementan funciones de búsqueda, condicionales, referencias cruzadas y tablas dinámicas, integrando datos de clientes (customers), productos (products) y pedidos (orders). Además, se construye un dashboard interactivo para visualizar tendencias de ventas y comportamiento de clientes.

-------

🚀 Funcionalidades principales

🔎 Funciones de búsqueda y referencia

      - EMAIL

            =SI(XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0)=0,"",
                 XLOOKUP(C2,customers!$A$1:$A$1001,customers!$C$1:$C$1001,,0))
            👉 Busca el correo electrónico del cliente según su Customer ID. Si no existe, devuelve vacío.

      - COUNTRY

            =XLOOKUP(C2,customers!$A$1:$A$1001,customers!$G$1:$G$1001,,0)
            👉 Devuelve el país del cliente desde la hoja customers.

📊 Funciones de búsqueda en productos

      - Coffee Type

          =ÍNDICE(products!$A$1:$G$49,
                  COINCIDIR(orders!$D2,products!$A$1:$A$49,0),
                  COINCIDIR(orders!I$1,products!$A$1:$G$1,0))
          👉 Obtiene el tipo de café según el Product ID.

      - Roast Type
      
          =ÍNDICE(products!$A$1:$G$49,
                  COINCIDIR(orders!$D2,products!$A$1:$A$49,0),
                  COINCIDIR(orders!J$1,products!$A$1:$G$1,0))
          👉 Devuelve el tipo de tostado (Light, Medium, Dark).

      - Size
      
          =ÍNDICE(products!$A$1:$G$49,
                  COINCIDIR(orders!$D2,products!$A$1:$A$49,0),
                  COINCIDIR(orders!K$1,products!$A$1:$G$1,0))
          👉 Obtiene el tamaño del paquete (ej. 0.5 kg, 1.0 kg).

      - Unit Price

          =ÍNDICE(products!$A$1:$G$49,
                  COINCIDIR(orders!$D2,products!$A$1:$A$49,0),
                  COINCIDIR(orders!L$1,products!$A$1:$G$1,0))
          👉 Devuelve el precio unitario del producto.

💰 Cálculo de ventas

      - Sale (Venta)
      
          =L2*E2
          👉 Multiplica el Unit Price por la Quantity para calcular el total de la venta.

🏷️ Clasificación de productos

       - Coffee Type Name

          =SI(I2="Rob","Robusta",
             SI(I2="Exc","Excelsa",
             SI(I2="Ara","Arabica",
             SI(I2="Lib","Liberica",""))))
          👉 Traduce abreviaturas de café a nombres completos.

      - Roast Type Name

          =SI(J2="M","Medium",
             SI(J2="L","Light",
             SI(J2="D","Dark","")))
          👉 Traduce abreviaturas de tostado a nombres completos.

🎟️ Fidelización

      =XLOOKUP([@[Customer ID]],customers!$A$1:$A$1001,customers!$I$1:$I$1001,,0)
      👉 Devuelve si el cliente tiene tarjeta de fidelidad (Yes/No).

--------------

📂 Estructura del archivo

      orders → Registro de pedidos con fórmulas para extraer datos de clientes y productos.
      
      customers → Base de datos de clientes (ID, nombre, país, email, fidelización).
      
      products → Catálogo de productos (ID, tipo de café, tostado, tamaño, precio, margen).
      
      TotalSales → Tabla dinámica con ventas por mes y año.
      
      CountryBarChart → Ventas por país.
      
      Top5Customers → Ranking de clientes principales.
      
      Dashboard → Panel interactivo con gráficos y filtros.

------------

🎯 Objetivo
Este proyecto demuestra cómo integrar funciones avanzadas de Excel (BUSCARX, ÍNDICE, COINCIDIR, SI) con tablas dinámicas y dashboards para analizar datos de ventas. El resultado es un sistema que convierte datos crudos en información estratégica para la toma de decisiones comerciales.
