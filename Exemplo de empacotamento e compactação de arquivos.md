**Tar** é um compactador?
**Não.** É um comando para juntar(agrupar) arquivos e diretórios em um único arquivo, muito utilizado para backup. Apesar disso por ser usado em conjunto com algum compactador disponível no sistema como o gzip(z), bzip2(j) ou xz.


## tar + gzip (.tar.gz ou .tgz) MENOS LEVE
**Compactar**
```console
tar -czvf arquivo.tar.gz pasta_ou_arquivos/
```
**c** = create
**z** = gzip
**v** = verbose
**f** = file

**Descompactar**
```console
tar -xzvf arquivo.tar.gz
```

## tar + bzip2 (.tar.bz2) MODERADO
**Compactar**  
```console
tar -cjvf arquivo.tar.bz2 pasta_ou_arquivos/
```  

**j = bzip2**  

**Descompactar**
```console
tar -xjvf arquivo.tar.bz2
```  

## tar + xz (.tar.xz)  MAIS LEVE
**Compactar**
```console
tar -cJvf arquivo.tar.xz pasta_ou_arquivos/
```

**J** = xz

**Descompactar**
```console
tar -xJvf arquivo.tar.xz
```  

## Níveis de compressão.
![Níveis de compressão.](/images/niveisdecompressao.png "Informações úteis.")

> O **tar** é uma ferramenta de **enpacotamento** ao passo que o **bzip, gzip e xz** são ferramentas de **compressão**.