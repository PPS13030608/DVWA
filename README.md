# DVWA (Damn Vulnerable Web Application)
​DVWA, siglas de Damn Vulnerable Web Application, es una aplicación web desarrollada en PHP y MySQL, intencionadamente vulnerable, diseñada con fines educativos y de formación en ciberseguridad. Su propósito principal es proporcionar un entorno legal y controlado donde profesionales de seguridad, desarrolladores y estudiantes puedan practicar la identificación y explotación de vulnerabilidades comunes en aplicaciones web.

![image](https://github.com/user-attachments/assets/60423b60-f515-490e-a8ac-90655f6fbb9a)

## BRUTE FORCE
**Low - Medium**

Tanto para low como para medium se utilizará la herramienta Wfuzz, una herramienta de código abierto diseñada para realizar pruebas de seguridad en aplicaciones web mediante técnicas de fuzzing y fuerza bruta.

```
wfuzz -c -w ~/rockyou.txt -b 'security=low; PHPSESSID=597da9h9uloefbmug1beair2js' 'http://127.0.0.1/DVWA/vulnerabilities/brute/index.php?username=admin&password=FUZZ&Login=Login'
```
Tendremos que fijarnos en la longitud de Chars para poder elegir la contraseña correcta.

![image](https://github.com/user-attachments/assets/2f1dd5d9-3b7d-4343-ad43-afac71e7fcc2)

![image](https://github.com/user-attachments/assets/7077bef2-f97e-493a-b95b-4b3718ca9606)

## COMMAND INJECTION
**Low**

Probamos a injectar comandos en el cuadro de texto y obtenemos lo siguiente:
```
127.0.0.1; ls
```
![image](https://github.com/user-attachments/assets/e64e9898-f2e2-4683-ab19-71c15aa36e25)

**Medium**

Si observamos el código de la página, podemos ver los carácteres que se sustituyen para prevenir injecciones de comandos.

![image](https://github.com/user-attachments/assets/35445459-7b8d-49f0-b4f6-cb37c0f06410)

Solo queda utilizar comandos que no estén definidos para prevenir injeccioines de comandos.

![image](https://github.com/user-attachments/assets/9cdb9943-d4f7-4bc6-b50e-c16ab800fded)

## CSRF
**Low**

Al cambiar la contraseña, se mostrará en la uri del navegador, pudiendo modificarse directamente desde ahí. 

![image](https://github.com/user-attachments/assets/dbc20a68-9eec-48b6-8819-5e1ee3041893)

![image](https://github.com/user-attachments/assets/1debde71-6d8a-4917-9af1-3d985cd15c7b)

