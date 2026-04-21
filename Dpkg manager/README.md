Laboratório: Gerenciado pacotes com a ferramenta DPKG

Esse laboratório descreve o processo e analise de como funciona o DPKG e seus parâmetros. 

 1. Conceitos fundamentais: DPKG é uma ferramenta de baixo nível, diferente do APT, ele não entende repósitorios, ele só instala, remove, mantém e gerencia pacotes já instalados na máquina.

Para visualizar a onde os pacotes .deb são armazenados quando o comando apt install é utilizado usa-se o comando:

* ls /var/cache/apt/archives

![ls](../Imagens/dpkg/cache.png)

1.1 Análise e entendimento da saída ls. Com base na execução do comando, identificamos:

Arquivos .deb: Pacotes compactados que foram baixados

O Debian guarda esses arquivos por dois motivos principais:

I- Reinstalação rápida: Se você desinstalar um pacote e quiser instalá-lo de novo daqui a cinco minutos, o apt não vai gastar internet. Ele vai olhar nessa pasta, ver que o .deb já está lá e instalar instantaneamente.

II - Segurança em atualizações: Se uma atualização falhar, você ainda tem os pacotes baixados ali para tentar entender o que aconteceu ou reinstalar manualmente via dpkg.

 2. Intalando pacote e gerenciado com DPKG

Para um ambiente mais controlado, um pacote foi baixado em /root, mas vale ressaltar que não é uma boa prática para o dia a dia. Para baixar um pacote utiliza-se o comando:

* apt download [pacote]

![download](../Imagens/dpkg/apt_download.png)

2.1 Análise e entendimento da saída apr download. Com base na execução do comando, observamos:

- Downalod efetuado, mas a instalação automática com pacote não foi executada.
- Após a execução do comando foi emitido um warning na tela.

O motivo do aviso é porque durante o download de pacotes, o apt utiliza o usuário restrito _apt, reduzindo privilégios como medida de segurança para mitigar possíveis impactos de conteúdos maliciosos.

Entretanto, ao armazenar o pacote em /root, o usuário _apt não possui permissões de escrita nesse diretório. Como consequência, o processo é assumido pelo próprio apt com privilégios elevados, gerando um warning indicando que o mecanismo padrão de isolamento (sandbox) não pôde ser aplicado.

 3. Gerenciado o pacote com DPKG

Com o pacote no sistema, é possível gerenciar ele com alguns parâmetros. Para saber sobre todos os parâmetros possíveis, execute o comando man dpkg. Os parâmetros utilizados nesse laboratório foram:

-c
-i
-l
-L
-s

3.1 Utilizando -c 

* dpkg -c levee_4.0-2_amd64.deb

![download](../Imagens/dpkg/dpkg_content.png)


