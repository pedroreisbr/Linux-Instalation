Linux-Instalation
=================

#Processo de configuração da maquina pessoal Linux Ubuntu Gnome 14.04

- Instalar modo normal, com atualizaćão

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
    
