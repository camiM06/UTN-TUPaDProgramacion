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

