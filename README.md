Docker kurulumu, baglantisi ve ayaga kaldirma!

nginx defaulta ayaga kalkacak path, domain ve php surumunu veriyoruz ve ../etc/hosts a ayni domaini veriyoruz. 

docker-compose up -d ile ayaga kaldiriyoruz docker ps ile docker daki container lara bakip ilgili container in id sine docker exec -it "id" bash ile baglaniyoruz daha sonra cd ile iligli laravel klasorumuze giriyoruz/

laravel env de ise 
app_url="url", (http://eloquent.com)
db_host=mysql, (yml icinde verilen ad)
db_password="pass" (12345678)

Proje klonlama & olusturma 

1- projeyi klonlamak icin once ubuntu dan home/okanaras 'a docker-mysql klonla. Eger repo priv ise pub cek. Daha sonra asagidaki kodu yapistir
git clone https://github.com/okanaras/docker-mysql.git

2- Projelerini cekmek icin docker a baglan ve 
docker ps -> docker exec -it "id" bash -> git clone https://github.com/okanaras/yazilim_egitim_blog.git 

3- egerki vs code'tayken permission hatasi varsa bu kodu docker a baglanmanmadan yapistir
sudo chown -R okanaras /home/okanara/