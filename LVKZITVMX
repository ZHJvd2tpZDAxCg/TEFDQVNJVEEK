#!/bin/bash
#COLORES
black="$(tput setaf 0)" && red="$(tput setaf 1)" && green="$(tput setaf 2)" && yellow="$(tput setaf 3)" && blue="$(tput setaf 4)" && magenta="$(tput setaf 5)" && cyan="$(tput setaf 6)" && white="$(tput setaf 7)" && rst="$(tput sgr0)"
instalador() {
  comando="$1"
  _=$(
    $comando >/dev/null 2>&1
  ) &
  >/dev/null
  pid=$!
  while [[ -d /proc/$pid ]]; do
    echo -ne " \033[1;33m|"
    for ((i = 0; i < 20; i++)); do
      echo -ne "\033[1;31m██"
      sleep 0.2
    done
    echo -ne "\033[1;33m|"
    sleep 1s
    echo
    tput cuu1
    tput dl1
  done
  echo -ne " \033[1;33m|\033[1;31m████████████████████████████████████████\033[1;33m| - \033[1;32m100%\033[0m\n"
  sleep 1s
}
msgi () {
    BLANCO='\033[1;37m' && ROJO='\e[1;31m' && VERDE='\e[32m' && AMARELO='\e[33m'
    AZUL='\e[34m' && MAGENTA='\e[35m' && MAG='\033[1;36m' && NEGRITA='\e[1m' && SINCOLOR='\e[0m'
    case $1 in
    -ne) cor="${ROJO}${NEGRITA}" && echo -ne "${cor}${2}${SINCOLOR}" ;;
    -ama) cor="${AMARELO}${NEGRITA}" && echo -e "${cor}${2}${SINCOLOR}" ;;
    -verm) cor="${AMARELO}${NEGRITA}[!] ${ROJO}" && echo -e "${cor}${2}${SINCOLOR}" ;;
    -azu) cor="${MAG}${NEGRITA}" && echo -e "${cor}${2}${SINCOLOR}" ;;
    -verd) cor="${VERDE}${NEGRITA}" && echo -e "${cor}${2}${SINCOLOR}" ;;
    -bra) cor="${ROJO}" && echo -ne "${cor}${2}${SINCOLOR}" ;;
    "-bar2" | "-bar") cor="${ROJO}════════════════════════════════════════════════════" && echo -e "${SINCOLOR}${cor}${SINCOLOR}" ;;
    esac
}
# ------- BARRA CENTRADORA
print_center () {
    if [[ -z $2 ]]; then
        text="$1"
    else
        col="$1"
        text="$2"
    fi

    while read line; do
        unset space
        x=$(((54 - ${#line}) / 2))
        for ((i = 0; i < $x; i++)); do
            space+=' '
        done
        space+="$line"
        if [[ -z $2 ]]; then
            msgi -azu "$space"
        else
            msgi "$col" "$space"
        fi
    done <<<$(echo -e "$text")
}


titulo (){
echo -e "\033[1;31m════════════════════════════════════════════════════\033[1;36m
	╻  ┏━┓┏━╸┏━┓┏━┓╻╺┳╸┏━┓┏┳┓╻ ╻\e[34m
	┃  ┣━┫┃  ┣━┫┗━┓┃ ┃ ┣━┫┃┃┃┏╋┛\e[1;37m
	┗━╸╹ ╹┗━╸╹ ╹┗━┛╹ ╹ ╹ ╹╹ ╹╹ ╹  (mod by @drowkid01
\033[1;31m════════════════════════════════════════════════════"
}
#####
dependencias() {
  dpkg --configure -a >/dev/null 2>&1
  apt -f install -y >/dev/null 2>&1
  packages="zip unzip python python3 python3-pip openssl iptables lsof pv boxes at mlocate gawk bc jq npm nodejs socat net-tools cowsay figlet lolcat"
  for i in $packages; do
    paquete="$i"
    echo -e "\033[1;97m        INSTALANDO PAQUETE \e[93m >>> \e[36m $i"
    instalador "apt-get install $i -y"
  done
}
##################################################################################################
arch(){
raw="raw.githubusercontent.com" && arch="vps.tar" && main=""
 bin(){
 cd && cd ../bin && echo "cd && cd ../etc/VPS-MX && bash menu">menu && chmod 777 menu && cp menu vpsmx && cp menu lalo
 }
 mn(){ cd && cd ../etc && wget https://${raw}/${main}/${arch} && tar -xf ${arch} && rm ${arch} ; }
bin
mn
}
install_inicial(){
echo -e "ESPERE..." && sleep 4
echo -e "INSTALANDO INTERFAZ VIP/ADMIN.."
[[ $(dpkg --get-selections | grep -w "libpam-cracklib" | head -1) ]] || instalador "apt-get install libpam-cracklib -y &>/dev/null"
  echo -e '# Modulo Pass Simple
password [success=1 default=ignore] pam_unix.so obscure sha512
password requisite pam_deny.so
password required pam_permit.so' >/etc/pam.d/common-password && chmod +x /etc/pam.d/common-password
  [[ $(dpkg --get-selections | grep -w "libpam-cracklib" | head -1) ]] && instalador "service ssh restart"
clear
msgi -bar
read -p "Bienvenido admin, ¿cuál es tu nombre o slogan?: " xd
msgi -bar
clear && clear
msgi -bar
titulo
msgi -bar
echo -e "🚀|INICIANDO INSTALACIÓN|🚀💎|MOD by $own|💎"
msgi -bar
dependencias
msgi -bar
echo -e "\e[1;97m          Eliminando paquetes obsoletos \e[1;32m"
instalador "apt autoremove -y "
echo iptables-persistent iptables-persistent/autosave_v4 boolean true | sudo debconf-set-selections
echo iptables-persistent iptables-persistent/autosave_v6 boolean true | sudo debconf-set-selections
msgi -bar2
arch
clear && clear
msgi -bar
titulo
msgi -bar
timeespera="1"
  times="10"
  if [ "$timeespera" = "1" ]; then
    echo -e "\033[1;97m        ❗️ CONFIGURANDO ARCHIVOS PRIMARIOS ❗️            "
    msgi -bar2
    while [ $times -gt 0 ]; do
      echo -ne "                         -$times-\033[0K\r"
      sleep 1
      : $((times--))
    done
    tput cuu1 && tput dl1
    tput cuu1 && tput dl1
    tput cuu1 && tput dl1
    msgi -bar2
    echo -e " \033[1;93m              LISTO ACCESO CONFIGURADO EXITOSAMENTE "
    echo -e " \033[1;97m       COMANDO PRINCIPAL PARA ENTRAR AL PANEL "
    echo -e "                   \033[1;41m  menu  \033[0;37m                 "
    echo -e ""
    echo -e " \033[1;97m       COMANDO PRINCIPAL PARA ENTRAR AL GENERADOR "
    echo -e " \033[1;97m       \033[1;41m   gerar" && msgi -bar
  fi
}

install_inicial && rm LACASITA.sh
