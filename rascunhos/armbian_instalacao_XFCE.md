`![banner](https://github.com/lnrddev/tvbox/blob/e7b7d6d542bb173f9e0e779bbf335d0e98095b51/images/area_trabalho_padrao.png)

# **Configuração como estação de trabalho (workstation)**

## **Alertas**

1. Estes protocolos foram testados em várias unidades sem nenhuma ocorrência negativa. Leia-os completamente antes de realizar qualquer procedimento para que não haja qualquer dúvida a respeito.
2. Há o risco eventual de travamento e/ou perda da sua TV Box caso haja algum problema mais severo. Use por seu próprio risco. Não nos responsabilizamos por nenhum dano.
3. Se o Armbian estiver instalado no seu pendrive ou cartão de memória, pode ser necessário aumentar o tamanho da partição de instalação para que seja possível baixar e instalar todos os aplicativos. Sugere-se o uso do Gparted em ambiente Linux para maior facilidade. Uma partição de 4 Gb normalmente é suficiente para a instalação.  Se estiver trabalhando diretamente na sua TV Box após a instalação, não é necessária tal ação.

## Ambiente gráfico XFCE mínimo

`sudo apt install xfce4-panel xfce4-session xfwm4 xfdesktop4 xfce4-settings xfce4-terminal thunar xserver-xorg-core xserver-xorg-video-fbdev xinit lightdm lightdm-gtk-greeter xserver-xorg-input-libinput xserver-xorg-input-all --no-install-recommends`

## Navegador Chromium

`sudo apt install chromium chromium-l10n`

Reinicie a máquina, faça o login e aguarde a interface gráfica do XFCE abrir.

## Funcionalidades do XFCE e Acessórios

`sudo apt install gvfs polkitd pkexec polkit-kde-agent-1 network-manager-gnome thunar mousepad ristretto qpdfview xarchiver xfce4-screenshooter xfce4-taskmanager galculator xfce4-screensaver xfce4-pulseaudio-plugin dconf-editor drawing`

## Instalação do LibreOffice

`sudo apt install libreoffice-writer libreoffice-calc libreoffice-impress libreoffice-l10n-pt-br libreoffice-help-pt-br ttf-mscorefonts-installer`

## Drivers gráficos e acessórios

`sudo apt install ffmpeg gstreamer1.0-fdkaac gstreamer1.0-libav gstreamer1.0-plugins-base-apps gstreamer1.0-vaapi gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly lame libavcodec-extra libavcodec-extra59 libavdevice59 libgstreamer1.0-0 sox twolame vorbis-tools mpv vlc`

## Arquivo xorg.conf

Para ativar o driver Mesa/Lima, alterar o arquivo /etc/X11/xorg.conf inserindo as informações a seguir.

```
Section "ServerFlags"
        Option  "AutoAddGPU" "off"
        Option "Debug" "dmabuf_capable"
 EndSection

 Section "OutputClass"
        Identifier "Lima"
        MatchDriver "<display DRM driver>"
        Driver "modesetting"
        Option "PrimaryGPU" "true"
 EndSection
```

Você deve substituir ```"<display DRM driver>"``` com seu respectivo driver, a depender de seu SoC:

* Allwinner: sun4i-drm
* Amlogic: meson
* Ericsson MCDE: mcde
* Exynos: exynos
* Rockchip: rockchip
* Tinydrm: tinydrm

Fonte: https://en.opensuse.org/ARM_Mali_GPU
