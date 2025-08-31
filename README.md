# Tutorial de Instalação do Wine e do Lattice Propel

Este guia mostra como instalar o **Wine** no Ubuntu/Debian e em seguida configurar o **Lattice Propel** com licença.

---

## Preparação

Se o seu sistema for **64 bits**, habilite a arquitetura de **32 bits**:

```bash
sudo dpkg --add-architecture i386
```

Verifique o nome da sua distribuição (codename):

- Copiar código


```bash
cat /etc/os-release
```
Procure pela linha UBUNTU_CODENAME ou VERSION_CODENAME.
Use o valor que aparecer após o =.

## Adicionar o repositório do WineHQ

1. Baixar e adicionar a chave do repositório

- Copiar código

```bash
sudo mkdir -pm755 /etc/apt/keyrings
wget -O - https://dl.winehq.org/wine-builds/winehq.key | sudo gpg --dearmor -o /etc/apt/keyrings/winehq-archive.key
```

2. Adicionar o repositório conforme a sua distribuição

Se o nome da sua distribuição não estiver listado, pacotes antigos podem estar disponíveis no servidor de downloads.

Distribuição	Comando

```bash
Ubuntu 25.04 (plucky)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/plucky/winehq-plucky.sources
Ubuntu 24.04 / Linux Mint 22 (noble)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/noble/winehq-noble.sources
Ubuntu 22.04 / Linux Mint 21.x (jammy)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
Debian Testing (forky)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/debian/dists/forky/winehq-forky.sources
Debian 13 (trixie)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/debian/dists/trixie/winehq-trixie.sources
Debian 12 (bookworm)	sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/debian/dists/bookworm/winehq-bookworm.sources
```

Atualize a lista de pacotes:


- Copiar código

```bash
sudo apt update
```

## Instalar o Wine

Você pode instalar um dos seguintes ramos:

Wine branch	Comando
Stable branch	sudo apt install --install-recommends winehq-stable
Development branch	sudo apt install --install-recommends winehq-devel
Staging branch	sudo apt install --install-recommends winehq-staging

Exemplo (instalação do Staging branch):


- Copiar código

```bash
sudo apt install --install-recommends winehq-staging
```

## Instalar o Lattice Propel

Baixe o Lattice Propel no site oficial:
👉 https://www.latticesemi.com/LatticePropel

Execute a instalação com o Wine.

Configure a licença:

Descubra o seu MAC Address:


- Copiar código

```bash
ifconfig
```

Gere a licença no site da Lattice e baixe o arquivo license.dat (recebido por e-mail).

Salve o arquivo em:

- Copiar código

```bash
/home/werlley/.wine/drive_c/lscc/propel/2025.1/builder/rtf/license/license.dat
```

## Corrigindo atalhos .desktop

Após a instalação, os atalhos criados na Área de Trabalho podem não abrir.


Corrija as permissões:


- Copiar código

```bash
chmod +x ~/Área\ de\ trabalho/*.desktop
```

Marque como confiáveis no GNOME/Nautilus:


- Copiar código

```bash
gio set ~/Área\ de\ trabalho/Lattice\ Propel\ Builder\ 2025.1.desktop metadata::trusted true
gio set ~/Área\ de\ trabalho/Lattice\ Propel\ 2025.1.desktop metadata::trusted true
```

### Para o Diamond 3.14 e o Diamond Programmer 3.14, basta aplicar os mesmos passos ajustando os nomes dos arquivos .desktop.

1. Dar permissão de execução
   
```bash
chmod +x ~/Área\ de\ trabalho/Diamond\ 3.14.desktop
chmod +x ~/Área\ de\ trabalho/Diamond\ Programmer\ 3.14.desktop
```

2. Marcar como confiáveis no Nautilus/GNOME
3. 
```bash
gio set ~/Área\ de\ trabalho/Diamond\ 3.14.desktop metadata::trusted true
gio set ~/Área\ de\ trabalho/Diamond\ Programmer\ 3.14.desktop metadata::trusted true
```

## Executar em tela cheia

Opção 1 — Configurar pelo Wine
Abra o Wine Configuration:


- Copiar código

```bash
winecfg
```

Vá na aba Graphics (Gráficos).

Marque “Emular um desktop virtual”.

Informe a resolução exata da sua tela.

Exemplo: se seu notebook for 1366x768, use essa resolução (não 1920x1080).

Para descobrir sua resolução atual:


- Copiar código

```bash
xrandr | grep '*'
```

## Conclusão
Agora o Wine está instalado e o Lattice Propel Builder configurado, com licença válida e atalhos corrigidos no Ubuntu/Debian.
