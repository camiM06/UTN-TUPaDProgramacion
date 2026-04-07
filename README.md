# UTN-TUPaDProgramacion
TP GITHUB

# EJERCICIO 5 ESCAPE ROOM LA ARENA DEL GLADIADOR

vida_gladiador = 100

vida_enemigo = 100

pociones_vida = 3

daño_ataque_pesado = 15

daño_base_enemigo = 12

turno_gladiador = True

nombre = input("ingrese el nombre del gladiador para iniciar el combate: ").strip().lower()

while not nombre.isalpha():
    nombre = input("nombre invalido, ingrese el nombre del gladiador para iniciar el combate: ").strip().lower()

while vida_gladiador > 0 and vida_enemigo > 0:

    while turno_gladiador:

        print(f"vida gladiador: {vida_gladiador}")
        print(f"vida del enemigo: {vida_enemigo}")
        print(f"pociones de vida disponibles: {pociones_vida}")

        accion = input("elige como seguir: \n1- ataque pesado \n2- rafaga veloz \n3- curar \n").strip()

        while not accion.isdigit():
            accion = input("opcion invalida! elige como seguir: \n1- ataque pesado \n2- rafaga veloz \n3- curar \n").strip()
        if int(accion) < 1 or int(accion) > 3:
            accion = input("opcion invalida! elige como seguir: \n1- ataque pesado \n2- rafaga veloz \n3- curar \n").strip()

        accion = int(accion)

    
        if accion == 1:

            if vida_enemigo >= 20:
                vida_enemigo = vida_enemigo - daño_ataque_pesado
                print(f"atacaste a tu oponente por {daño_ataque_pesado} puntos de daño! ")

            if vida_enemigo < 20:
                daño_ataque_pesado = daño_ataque_pesado * 1.5
                daño_ataque_pesado = float(daño_ataque_pesado)
                print(f"le das un golpe critico a tu oponente por {daño_ataque_pesado} puntos de daño!")
            
            turno_gladiador = False

        if accion == 2:
            for i in range (3):
                vida_enemigo = vida_enemigo - 5
                print("¡atacaste a tu oponente por 5 puntos de daño!")

            turno_gladiador = False

        if accion == 3:
            if pociones_vida > 0:
                pociones_vida = pociones_vida - 1
                vida_gladiador = vida_gladiador + 30
                print(f"tomaste una pocion de vida, tu vida es de {vida_gladiador} puntos y te quedan {pociones_vida} pociones de vida")

            if pociones_vida == 0:
                print("no te quedan pociones de vida")

            turno_gladiador = False


    while not turno_gladiador:
        print("//// TURNO DEL OPONENTE ////")
        vida_gladiador = vida_gladiador - 12
        print("te ataco por 12 puntos de daño!")
        turno_gladiador = True

    if vida_gladiador > 0 and vida_enemigo <= 0:
        print(f"¡VICTORIA! {nombre} has ganado la batalla")
    elif vida_enemigo > 0 and vida_gladiador <= 0:
        print(f"¡DERROTA! has caido en combate.")
    
                    
# EJERCICIO 3 AGENDA DE TURNOS CON NOMBRES 
#/////////////////////////////////////////

lunes1 = "" # 10 hs

lunes2 = "" # 11 hs

lunes3 = "" # 12 hs

lunes4 = "" # 13 hs

martes1 = "" # 13 hs

martes2 = "" # 14 hs

martes3 = "" # 15 hs


nombre = input("ingrese su nombre para comenzar a operar: ").strip()

while not nombre.isalpha():
    nombre = input("nombre invalido. ingrese su nombre para comenzar a operar: ").strip()

while True:
    opcion = input("ingrese una opcion: \n1 - reservar turno \n2 - cancelar turno \n3 - ver agenda \n4 - resumen general \n5 - cerrar sistema ").strip()

# aca busque como hacer el salto de linea para que se vea mas claro



    while opcion not in ("1", "2", "3", "4", "5"):
        opcion = input("opcion invalida. ingrese una opcion:  \n1 - reservar turno \n2 - cancelar turno \n3 - ver agenda \n4 - resumen general \n5 - cerrar sistema ").strip()
    opcion = int(opcion)

    if opcion == 1: 
        dia = input("seleccione un dia: \n1- lunes \n2- martes ").strip()
        while not dia.isdigit() or dia not in ("1", "2"):
            dia = input("opcion invalida. seleccione un dia: \n1- lunes \n2- martes ").strip()
        dia = int(dia)
          
        paciente = input("ingrese el nombre: ").strip().lower()
        while not paciente.isalpha():
            paciente = input("nombre invalido. ingrese el nombre: ").strip().lower()

        if dia == 1 and (paciente == lunes1 or paciente == lunes2 or paciente == lunes3 or paciente == lunes4): 
            print("el paciente ya tiene turno agendado ese dia")
        elif dia == 2 and (paciente == martes1 or paciente == martes2 or paciente == martes3):
            print("el paciente ya tiene turno agendado ese dia")
        else:
            print("seleccione el horario: ")
            if dia == 1:
                hora = input(" 1 - 10 hs, 2 - 11 hs, 3 -12 hs, 4 -13 hs").strip()
                while hora not in ("1", "2", "3", "4"):
                    hora = input("opcion invalida. seleccione el horario: 1 - 10 hs, 2 - 11 hs, 3 -12 hs, 4 - 13 hs").strip()
                hora = int(hora)   
                if hora == 1:
                    lunes1 = paciente
                    print(f" turno agendado 10 hs {lunes1}")  
                elif hora == 2:
                    lunes2 = paciente
                    print(f" turno agendado 11 hs {lunes2}") 
                elif hora == 3:
                    lunes3 = paciente
                    print(f" turno agendado 12 hs {lunes3}")
                else:
                    lunes4 = paciente
                    print(f" turno agendado 13 hs {lunes4}")
            elif dia == 2:
                hora = input(" 1 - 13 hs, 2 - 14 hs, 3 -15 hs").strip()
                while hora not in ("1", "2", "3"):
                    hora = input("opcion invalida. seleccione el horario: 1 - 13 hs, 2 - 14 hs, 3 -15 hs").strip()
                hora = int(hora) 
                if dia == 1:
                    martes1 = paciente
                    print(f" turno agendado 13 hs {martes1}")
                elif dia == 2:
                    martes2 = paciente
                    print(f" turno agendado 14 hs {martes2}")
                else:
                    martes3 = paciente
                    print(f" turno agendado 15 hs {martes3}")

    elif opcion == 2:
        cancelar = input("ingrese su nombre para cancelar: ").strip().lower()

        if cancelar == lunes1:
            lunes1 = ""
            print("turno lunes 10 hs cancelado")
        elif cancelar == lunes2:
            lunes2 = ""
            print("turno lunes 11 hs cancelado")
        elif cancelar == lunes3:
            lunes3 = ""
            print("turno lunes 12 hs cancelado")
        elif cancelar == lunes4:
            lunes4 = ""
            print("turno lunes 13 hs cancelado")
        elif cancelar == martes1:
            martes1 = ""
            print("turno martes 13 hs cancelado")
        elif cancelar == martes2:
            martes2 = ""
            print("turno martes 14 hs cancelado")
        elif cancelar == martes3:
            martes3 = ""
            print("turno martes 15 hs cancelado")
        else: 
            print(" no posee turnos programados")

    elif opcion == 3:
        dia = input("seleccione un dia para ver la agenda: \n1- lunes \n2- martes ").strip()
        while not dia.isdigit() or dia not in ("1", "2"):
            dia = input("opcion invalida. seleccione un dia: \n1- lunes \n2- martes ").strip()
        dia = int(dia)

        if dia == 1:
            if lunes1 == "":
                lunes1 = "libre"
            if lunes2 == "":
                lunes2 = "libre"
            if lunes3 == "":
                lunes3 = "libre"
            if lunes4 == "":
                lunes4 = "libre"
            print(f" turno 10 hs {lunes1}, turno 11 hs {lunes2}, turno 12 hs {lunes3}, turno 13 hs {lunes4}")

        elif dia == 2:
            if martes1 == "":
                martes1 = "libre"
            if martes2 == "":
                martes2 = "libre"
            if martes3 == "":
                martes3 = "libre"
            print(f" turno 13 hs {martes1}, turno 14 hs {martes2}, turno 15 hs {martes3}")

    elif opcion == 4: 
        dia = input("seleccione un dia para ver los turnos dados: \n1- lunes \n2- martes \n3- comparar dias").strip()
        while not dia.isdigit() or dia not in ("1", "2", "3"):
            dia = input("opcion invalida. seleccione un dia: \n1- lunes \n2- martes \n3- comparar dias").strip()
        dia = int(dia) 

        sin_turno_lunes = 0

        if lunes1 == "":
            sin_turno_lunes += 1
        
        if lunes2 == "":
            sin_turno_lunes += 1
        
        if lunes3 == "":
            sin_turno_lunes += 1
        
        if lunes4 == "":
            sin_turno_lunes += 1

        if dia == 1:
            print(f"cantidad de turnos libres para el dia lunes: {sin_turno_lunes}")

        sin_turno_martes = 0

        if martes1 == "":
            sin_turno_martes += 1

        if martes2 == "":
            sin_turno_martes += 1

        if martes3 == "":
            sin_turno_martes += 1

        if dia == 2:
            print(f"cantidad de turnos libres para el dia martes: {sin_turno_martes}")

        if dia == 3:
            if sin_turno_lunes > sin_turno_martes:
                print("mas turnos disponibles dia lunes")
            if sin_turno_lunes < sin_turno_martes:
                print("mas turnos disponibles dia martes")
            else:
                print("misma ocupacion ambos dias")
        
    if opcion == 5:
        print("saliendo del sistema")
    break

# EJERCICIO 4 ESCAPE ROOM LA BOVEDA
#//////////////////////////////////

energia = 100

tiempo = 12

cerraduras_abiertas = 0

alarma = False

codigo_parcial = ""

opcion_anterior = ""

repetidas = 0

nombre = input("ingrese nombre del agente: ").strip().lower()

if not nombre.isalpha():
    nombre = input("nombre invalido, ingrese nombre del agente: ").strip().lower()



while not alarma and energia > 0 and tiempo > 0 and cerraduras_abiertas < 3:

        opcion = input("tenes que abrir tres cerraduras antes que se te agote el tiempo o la energia! elegi lo que vas a hacer: \n1- forzar cerradura \n2- hackear panel \n3- descansar ").strip()
    
        while opcion not in ("1", "2", "3"):
            opcion = input("opcion invalida. elegi lo que vas a hacer: \n1- forzar cerradura \n2- hackear panel \n3- descansar ").strip()

        opcion = int(opcion)


        if opcion == opcion_anterior : # aca busque ayudar porque no sabia como hacer para que corte el bucle si se elegia 3 veces la misma opcion
            repetidas += 1
        else:
            repetidas = 1
            opcion_anterior = opcion
        
        if repetidas == 3:
            alarma = True

        
        if opcion == 1 and repetidas != 3:
                energia = energia - 20
                print(f" tu energia bajo a {energia}")
                tiempo = tiempo - 2
                print(f"tu tiempo bajo a {tiempo}")
                cerraduras_abiertas += 1
                print(f"abriste 1 cerradura, tenes {cerraduras_abiertas} cerraduras abiertas")
                if energia < 40:
                    riesgo_alarma =input("riesgo de alarma! elige un numero del 1 al 3 para intentar abrir la cerradura").strip()
                    while riesgo_alarma not in ("1", "2", "3"):
                        riesgo_alarma =input("opcion invalida. elige un numero del 1 al 3 para intentar abrir la cerradura").strip()

                    riesgo_alarma = int(riesgo_alarma)

                    if riesgo_alarma == 1:
                        cerraduras_abiertas += 1
                        print(f"abriste una cerradura, tenes {cerraduras_abiertas} cerraduras abiertas")
                        energia = energia - 20
                        print(f" tu energia bajo a {energia}")
                        tiempo = tiempo - 2
                        print(f"tu tiempo bajo a {tiempo}")
                    elif riesgo_alarma == 2:
                        cerraduras_abiertas+= 1
                        print(f"abriste una cerradura, tenes {cerraduras_abiertas} cerraduras abiertas")
                        energia = energia - 20
                        print(f" tu energia bajo a {energia}")
                        tiempo = tiempo - 2
                        print(f"tu tiempo bajo a {tiempo}")
                
                    elif riesgo_alarma == 3:
                        alarma = True
                
                if cerraduras_abiertas == 3:
                    print("¡abriste todas las cerraduras, mision exitosa! felicitaciones!")
                    break


        if opcion == 2:
            energia = energia - 10
            print(f" tu energia bajo a {energia}")
            tiempo = tiempo - 3
            print(f"tu tiempo bajo a {tiempo}")  
        

            for i in range (4):
                letra = input("para hackear el sistema de seguridad, ingresa de a una letra: ").strip()
             
                # aca busque un poco de ayuda en como armar esta variable para poder contar las letras que ingresa el usuario

                while len(letra) != 1 or not letra.isalpha():
                    letra = input("Error, ingrese solo una letra para escribir el codigo: ").strip()

                codigo_parcial += letra


            if len(codigo_parcial) >= 8:
                cerraduras_abiertas += 1
                print(f"abriste una cerradura, tenes {cerraduras_abiertas} cerraduras abiertas")

            if cerraduras_abiertas >= 3:
                print("¡abriste todas las cerraduras, mision exitosa! felicitaciones!")
                break
            
            
            if len(codigo_parcial) < 8:
                print("aun faltan letras para abrir la cerradura")

        if opcion == 3:
            
            tiempo = tiempo - 1
            print(f"tomas un descanso, tu tiempo bajo a {tiempo}")

            if energia < 40:
                energia = energia - 10
                print(f"riesgo de alarma activo, tu energia bajo a {energia}")
            elif energia >= 40:
                energia = energia + 15
                print(f" tu energia subio a {energia}")
            
            if energia <= 0:
                print("¡te quedaste sin energia! fracasaste en la mision!")
                break

if alarma == True:
    print("¡¡se activo la alarma!! el sistema se bloqueo. Fracaste en la mision!")

elif tiempo <= 3 and cerraduras_abiertas < 3:
    print("¡¡te quedaste sin tiempo!! fracaste en la mision!")

# EJERCICIO 2 ACCESO AL CAMPUS Y MENU SEGURO
#///////////////////////////////////////////

usuario = "alumno"

clave = "python123"

cont = 1

usuario = input("ingrese su usuario: ").strip().lower()


while usuario != "alumno" and cont < 3:
    usuario = input("usuario incorrecto. ingrese su usuario: ").strip().lower()
    cont += 1
if usuario != "alumno":
    print("demasiados intentos. cuenta bloqueada") 
else:
    clave = input("ingrese la clave para ingresar: ")
    cont = 1
    while clave != "python123" and cont < 3:
        clave = input("clave incorrecta. ingrese su clave: ").strip().lower()
        cont += 1
    if clave != "python123":
        print("demasiados intentos. cuenta bloqueada") 
    else:
        while True:

            opcion = input("ingrese una opcion: 1) estado 2) cambiar clave 3) mensaje 4) salir: ").strip()

            while not opcion.isdigit() or opcion not in ("1", "2", "3", "4"): 
                opcion = input("ingrese una opcion correcta: 1) estado 2) cambiar clave 3) mensaje 4) salir: ").strip()   
            opcion = int(opcion)
        
            if opcion == 1:
                print("inscripto")
                

            if opcion == 2:
                clave = input("la nueva clave debe tener 6 caracteres minimmo. ingrese su nueva clave: ").strip()
                while len(clave) < 6:
                    clave = input("la nueva clave debe tener 6 caracteres minimo. ingrese una nueva clave: ").strip()
                else:
                    confirmacion= input("ingrese de nuevo la clave para confirmar: ").strip()
                
                while confirmacion != clave:
                    confirmacion= input("las claves no coinciden. ingrese de nuevo la clave para confirmar: ").strip() 
                else:
                    print("la nueva clave se guardo correctamente.")

            if opcion == 3:
                print("´en medio de la dificultad, reside la oportunidad´. albert einstein.")

            if opcion == 4: 
                print("esta saliendo del campus.")
                break
            
# EJERCICIO 1 CAJA DEL KIOSCO 

nombre = input("ingrese el nombre del cliente: ").strip() # en la consigna piden que validemos con isalpha pero me toma como false nombre y apellido

while not nombre.isalpha():
    nombre = input("ingrese un nombre valido: ")
if nombre == "":
    nombre = input("ingrese un nombre valido: ")


cantidad_productos = (input("ingrese la cantidad de productos a adquirir: ")).strip()

while not cantidad_productos.isdigit():
    cantidad_productos =input("ingrese una cantidad valida: ")
if int(cantidad_productos) <= 0 or cantidad_productos == "":
    cantidad_productos =input("ingrese una cantidad valida: ")

cantidad_productos = int(cantidad_productos)

total_sin_desc = 0

total_con_desc = 0


for i in range (1, cantidad_productos+1):
    precio = input(f"ingrese el valor del articulo {i}: ").strip()
    while not precio.isdigit():
        precio = input("ingrese un valor valido: ")
    if precio == "" or int(precio) <= 0:
        precio = input("ingrese un valor valido: ")
    precio = int(precio)
    total_sin_desc += precio
    descuento = input("¿tiene descuento? ingrese S por si y N por no: ").strip().lower()
    while descuento != "s" and descuento != "n":
        descuento = input("opcion no valida. ingrese S por si y N por no: ").strip().lower()
    if descuento == "s":
        total_con_desc += precio * 0.90
    else:
        total_con_desc += precio
    print(f"articulo {i} / precio {precio} / descuento {descuento}")

ahorro = total_sin_desc - total_con_desc

promedio = total_con_desc / cantidad_productos

print(f" cliente: {nombre}")
print(f"cantidad de productos: {cantidad_productos}")
print(f"total sin descuento: {total_sin_desc:.2f}")
print(f"total con descuento: {total_con_desc:.2f}")
print(f"ahorro total: {ahorro:.2f} ")
print(f" promedio de descuento por articulo: {promedio:.2f}")




