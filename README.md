Linux-Instalation
=================

#Processo de configuração da maquina pessoal Linux Ubuntu Gnome 14.04

- Instalar modo normal, com atualização

- Atualizar sistema
    * `sudo apt-get update && sudo apt-get upgrade`
    * Software Update
   
- Instalar Driver Placa de Vídeo Nvidia GeForce 660M com Bumblebee
    * Executar os seguintes comandos
        * http://www.themukt.com/2014/06/13/howto-install-nvidia-331-bumblebee-optimus-cards-ubuntu/
        * `sudo apt-get install linux-headers-generic`
        * `sudo apt-add-repository ppa:xorg-edgers/ppa`
        * `sudo apt-get update && sudo apt-get upgrade`
        * `sudo add-apt-repository ppa:bumblebee/stable`
        * `sudo apt-get update && sudo apt-get install bumblebee bumblebee-nvidia primus`
        * `sudo apt-get install nvidia-331`
        * `sudo gedit /etc/bumblebee/bumblebee.conf`
           * Driver=nvidia
           * KernelDriver=nvidia-331
           * LibraryPath=/usr/lib/nvidia-331:/usr/lib32/nvidia-331
           * XorgModulePath=/usr/lib/nvidia-331/xorg,/usr/lib/xorg/modules
        * `sudo apt-get install --reinstall bbswitch-dkms`
        * `sudo /etc/init.d/bumblebeed stop` or `sudo stop bumblebeed`
        * `sudo /etc/init.d/bumblebeed start` or `sudo start bumbleed`
        * `sudo reboot`
    * Testar placa de video
        * http://sourceforge.net/projects/virtualgl/
        * Baixar e instalar VirtualGL
        * `cd /opt/VirtualGL/bin/`
        * `./glxspheres64`
        * `optirun ./glxspheres64`
            * Comparar taxa de FPS dos dois casos. Se a placa tiver funcionando o segundo comando terá desempenho superior.
    * Instalar o Bumblebee GUI para gerenciar aplicativos para ser aberto usando nVidia
        * http://askubuntu.com/questions/452556/how-to-set-up-nvidia-optimus-bumblebee-in-14-04
        * `sudo apt-get install python-appindicator`
        * `sudo apt-get install git`
        * `mkdir git && cd git`
        * `git clone https://github.com/Bumblebee-Project/bumblebee-ui.git`
        * `cd bumblebee-ui`
        * `sudo ./INSTALL`
        * `cd ../.. && rm -R -f git`
    * Criar lançador GlxSpheres64
        * `cd /usr/share/applications`
        * `sudo touch glxspheres.desktop`
        * `sudo gedit glxspheres.desktop`
```
[Desktop Entry]
Name=GlxSpheres64
Comment=An application test FPS performance Video Driver
Exec=/opt/VirtualGL/bin/glxspheres64
Icon=bumblebee
Type=Application
Categories=GNOME;GTK;
```
        * Open 'Bumblebee - Applications Settings'
        * Marque GlxSpheres64
        * Click 'Apply Now'
        * Click 'Configure Aplications'
        * Altere 'Mode' para 'Performance' e Click 'Close'
        
- Configurar Teclado Padrão internacional (não funcionava o ç, ficava ć)
   * `sudo gedit /etc/enviroment`
   * Adicione as linhas, salve e reinicie a seção
```
GTK_IM_MODULE=cedilla
QT_IM_MODULE=cedilla
```

- Reparar AutoComplete do Bash que parou de funcionar corretamente
   * `sudo apt-get install --reinstall bash-completion`
   * `cp /etc/skel/.bashrc ~/`

- Instalar Gnome Do (para pesquisas rápidas por aplicativos) e o Docky (para acessorádo de Aplicativos)
   * `sudo apt-get install gnome-do docky`

- Instalar Fish (Auxiliar do Bash)
   * `sudo apt-get install fish` 

- Instalar Google Chrome - https://www.google.com.br/chrome/browser/desktop/index.html

- 
