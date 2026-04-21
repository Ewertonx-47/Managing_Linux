Laboratório: Gerenciado pacotes com a ferramenta DPKG

Esse laboratório descreve o processo e analise de como funciona o DPKG e seus parâmetros. 

 1. Conceitos fundamentais: DPKG é uma ferramenta de baixo nível, diferente do APT, ele não entende repósitorios, ele só instala, remove, mantém e gerencia pacotes já instalados na máquina.

Para visualizar a onde os pacotes .deb são armazenados quando o comando apt install é utilizado usa-se o comando:

* ls /var/cache/apt/archives

![ls](../Imagens/dpkg/cache.png)

 2. Análise e entendimento da saída ls. Com base na execução do comando, identificamos:

Arquivos .deb: Pacotes compactados que foram baixados

O Debian guarda esses arquivos por dois motivos principais:

I- Reinstalação rápida: Se você desinstalar um pacote e quiser instalá-lo de novo daqui a cinco minutos, o apt não vai gastar internet. Ele vai olhar nessa pasta, ver que o .deb já está lá e instalar instantaneamente.

II - Segurança em atualizações: Se uma atualização falhar, você ainda tem os pacotes baixados ali para tentar entender o que aconteceu ou reinstalar manualmente via dpkg.

 3. Intalando pacote e gerenciado com DPKG

Para um ambiente mais controlado, um pacote foi baixado em /root, mas vale ressaltar que não é uma boa prática para o dia a dia. Para baixar um pacote utiliza-se o comando:

* apt download [pacote]

(imagem)



