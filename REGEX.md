## Regular Expression.
- Um regex é um método formal de se especificar um padrão de texto a ser procurado em um ou mais arquivos.
* Úteis na busca e validação de textos como:
  * Número de endereço de IP;
  * Endereço de e-mail;
  * Endereço de Internet(**URL**);
  * Dados na coluna em um texto;
  * Dados que estão entre tags<tags></tags>;
  * Número de NPC, NIF, NISS e etc;
  * Data e horário.
## Diferença entres os **greps**:
- grep: pode ser usado para procurar expressões regulares simples;
 - grep: procura usando expressões regulares (BRE - basic regular expressions). Pode também receber opções como `-E` para ERE ou `-P` para PCRE (quando suportado).

 - egrep: histórico para "extended grep" — usa ERE (expressões regulares estendidas). Equivalente a `grep -E`.

 - fgrep: busca por strings literais (sem interpretação de metacaracteres). Equivalente a `grep -F`. Mais rápido para padrões fixos.

 Observação: `egrep` e `fgrep` são nomes legados; prefira `grep -E` e `grep -F` para consistência.

 ## Exemplos práticos

 Exemplo de arquivo de teste (`exemplo.log`):

 ```text
 [INFO] Servidor iniciado em 10.0.0.1
 [ERROR] falha ao abrir /var/log/app.log
 user: maria@example.com
 ip=192.168.0.10
 2025-12-11 10:00:00 backup concluído
 ```

 - **Busca literal (grep/fgrep):** procura por linhas que contenham a palavra `ERROR`.

   `grep "ERROR" exemplo.log`

   Ou, usando fixed-strings (mais rápido para buscas literais):

   `grep -F "ERROR" exemplo.log`  # mesmo que `fgrep "ERROR" exemplo.log`

 - **Busca com número da linha e ignorando maiúsculas/minúsculas:**

   `grep -n -i "error" exemplo.log`

 - **Alternância (ou) com ERE — `egrep` / `grep -E`:** procura por `error` ou `falha` (case-insensitive).

   `egrep -n -i "error|falha" exemplo.log`
    ### ou
   `grep -E -n -i "error|falha" exemplo.log`

 - **Expressão para IP (ERE):** encontra endereços IPv4 simples com `egrep`/`grep -E`:

   `egrep -o "[0-9]{1,3}(\.[0-9]{1,3}){3}" exemplo.log`

   `-o` mostra somente a parte que casa com o padrão.

 - **Datas com BRE (grep) ou ERE (grep -E):** usando BRE (note as chaves escapadas em BRE):

   `grep "^[0-9]\{4\}-[0-9]\{2\}-[0-9]\{2\}" exemplo.log`

   Com ERE (`grep -E`) as chaves não precisam ser escapadas:

   `grep -E "^[0-9]{4}-[0-9]{2}-[0-9]{2}" exemplo.log`

 - **Buscas por múltiplos padrões (arquivo de padrões) com `-f`:** crie `patterns.txt` com linhas como:

   ```text
   ERROR
   maria@example.com
   backup concluído
   ```

   E então rode:

   `grep -F -f patterns.txt exemplo.log`  # usa strings fixas

 - **Exemplo com quantificadores e grupos (ERE):** encontrar 1 ou mais dígitos seguidos por `backup`:

   `egrep -i "[0-9]+\s+backup" exemplo.log`

 - **Busca recursiva em diretórios:**

   `grep -R "ERROR" /var/log/`  # procura recursivamente

 - **Usar PCRE (quando disponível):** `grep -P` permite lookarounds e outras features do PCRE:

   `grep -P "(?<=user:\s)\S+@\S+" exemplo.log`  # extrai o e-mail após 'user: '

 ## Dicas rápidas

 - **Quando usar `grep -F`/`fgrep`:** quando você tem padrões literais (sem regex) — é mais rápido e evita precisar escapar caracteres especiais.
 - **Quando usar `grep -E`/`egrep`:** para alternância (`|`), `+`, `?`, `{m,n}` sem escapes extras.
 - **Quando usar `grep` (BRE):** útil em scripts que assumem BRE; lembre-se de escapar `{}` e `+ ? |` se necessário.
 - **Prefira `grep -E` e `grep -F`** em ambientes modernos por clareza e portabilidade.

 ## Exemplos de uso prático rápido (linha de comando)

 - Mostrar linhas com `ERROR` e exibir número da linha:

   `grep -n "ERROR" exemplo.log`

 - Encontrar IPs no arquivo:

   `egrep -o "[0-9]{1,3}(\.[0-9]{1,3}){3}" exemplo.log`

 - Procurar vários termos listados em `patterns.txt` como strings literais:

   `grep -F -f patterns.txt exemplo.log`

 - Usar lookbehind com PCRE (se `grep` suportar `-P`):

   `grep -P -o "(?<=user:\s)\S+@\S+" exemplo.log`
 
 - Uso do `grep` para inverter resultado da pesquisa `-v`):

   `grep -v "bash$"` /etc/passwd  
 - Exibe todos os usuários do sistema que não tenham a última linha/coluna o valor bash, de forma invertida. 
