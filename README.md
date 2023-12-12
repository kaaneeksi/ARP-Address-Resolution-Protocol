# ARP (Address Resolution Protocol)

**ARP** Türkçe ismi ile _"Adres Çözümleme Protokolü"_ kısaca bilgi vermek gerekirse, her **IP (Internet Protocol Address)** adresine karşılık gelen bir **MAC (Media Access Control)** adresi arasındaki ilişkiyi sürdürmek için kullanılır.

Yerel bir ağda veri alış-verişi yapılacak cihazın MAC adresini bilmeliyiz. Bu sebeple eğer ki cihazın IP'sini biliyorsak fakat MAC adresini bilmiyorsak, **ARP** yani Adres Çözümleme Protokolü'nü kullanılırz


## ARP Nasıl Çalışır ?

Evinizin içinde 2 cihaz olduğunu düşünün ve sizin cihazınızın diğer cihaz ile iletişime geçmesi için MAC adresini bilmesi gerektiğini söyledik ve bunu öğrenmek için de ARP protokolünü kullancak bunu için;

 - IP si bilinen fakat fiziksel adresi bilinmeyen bir cihaz varsa bütün ağa arp isteği (arp request) gönderilir. Bu pakette gönderenin IP adresi, gönderenin MAC adresi ve alıcının IP adresi vardır. Alıcının MAC adresi bilinmediğinden tüm ağa yayın yapan (broadcast) bir paket yollanır ve isteğin bütün ağa ulaşması sağlanır.

Gönderilen ARP request paketinin formatı:
```
Address Resolution Protocol (request)

  Hardware type: Ethernet (1)
  Protocol type: IPv4 (0x0800)
  Hardware size: 6 
  Protocol size: 4
  Opcode: request (1)
  Sender MAC address: 05:53:ff:ff:aa:aa
  Sender IP adreess: 10.0.0.11
  Target MAC address: ff:ff:ff:ff:ff:ff
  Target IP adreess: 10.0.0.22
```
-  Belirtilen IP nin dışındaki hiçbir IP den cevap gelmez ve gelen cevap cihazın kendi MAC adresini içerir.

-  Ayrıca isteği yollayan ve isteği yanıtlayan 2 cihazda diğerinin MAC adresini ve IP adresini daha sonra kullanmak üzere belleğine (ARP Tablosu) kaydeder.


## ARP TAblosu

Arp işlemini tekrar tekrar yapmamak, öğrenilen fiziksel adres-IP adresi bilgilerini ileride kullanabilmek için bu bilgiler arp tablosunda tutulur. 



Her arp girdisi en fazla 10 dakikalık bir ömre sahiptir. Tabloya eklendikten sonra 2 dakika içinde tekrar kullanılmayan girdiler silinir. Eğer 2 dakika içinde tekrar kullanılırsa tabloda 2 dakika daha kalır ama en fazla 10 dakika sonra silinir.


