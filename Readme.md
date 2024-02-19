# Errores:
1. Falta de documentación en el proyecto (Archivo->Readme.md).
---
2. Violación de los principios de diseño del lenguaje( Separación entre la interfaz '*.h' y la implementacion '*.cpp').
---
3. Violación del DRY(Don't Repeat Yourself) No repetir el codigo que hemos escrito:
    ```
        do {
            ...
        } while (input != 'S' && input != 'N');
        tanquePocaAgua = (input == 'S');

        // Solicitar si la cisterna tiene poca agua
        do {
            ...
        } while (input != 'S' && input != 'N');
        cisternaPocaAgua = (input == 'S');

        // Solicitar si la turbina est� encendida
        do {
            ...
        } while (input != 'S' && input != 'N');
        turbinaEncendida = (input == 'S');
    ```
    ### Se puede hacer una función general para solicitarle al usuario los datos:
    ```
        bool solicitarDato( string pregunta ){
            char input;
            do {
                cout << pregunta + (S/N): ";
                cin >> input;
                input = toupper(input);
                system("cls");
            } while (input == 'S' && input != 'N');
            return (input == 'S');
        }
    ```
---
4. Violación del SRP( Single Responsibility Principle ) de los principios SOLID.
- La clase TurbinaControl realiza dos tareas, la obtención de datos del usuario y el control de la turbina,
para un mejor uso del código limpio modularizar esa clase en 2, una encargada en obtención de datos del usuario
y TurbinaControl solo se encargue del control de la turbina.
---
5. Separación de responsabilidades: cada modulo se deberia centrar en una única responsabilidad, recomendación es   separar el proyecto en modulos individuales como los mencionados en el .4, además de independizar el arhivo main y hacerlo lo mas legible y simple posible.
---
6. En este fragmento de código:
    ```
        bool solicitarDato( string pregunta ){
            char input;
            do {
                cout << pregunta + (S/N): ";
                cin >> input;
                input = toupper(input);
                system("cls");
            } while (input == 'S' && input != 'N');
            return (input == 'S');
        }
    ```
    **Le faltan validaciones como:**
    - El usuario no introduzca una cadena de caracteres ( problema solo lee el primero y el resto lo deja en memoria "buffer" y puede traer como consecuncia irregularidades en la posterior ejecución del código ).
    - De utilizar para la lectura el 'cin' se debería de realizar una limpieza del buffer antes y luego de la entrada. Recomendación trabajar con cin.get(), cin.getline(), cin.ignore().
---



