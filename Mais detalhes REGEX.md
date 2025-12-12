## Resumo das REGEX.
\ - informar caractere imediatamente após;**(contra-barra)**.
^ - início da linha.
$ - fim da linha.
? - zero ou uma ocorrência do caracter são válidos.
* - zero, uma ou mais ocorrências válidas.
+ - pelo menos **uma** ou **mais ocorrências** são válidas.
(verde|amarelo) O **|(Pipeline)** representam o OU.
a{2} - procura por duas ocorrências do caractere 'a'.
a{2,5} - procura por duas ocorrências até cinco do caractere 'a' consecutivas.
[aeiou] - sequencia de caracteres dentro do colchete é interpretada como todos os caracteres individualmente são válidos na busca.
[a-z] - O sinal '-' indica intervalo entre A-Z.
[0-9] - Indica que qualquer número de zero a nove é válido para busca.
[^abc] - [^ dentro do range] Indica que qualquer caractere é válido para busca **menos^** 'a,b,c'.
/palavra/ - Indica que a palavra procurada deverá estar separada por espaços na esquerda e direita.(barra simples)
. - Indica que qualquer caractere é válidos, **menos uma linha em branco**. (ponto final)

### Entendendo a busca de endereço de IP com o grep -E(egrep).
- Busca de endereço de IP num arquivo de logs.
    `grep -E "[0-9]{3}\.[0-9]{3}\.[0-9].\{3}[0-9]{3}" messages`  
(ex. 255.255.255.255 ou 192.225.111.154)  
[] - range de alcance.  
{} - quantidade de repetição de caracteres.  
\ - obriga que se lê literalmente o **próximo caractere**.

-  Busca **mais correta** de endereço de IP de tamanhos variados separados por **.ponto**.
    `grep -E "[0-9]{1,3}\.[0-9]{1,3}\.[0-9].\{1,3}[0-9]{1,3}" messages`  
(ex. 255.255.255.255 ou 192.225.111.154 ou 1.1.1.1 ou 8.8.8.8)  

### Exemplos prático com o uso da acentuação gráfica no REGEX.



#### Aspas Simples e Duplas no Bash. 
[Link](https://caiosantesso.dev/bash-aspas-simples-e-duplas/)