# caso3-Servidor en la Nube
###SERVIDOR DE APACHE DONDE ESTA MI SITIO WEB                          
>http://172.174.244.25/

##COMO LO HICE
1. Primero cree un servidor fisico en la nube en azure.                                       
2. Despues lo inicie usando la  MOBAXTERM para pooder inicializar el servidor.                                               
   1.instale el mobaXterm del siguiente enlace:                         
   https://mobaxterm.mobatek.net/download-home-edition.html                                                      
   2. Abri el nobaxterm y en el puerto puse la ip del la maquina virtual generado en el azure, y inicie sesion                
   3. Se abrio un terminal donde puse una serie de comando para poder levantar, tales como:
      ```bash
      apt-get update 
      ```
      ```bash
      apt-get install ubuntu-desktop 
      ```
      ```bash
      apt-get install --reinstall ubuntu-desktop
      ```
      ```bash
      nano script1.sh
      ```
      ```bash
      chmod +x script1.sh
      ```
      ```bash
      ./script1.sh
      ```
      ```bash
      apt install xfce4 slim
      ```
      ```bash
       service slim start
      ```
   4. Volvi al inicio del nodextrem y puse **session**
   ![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/cc38a39d-34b9-421d-8c43-3fbad6bf520e)
   5. En session puse RDP
   ![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/988a574a-3fad-4df9-8b1b-04227c5741bf)
   6. Donde me pide que ponga remote host y username, y le di **ok**.
   ![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/0b289f71-6b0d-4051-99f2-57492303f47e)
   7. Se me abrio la maquina virtual y en el terminal del ubuntu clone el repostorio donde estaba mi sitio web con git page.
   ![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/a067ee30-c9a3-46c5-a6f3-3702c5c8deba)
   8. Lo movi los archivos al directorio de documentos de Apache.
      ```bash
      sudo mv repositorio_clonado /var/www/html/
      ```
   10. Instale el visual studio para ubuntu.
   11. Una vez instalado el visual studio abri la carpeta donde estaba mi respositorio clonado.
   ![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/28a41845-d1d1-4e55-8b9a-ee04305117d4)
   12. Instale el npm, git, docusaurus y el node js.
   13. En el archivo docusaurus.config.js cambie la baseUrl
       >de:  baseUrl: '/caso2/'  a  baseUrl:'/'
   15. Una vez cambiado y guardo los cambios puse el siguiente comado en el terminal
   ```bash
   sudo npm run build
   ```
   16. Despues puse este comando para abrir el archivo de configuración de Apache correspondiente al sitio llamado "caso3Ter" en el editor de texto nano
   ```bash
   sudo nano /etc/apache2/sites-available/caso3Ter.conf
   ```
   Dentro de este archivo, configuramos el directorio raíz del sitio web para apuntar al directorio 'build' del repositorio de GitHub. Por ejemplo:
   ```bash
   <VirtualHost *:80>
       ServerAdmin tu_correo_electronico@example.com
       ServerName tusitio.com
       DocumentRoot /var/www/html/ **caso2/build**
   
       <Directory /var/www/html/caso2/build>
           Options Indexes FollowSymLinks
           AllowOverride All
           Require all granted
       </Directory>
   
       ErrorLog ${APACHE_LOG_DIR}/error.log
       CustomLog ${APACHE_LOG_DIR}/access.log combined
   </VirtualHost>
   ```
   
   Despues de poner todo eso presione '**crt+x**'para guardar los cambios                       
   16. Para terminar habilite y reinicie el apache               
   
   ```bash
   sudo a2ensite tu_sitio.conf
   ```            
   ```bash         
   sudo systemctl restart apache2       
   ```      
3. Por ultimo puse la ip en calquir navegador para ver si funciono.
![image](https://github.com/KenaiJoseRod/caso3-servidorweb/assets/160261456/c84306d0-bf9c-43a5-aa90-d52c06eabe3c)
