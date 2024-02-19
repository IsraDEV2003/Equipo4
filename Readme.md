## Errores:
1. Falta de documentación (Archivo->Readme.md).
---
2. Violación de los principios de diseño( Separación entre la interfaz '*.h' y la implementacion '*.cpp').
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
    # Se puede hacer una función general para solicitarle al usuario los datos:
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
4. 


