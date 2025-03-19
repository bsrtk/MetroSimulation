# Sürücüsüz Metro Simülasyonu - Rota Optimizasyonu

:black_square_button:Bu proje, sürücüsüz metro sistemleri için bir rota optimizasyonu algoritması geliştirmeyi amaçladım. Projede, metro ağını bir grafik yapısıyla modelleyerek en az aktarmalı ve en hızlı rotaları hesaplayan algoritmalar uygulamaya çalıştım.
:black_square_button:Projede Genişlik Öncelikli Arama (BFS) algoritması ile en az aktarmalı rota, A algoritması ile en hızlı rota* hesaplamaları yapmayı amaçladım.

Projede kullanılan temel teknolojiler ve kütüpühaneler şunlardır:
:radio_button:Python: Projenin temel programlama dili
:radio_button:heapq: En hızlı rota hesaplamada A algoritması* için öncelikli kuyruk (priority queue) yapısını sağlamak amacıyla kullandık.
collections:
:radio_button:defaultdict: Metro ağını tanımlarken varsayılan değerlerle sözlük yapısı kullanıldı.
:radio_button:deque: BFS algoritmasının kuyruğu için performanslı bir veri yapısı sağlamak amacıyla kullandık.
:radio_button:typing: Kodun daha anlaşılır ve okunabilir olması için tip belirteçleri (Type Hints) olarak ekledik.

##BFS Algoritması(En az aktarmalı rota) Nasıl Çalışır?
:black_square_button:BFS (Genişlik Öncelikli Arama) algoritması, graf yapılarında en kısa yolları bulmak için kullanılır.
:black_square_button:Metro ağını bir graf olarak düşünürsek, BFS algoritması bir istasyondan başlayarak bütün istasyonları katman katman gezer ve hedef istasyona ulaşan en az durak değiştirmeli rotayı bulur.
##Kullanmamızın Nedeni: 1.En az aktarmalı rota bulunurken kenar ağırlıkları (yani süreler) dikkate alınmaz.
                        2.BFS, ağırlıksız graf yapılarında en kısa yolu garantili olarak bulur.

##A Algoritması (En Hızlı Rota)* Nasıl Çalışır?
:black_square_button:A algoritması*, hedefe en hızlı ulaşan yolu bulmak için kullanılır.
:black_square_button:A* algoritması f(n) = g(n) + h(n) formülüyle çalışır:
:large_orange_diamond:g(n): Başlangıçtan mevcut noktaya kadar olan toplam süre.
:large_orange_diamond:h(n): Hedefe tahmini uzaklık (burada h(n) = 0 olarak kabul edilmiştir, çünk kesin süre hesaplanıyor).
##Kullanmamızın Nedeni: 1.:triangular_flag_on_post:Metro ağındaki kenar ağırlıkları gerçek süreleri temsil ettiği için A* algoritması uygun bir                          tercih olmuştur.
                        2.:triangular_flag_on_post:Dijkstra algoritması gibi diğer en kısa yol algoritmalarından daha verimli çalıştığı için                             tercih edilmiştir.


#Test senaryosu örneğine bakalım:
##Senaryo 1: AŞTİ'dan OSB'ye
<pre>```rota = metro.en_az_aktarma_bul("M1", "K4")
if rota:
    print("En az aktarmalı rota:", " -> ".join(i.ad for i in rota))

test_sonuc = metro.en_hizli_rota_bul("M1", "K4")
if test_sonuc:
    rota, sure = test_sonuc
    print(f"En hızlı rota ({sure} dakika):", " -> ".join(i.ad for i in rota))``` </pre>

##Beklenen Çıktı:
:triangular_flag_on_post:En az aktarmalı rota: AŞTİ -> Kızılay -> Ulus -> Demetevler -> OSB
:triangular_flag_on_post:En hızlı rota (XX dakika): AŞTİ -> Kızılay -> Demetevler -> OSB


:black_square_button:Bu projeyi geliştirmemdeki fikirlerim: Metro istasyonları arasındaki yürüyüş sürelerini ekleyerek daha gerçekçi bir rota optimizasyonu yapmak. 
:black_square_button:Kullanıcı yoğunluğuna göre alternatif rota önerileri sunmak.
D:black_square_button:inamik olarak trafik yoğunluğuna göre süreleri güncelleyen bir sistem eklemek.

