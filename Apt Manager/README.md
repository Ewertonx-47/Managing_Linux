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

Os pacotes .deb ficam armazenado em repositórios e disponíveis para ser utilizados conforme a necessidade do usuário. Um exemplo de repositório é o http://deb.debian.org/debian. quando o sistema é instalado na máquina, ele não faz o download/instalação de todos os pacotes disponíveis no mundo, pois é algo inviável. O que ele mantém localmente é uma base de dados (cache) com informações sobre os pacotes. O diretório principal é o /var/lib/apt/lists/. Dentro desse diretório existe os índices dos pacotes, esses índices são São arquivos de texto (compactados) que contêm informações como: Nome do pacote, versão disponível, dependências, descrição e
URL de download. Para visualizar o contéudo, usaremos o comando:

* cd /var/lib/apt/lists/
* ls -l lists

(imagem) 

Analisando a saída do comando ls -l, podemos observar as seguintes informações:

deb.debian.org_debian_dists_trixie_main_binary-amd64_Packages - A lista de TODOS os pacotes disponíveis no repositório main para arquitetura amd64 

deb.debian.org
→ servidor

debian_dists_trixie
→ distribuição

main
→ seção

binary-amd64
→ arquitetura

Packages
→ lista de pacotes

A saída também mostra a lista de outros pacotes com outros objetivos, por exemplo o deb.debian.org_debian_dists_trixie_InRelease que contém metadados do repositório, assinatura e GPG (segurança). 

2.1 Verificando as informções de um pacote em /var/lib/apt/lists/

Dentro do arquivo deb.debian.org_debian_dists_trixie_main_binary-amd64_Packages existe uma enorme quantidade de informações sobre diversos pacotes. Para verificar o índice de um pacote especifíco, usa-se o comando:

* cat deb.debian.org_debian_dists_trixie_main_binary-amd64_Packages | grep [pacote]

(imagem)

A saída do comando cat juntamente com o comando grep mostrou o índice que o apt consulta na instalação do pacote levee. Esses índices são: Package, homepage e filename. São essas as informações básicas que o apt precisapara ir até o repositório e fazer o download e instalação do pacote .deb levee. 

2.2 

