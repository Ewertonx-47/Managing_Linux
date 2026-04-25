Laboratório: Gerenciando pacotes com a ferramenta DPKG

Esse laboratório descreve o processo e analise de como funciona o APT e seus parâmetros.

Conceitos fundamentais: Diferente do DPKG, que também é um gerenciador de pacotes, o APT ele é um sistema de Alto nível, ele consegue fazer o download, instalação, resolução de dependêcias do pacote, remoção, 
pesquisa por pacotes, limpa o cache local e etc. O APT para fazer atualização de cache e instalação dos pacotes, é necessário acesso a internet. 

Para visualizar a onde os pacotes .deb são armazenados quando o comando apt install é utilizado usa-se o comando:

ls /var/cache/apt/archives

![ls](../Imagens/dpkg/cache.png)

