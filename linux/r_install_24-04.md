# Instalando o R no Ubuntu 24.04

## Instalação do repositório

Execute o comando no Terminal:

`sudo nano /etc/apt/sources.list`

Para o Ubuntu 24.04, insira a linha abaixo abaixo da última linha do arquivo. 

`deb https://cloud.r-project.org/bin/linux/ubuntu noble-cran40/`

Salve com Ctrl+O e Ctrl+X.

Execute as linhas abaixo:

`wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc | sudo tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc`

`sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9`



Atualize os repositórios.

`sudo apt update`



## Instalando o R

No terminal:

`sudo apt install r-base r-base-dev`
