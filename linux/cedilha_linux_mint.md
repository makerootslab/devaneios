
Observação: testado com sucesso em janeiro de 2026 no Linux Mint 22.3!

## Para o GTK 2 e 3

1. Edite os arquivos de configuração no GTK 2 e 3:

```
sudo nano /usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules.cache
sudo nano /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules.cache
```

Em ambos, procure as linhas que se iniciam com "cedilla" "Cedilla" e adicione :en à linha, de forma semelhante a isto:

`"cedilla" "Cedilla" "gtk30" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa:en"`

# Configurando o cedilha no Linux Mint 22.3

2. Altere o arquivo Compose:

`sudo sed -i /usr/share/X11/locale/en_US.UTF-8/Compose -e 's/ć/ç/g' -e 's/Ć/Ç/g'`

3. Instrua o sistema a carregar o módulo cedilla:

Adicione as linhas a seguir no arquivo `/etc/environment`:

```
GTK_IM_MODULE=cedilla
QT_IM_MODULE=cedilla
```
## Para o GTK 4

Crie um arquivo .XCompose no diretório do seu usuário:

`nano .XCompose`

Insiera o conteúdo abaixo:

```
# Overrides C acute with Ccedilla:
 <dead_acute> <C> : "Ç" "Ccedilla"
 <dead_acute> <c> : "ç" "ccedilla"
```

Execute o seguinte comando no terminal:

`gsettings set org.gnome.settings-daemon.plugins.xsettings overrides "{'Gtk/IMModule': <'ibus'>}"`

Reinicie o computador.

Fontes: 

1. https://superuser.com/questions/1075992/cedilla-under-c-%c3%a7-in-us-international-with-dead-keys-keyboard-layout-in-linu

2. https://www.danielkossmann.com/pt/ajeitando-cedilha-errado-ubuntu-linux/
