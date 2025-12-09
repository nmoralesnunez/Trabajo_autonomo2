Algoritmo Ahorcado
	
    Definir palabraSecreta, palabraAdivinada, usadas, entrada, letra, nuevo Como Cadena
    Definir intentos, i, indice, largo, dificultad Como Entero
    Definir encontrada, repetida Como Logico
	
    Dimension facil[10]
    Dimension normal[10]
    Dimension dificil[10]

    facil[1] <- "sol"
    facil[2] <- "gato"
    facil[3] <- "casa"
    facil[4] <- "perro"
    facil[5] <- "uva"
    facil[6] <- "luna"
    facil[7] <- "foca"
    facil[8] <- "nube"
    facil[9] <- "flor"
    facil[10] <- "tren"
	
    normal[1] <- "teclado"
    normal[2] <- "computadora"
    normal[3] <- "escritorio"
    normal[4] <- "bicicleta"
    normal[5] <- "murcielago"
    normal[6] <- "ecuador"
    normal[7] <- "montana"
    normal[8] <- "astronauta"
    normal[9] <- "programacion"
    normal[10] <- "internet"
	
    dificil[1] <- "otorrinolaringologo"
    dificil[2] <- "desoxirribonucleico"
    dificil[3] <- "esternocleidomastoideo"
    dificil[4] <- "ventrilocuo"
    dificil[5] <- "hiperbaton"
    dificil[6] <- "paralelepipedo"
    dificil[7] <- "electroencefalograma"
    dificil[8] <- "tergiversacion"
    dificil[9] <- "idiosincrasia"
    dificil[10] <- "inconmensurable"
	
    Escribir "Selecciona dificultad:"
    Escribir "1. Fácil"
    Escribir "2. Normal"
    Escribir "3. Difícil"
    Leer dificultad
	
    Segun dificultad Hacer
		
        1:
            indice <- Azar(10)
            Si indice = 0 Entonces
                indice <- 1
            FinSi
            palabraSecreta <- facil[indice]
			
        2:
            indice <- Azar(10)
            Si indice = 0 Entonces
                indice <- 1
            FinSi
            palabraSecreta <- normal[indice]
			
        3:
            indice <- Azar(10)
            Si indice = 0 Entonces
                indice <- 1
            FinSi
            palabraSecreta <- dificil[indice]
			
        De Otro Modo:
            Escribir "Dificultad no válida. Se selecciona NORMAL."
            indice <- Azar(10)
            Si indice = 0 Entonces
                indice <- 1
            FinSi
            palabraSecreta <- normal[indice]
			
    FinSegun
		
    palabraAdivinada <- ""
    largo <- Longitud(palabraSecreta)
	
    Para i <- 1 Hasta largo
        Si SubCadena(palabraSecreta, i, i) = " " Entonces
            palabraAdivinada <- palabraAdivinada + " "
        Sino
            palabraAdivinada <- palabraAdivinada + "_"
        FinSi
    FinPara
	
    intentos <- 6
    usadas <- ""
	
    Mientras intentos > 0 Y palabraAdivinada <> palabraSecreta
		
        Escribir ""
        Escribir "PALABRA: ", palabraAdivinada
        Escribir "Intentos restantes: ", intentos
        Escribir "Letras usadas: ", usadas
        Escribir ""
		
        DibujarAhorcado(intentos)
        Escribir ""
        Escribir "Ingresa una letra o la palabra completa:"
        Leer entrada
		
        Si Longitud(entrada) > 1 Entonces
            Si entrada = palabraSecreta Entonces
                palabraAdivinada <- palabraSecreta
            Sino
                intentos <- intentos - 1
                Escribir "Incorrecto."
            FinSi
			
        Sino
			
            Si Longitud(entrada) <> 1 Entonces
                Escribir "Ingresa solo UNA letra -_-."
            Sino
				
                letra <- entrada
                repetida <- Falso
				
                Para i <- 1 Hasta Longitud(usadas)
                    Si SubCadena(usadas, i, i) = letra Entonces
                        repetida <- Verdadero
                    FinSi
                FinPara
				
                Si repetida Entonces
                    Escribir "Esta letra ya la usaste ponte once."
					
                Sino
					
                    usadas <- usadas + letra
                    encontrada <- Falso
                    nuevo <- ""
					
                    Para i <- 1 Hasta largo
						
                        Si SubCadena(palabraSecreta, i, i) = " " Entonces
                            nuevo <- nuevo + " "
                        Sino
                            Si SubCadena(palabraSecreta, i, i) = letra Entonces
                                nuevo <- nuevo + letra
                                encontrada <- Verdadero
                            Sino
                                nuevo <- nuevo + SubCadena(palabraAdivinada, i, i)
                            FinSi
                        FinSi
						
                    FinPara
					
                    palabraAdivinada <- nuevo
					
                    Si encontrada Entonces
                        Escribir "Correcto."
                    Sino
                        intentos <- intentos - 1
                        Escribir "Incorrecto."
                    FinSi
					
                FinSi
				
            FinSi
			
        FinSi
		
    FinMientras
	
    Escribir ""
    DibujarAhorcado(intentos)
	
    Si palabraAdivinada = palabraSecreta Entonces
        Escribir "¡GANASTE! La palabra era: ", palabraSecreta
    Sino
        Escribir "PERDISTE. La palabra era: ", palabraSecreta
    FinSi
	
FinAlgoritmo

SubProceso DibujarAhorcado(intentos)
	
    Segun intentos Hacer

        6:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
			
        5:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
            Escribir "     |"
			
        4:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
            Escribir "    /|"
			
        3:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
            Escribir "    /|\"
			
        2:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
            Escribir "    /|\"
            Escribir "    / \"
			
        1:
            Escribir "__________"
            Escribir "     |"
            Escribir "     |"
            Escribir "     O"
            Escribir "    /|\"
            Escribir "    / \"
            Escribir "   GAME OVER"
			
    FinSegun
	
FinSubProceso
