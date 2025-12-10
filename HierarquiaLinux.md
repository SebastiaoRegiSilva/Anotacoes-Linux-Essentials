
### 1- Hierarquia Linux?
![HierarquiaLinux.](/images/hierarquiaLinux.png "Exemplo da hierarquia Linux.")

## Quais os diretórios da estrutura de arquivos do LINUX e quais suas funções
* **/bin** - contém os binários de forma geral;
* **/boot** - arquivos para carga do OS como a imagem de Kernel;
* **/dev** - pseudo file system. Abstração de hardware na forma de arquivo. Facilita a manutenção do dispositivos;
* **/etc** - contém arquivos de configuração do sistema;
* **/home** - diretório do usuário;
* **/lib** - contém as bibliotecas essenciais do sistema;
* **/mnt** - serve para montar dispositivos removíveis;
* **/opt** - serve para guardar softwares de terceiros;
* **/proc** - outro pseudo file system que serve para guardar informações do kernel para apresentar aos usuários;
* **/root** - home do superusuário. Pode existir ou não;
* **/sbin** - contém comandos de manutenção e supervisão do usuário;
* **/tmp** - contém arquivos temporários;
* **/usr** - contém recursos de sistema LINUX. Pode ser compartilhado entre outros sistemas;
* **/var** - informações variáveis. Log, caixa postal...
## Resumo.

- Quais são os principais arquivos e diretórios do Linux?
    - Essenciais ao sistema: /boot, /bin, /sbin e /etc;
    - Diretório Home: /home, /root;
    - Pseudo-filesystem: /proc, /dev;
    - Pontos de montagem: /mnt, /media;
    - Bibliotecas e módulos do kernel: /lib e /lib64;
    - Serviços do Sistema: /srv;
    - Arquivos variáveis: /var;
    - Arquivos de usuário: /usr;
    - Arquivos temporários: /tmp;
    - Programas de Terceiros: /opt.