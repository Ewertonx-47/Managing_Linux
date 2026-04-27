Laboratório: Gerenciando pacotes com a ferramenta APT

Esse laboratório descreve o processo e analise de como funciona o APT e seus parâmetros.

 1. Conceitos fundamentais: O APT é um gerenciador de pacotes igual o DPKG, porém existem diferenças entre eles. Diferente do DPKG, o APT é um sistema de alto nível, ele faz buscas em repositórios, baixa, instala, atualiza, mantém e remove pacotes. O APT também faz a resolução de dependências, isso quer dizer que se o pacote instalado precisar de outro pacote, o APT instalado esse outro pacote antes também.

Para visualizar a onde os pacotes .deb são armazenados quando o comando apt install é utilizado usa-se o comando:

* ls /var/cache/apt/archives

![cache](../Imagens/dpkg/cache.png)

1.1 Análise e entendimento da saída ls. Com base na execução do comando, identificamos:

Arquivos .deb: Pacotes compactados que foram baixados

O Debian guarda esses arquivos por dois motivos principais:

I- Reinstalação rápida: Se você desinstalar um pacote e quiser instalá-lo de novo daqui a cinco minutos, o apt não vai gastar internet. Ele vai olhar nessa pasta, ver que o .deb já está lá e instalar instantaneamente.

II - Segurança em atualizações: Se uma atualização falhar, você ainda tem os pacotes baixados ali para tentar entender o que aconteceu ou reinstalar manualmente via dpkg.

 2. Entendendo a estrutura dos pacotes .deb

Os pacotes .deb ficam armazenado em repositórios e disponíveis para ser utilizados conforme a necessidade do usuário. Um exemplo de repositório é o http://deb.debian.org/debian. quando o sistema é instalado na máquina, ele não faz o download/instalação de todos os pacotes disponíveis no mundo, pois é algo inviável. 
