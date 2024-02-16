# A. WSL Kurulumu & Kaldirma </br> 

## 1- terminalde <b>"wsl --install"</b> koumutunu calistir. </br></br>

## 2- Sırasıyla aşağıdaki komutları girerek Ubuntu güncellemelerimizi ve gerekli paketlerimizi kuralım. </br>
sudo apt update </br>
sudo apt upgrade -y </br>
sudo apt -y install curl dirmngr apt-transport-https lsb-release ca-certificates </br>
sudo apt install git </br></br>

## 3- Şimdi sistemimize NodeJS kuralım. </br>
sudo apt-get update </br>
sudo apt-get install -y ca-certificates curl gnupg </br>
sudo mkdir -p /etc/apt/keyrings </br>
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | sudo gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg </br></br>

## 4- Ardından repoyu oluşturalım </br>
NODE_MAJOR=20 </br>
echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | sudo tee /etc/apt/sources.list.d/nodesource.list </br></br>

## 5- Şimdi NodeJS'yi kurabiliriz. </br>
sudo apt-get update </br>
sudo apt-get install nodejs -y </br></br></br></br>

## WSL Kaldirma </br></br>

## 1- Uygulamalardan ubuntuyu kaldir. </br></br>

## 2- terminalde <b>"wsl --list"</b> koumutunu calistir. </br></br>

## 3- terminalde <b>"wsl --unregister Ubuntu"</b> koumutunu calistir. </br></br>

# B. Github Kurulumu </br>
## 1- Asagidaki kodlar git kurulum kodlaridir hepsi ubuntu terminalinde calisacak! </br>
sudo apt install git || git --version </br>
git config --global user.name "Okan Aras" </br>
git config --global user.email "oknaras@icloud.com" </br>
git config --global init.defaultBranch main </br>
cat ~/.gitconfig </br></br>

## 2- SSH kurulumu </br>
ssh-keygen -t rsa -b 4096 -C "okanaras" </br>
cikan ekranda public key yazan bolumdeki /root/.ssh/id_rsa.pub yazan yerde asagidaki komutu yaziyoruz </br>
code ~//.ssh/id_rsa.pub </br>
komutu ile vscode ta key i aciyoruz ve key i kopyalayip github web te settings-ssh and gpg keys yerine girip yeni ssh ekliyoruz </br>
title'a "Ubuntu-WSL" verdim "key tipi auth" ve "key e yukarda kopyaladigimi" verip ekledim </br></br>

ssh -T git@github.com </br> 
<b>'yes'</b> diyoruz </br>
en sonda "git clone 'sshlinki'" ile projeyi cekiyoruz </br></br></br></br>

# C. Docker Desktop </br>
## Uygulama ayarlari
Docker Desktop(Windows) indirelim ve kuralım. </br>
Kurulum sonrasında Docker Desktop uygulamamızı açalım ve sağ üstteki ikona tıklayarak ayarlar menüsüne gidelim. </br>
General bbölümünde 'Use WSL 2 ve Use Docker Compose V2' seçili olsun. </br>
Ardından Resources - WSL Integration kısmında Ubuntu seçeneğini aktif edelim.</br>
nginx defaulta ayaga kalkacak path, domain ve php surumunu veriyoruz ve ../etc/hosts a ayni domaini veriyoruz. </br>
docker-compose up -d ile ayaga kaldiriyoruz docker ps ile docker daki container lara bakip ilgili container in id sine docker exec -it "id" bash ile baglaniyoruz daha sonra cd ile iligli laravel klasorumuze giriyoruz</br></br>

## laravel env de ise 
app_url="url", (http://eloquent.com) </br>
db_host=mysql, (yml icinde verilen ad) </br>
db_password="pass" (12345678) </br></br></br></br>

# D. Proje Klonlama & Hata Giderme  </br>
## 1- projeyi klonlamak icin once ubuntu dan home/okanaras 'a docker-mysql klonla. Eger repo priv ise pub cek. Daha sonra asagidaki kodu yapistir</br>
git clone https://github.com/okanaras/docker-mysql.git</br></br>

## 2- Projelerini cekmek icin docker a baglan ve terminale </br> 
docker ps -> docker exec -it "id" bash -> git clone https://github.com/okanaras/yazilim_egitim_blog.git </br></br>

## 3- egerki vs code'tayken permission hatasi varsa bu kodu ubuntu terminale yapistir</br>
sudo chown -R okanaras /home/okanaras</br></br>

## 4- composer install (dockera baglan) ve npm install (dockera baglanmadan) terminalde calistir eger ki "bash: npm: command not found" hatasi cikarsa asagidaki kodu calistirdiktan sonra tekrar dene </br>

composer install & update --ignore-platform-req=ext-exif</br>
apt-get install -y npm </br></br>

## 5- 'The stream or file "/var/www/html/yazilim_egitim_blog/storage/logs/laravel.log" could not be opened in append mode: Failed to open stream: Permission denied The exception occurred while attempting to log: The stream or file "/var/www/html/yazilim_egitim_blog/storage/logs/laravel.log" could not be opened in append' icin asagidaki kodu yapistir exec it baglanmaddan proje yoluna yapistir</br>
sudo chmod -R 777 storage/</br></br>

## 6- The /var/www/html/yazilim_egitim_blog/bootstrap/cache directory must be present and writable.
sudo chmod -R 777 bootstrap/cache/ </br></br>

## 7- Laravel not found icin docker a baglandiktan sonra :
export PATH="/root/.composer/vendor/bin:$PATH" 

