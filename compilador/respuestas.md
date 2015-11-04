1)Escriban qu� esperan de cada uno de los pasos

1-Pre-procesador: make preprocessing
2-Compilacion I: make assembler
3-Compilacion II: make object
4-Linkeo: make executable

1-Ejecutar�:
gcc -E calculator.c -o calculator.pp.c  
Generar� el archivo calculator.pp.c en donde tendr� las caracterisitcas de la funcion pero no la operacion de la misma.

2- Ejecutar�:
gcc -S calculator.c -o calculator.asm
Generar� el archivo .asm donde guarda las instrucciones en lenguaje assembler.

3- Ejecutar�: 
gcc -C calculator.c -o calculator.o
Generar� un archivo .o donde transform� las instrucciones del paso anterior a binario (c�digo de m�quina).

4-Ejecutar�:
gcc -v calculator.o -o calculator.e
Generar� un archivo .e que es finalmente el ejecutable.

2) �Qu� agreg� el preprocesador?
Agreg� todo los headers del stdio.h y luego lo de calculator.h.

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


4) Explicar qu� quieren decir los s�mbolos que se crean en el objeto
Al hacer
nm calculator.o
000000000000003a T add_numbers
0000000000000000 T main
                 U printf


T=texto
U=undifined
May�scula quiere decir que puedo tener acceso desde afuera.

5)�En qu� se diferencian los s�mbolos del objeto y del ejecutable?
En el caso del objeto los simbolos describen solo main, add_numbers y printf.
En el caso del ejecutable los simbolos describen todo lo que se linkea que es necesario para ejecutar. 
