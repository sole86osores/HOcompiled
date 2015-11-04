1)Escriban qué esperan de cada uno de los pasos

1-Pre-procesador: make preprocessing
2-Compilacion I: make assembler
3-Compilacion II: make object
4-Linkeo: make executable

1-Ejecutará:
gcc -E calculator.c -o calculator.pp.c  
Generará el archivo calculator.pp.c en donde tendrá las caracterisitcas de la funcion pero no la operacion de la misma.

2- Ejecutará:
gcc -S calculator.c -o calculator.asm
Generará el archivo .asm donde guarda las instrucciones en lenguaje assembler.

3- Ejecutará: 
gcc -C calculator.c -o calculator.o
Generará un archivo .o donde transformó las instrucciones del paso anterior a binario (código de máquina).

4-Ejecutará:
gcc -v calculator.o -o calculator.e
Generará un archivo .e que es finalmente el ejecutable.

2) ¿Qué agregó el preprocesador?
Agregó todo los headers del stdio.h y luego lo de calculator.h.

3)Identificar en la rutina de assembler las funciones
Funcion main:
main:
.LFB2:
        push    rbp
.LCFI0:
        mov     rbp, rsp
.LCFI1:
        sub     rsp, 32
.LCFI2:
        mov     DWORD PTR [rbp-20], edi
        mov     QWORD PTR [rbp-32], rsi
        mov     esi, 11
        mov     edi, 31
        call    add_numbers
        mov     DWORD PTR [rbp-4], eax
        mov     esi, DWORD PTR [rbp-4]
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf
        mov     eax, 0
        leave
        ret


Funcion add_numbers:

add_numbers:
.LFB3:
        push    rbp
.LCFI3:
        mov     rbp, rsp
.LCFI4:
        mov     DWORD PTR [rbp-4], edi
        mov     DWORD PTR [rbp-8], esi
        mov     edx, DWORD PTR [rbp-8]
        mov     eax, DWORD PTR [rbp-4]
        add     eax, edx
        leave
        ret


4) Explicar qué quieren decir los símbolos que se crean en el objeto
Al hacer
nm calculator.o
000000000000003a T add_numbers
0000000000000000 T main
                 U printf


T=texto
U=undifined
Mayúscula quiere decir que puedo tener acceso desde afuera.

5)¿En qué se diferencian los símbolos del objeto y del ejecutable?
En el caso del objeto los simbolos describen solo main, add_numbers y printf.
En el caso del ejecutable los simbolos describen todo lo que se linkea que es necesario para ejecutar. 
