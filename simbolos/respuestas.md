1)identificar los símbolos ejecutando make object

Al realizar nm visibility.o se obtiene:

0000000000000000 t add_abs
000000000000002b T main
                 U printf
0000000000000000 r val1
0000000000000004 R val2
0000000000000000 d val3
0000000000000004 D val4


Minúsculas no admite acceso desde afuera y Mayuscula viceversa.

t T escritura
U undefined
r R read only
d D data


Al linkear el .o , el ejecutable tendrá la funcion printf undefined pero linkeada a donde esta localizada 