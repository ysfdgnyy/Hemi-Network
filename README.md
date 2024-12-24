
# Hemi Network CLI Madencisi Kurulumu

Donanım gereksinimi yoktur, sadece sunucunuza kurulum yapabilirsiniz (çoklu sunucu desteği yakında).

(Opsiyonel) Node kurmak istemeyenler şu işlemi gerçekleştirebilir: e2733fa6

(Opsiyonel) Ana bilgisayarınızda kurulum yapmak için buradan da yardımcı olabilirsiniz.

## Kurulum Adımları  

1. İlk olarak, ihtiyacımız olan binary dosyasını indirelim.  
   ```bash
   wget https://github.com/hemilabs/heminetwork/releases/download/v0.4.3/heminetwork_v0.4.3_linux_amd64.tar.gz
   ```

2. İndirdiğimiz sıkıştırılmış dosyayı açalım ve dosya klasörüne girelim.  
   ```bash
   tar xvf heminetwork_v0.4.3_linux_amd64.tar.gz && cd heminetwork_v0.4.3_linux_amd64
   ```

3. Madenci için yeni bir cüzdan oluşturalım.  
   ```bash
   ./keygen -secp256k1 -json -net="testnet" > ~/popm-address.json
   ```

4. Oluşturduğumuz cüzdan bilgilerini kontrol edelim. İsterseniz kendi bilgisayarınıza kaydedebilirsiniz.  
   ```bash
   cat $HOME/popm-address.json
   ```  
   Yukarıdaki çıktıda ethereum_address, network, private_key, public_key ve pubkey_hash bilgilerini alacaksınız.

İlk olarak, pubkey_hash değeri ile Hemi Network discord sunucusundaki faucet kanalına gidin ve `/tbtc-faucet` komutunu kullanarak pubkey_hash’i address kısmına ekleyip faucet talebinde bulunun.

Kurulum tamamlandığında aşağıdaki adımlara geçelim:

5. Şimdi, ubuntu sunucumuza geri dönelim. Export işlemleriyle ayarları yapalım. Ben export değerlerini kalıcı hale getireceğim. İlk olarak bir screen başlatalım:
   ```bash
   screen -S hemi
   ```

6. Şimdi cüzdan bilgilerimizden private_key kısmını kullanacağız. Aşağıdaki satırda uygun şekilde değiştirin ve uygulayın.
   ```bash
   echo 'export POPM_BTC_PRIVKEY=PRIVATE KEY BURAYA YAZILACAK' >> ~/.bashrc  
   echo 'export POPM_STATIC_FEE=50' >> ~/.bashrc  
   echo 'export POPM_BFG_URL=wss://testnet.rpc.hemi.network/v1/ws/public' >> ~/.bashrc  
   source ~/.bashrc
   ```

7. Sonrasında aşağıdaki komutla madenciyi başlatabilirsiniz.  
   ```bash
   ./popmd
   ```

Her şey bu kadar.
