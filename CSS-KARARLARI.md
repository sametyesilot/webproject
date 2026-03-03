# CSS Kararları

## 1. Breakpoint Seçimi
- **Neden 640px ve 1024px seçtim?** : Çoğu tablet ve masaüstü tarayıcısının standart ekran genişliğine uyum sağlamak için bu kırılım noktalarını (breakpoint) seçtim.
- **İçeriğim bu noktalarda nasıl değişiyor?** : 640px'te (tablet) öğeler yan yana gelmeye (row) başlıyor. 1024px'te (masaüstü) sayfa boydan boya uzamak yerine ortalanmış, sınırlı bir kapsayıcı (`max-width: 1200px`) içerisine giriyor ve proje grid yapısı 3 sütunlu oluyor.

## 2. Layout Tercihleri
- **Header için neden Flexbox seçtim?** : Sola yaslı logo ve sağa yaslı navigasyon menüsü gibi tek boyutlu yatay ve dikey hizalamalarda öğeleri iki uca yaymak (`space-between`) ve ortalamak (`align-items: center`) için en pratik yöntem Flexbox'tır.
- **Proje kartları için neden Grid seçtim?** : Proje ekranı satır ve sütunlara dayalı, iki boyutlu bir yapı sunuyor. Grid ile eşit yüksekliklerde, cihaza göre otomatik kırılan ve kendini boyutlayan dinamik bir kart iskeleti kurabildim.
- **auto-fit mi auto-fill mi kullandım, neden?** : `auto-fit` kullandım. Çünkü ekran genişlediğinde yan tarafta görünmeyen potansiyel (hayalet) sütunların oluşmasını istemiyorum; var olan elemanların (kartların) kalan tüm boşlukları homojen doldurması tasarım olarak daha estetik ve responsive oluyor.

## 3. Design Tokens
- **Hangi renk paletini seçtim ve neden?** : Güven verici bir koyu mavi (`#1E3A8A`) ile canlı mavi (`#2563EB`) temelinde sade, modern ve kontrast oranı yüksek profesyonel bir web paleti tanımladım.
- **Spacing skalasını nasıl belirledim?** : Modern `8pt / 4px / 0.25rem` katları prensibini temel alarak hiyerarşik bir mesafe (`--space-xs, -sm, -md, -lg...`) skalası belirledim, böylece projede oran konusunda tutarlılığı yakaladım.
- **Fluid typography için clamp değerlerini nasıl ayarladım?** : Mobil cihazlarda yazının çok büyük olup ekranı boğmaması ve ekran büyüdükçe çok küçük kalmaması için `vw` parametresi (viewport width) devreye girecek şekilde `rem+vw` kombinasyonları (`clamp(minimum, tercih, maksimum)`) kullandım.

## 4. Responsive Stratejiler
- **Mobile-first yaklaşımını nasıl uyguladım?** : Önce hiçbir media sorgusu kullanmadan, tüm elemanları %100 genişlikte ve alt alta akacak (dikey) boyutta mobiller için tasarladım. Daha büyük ekranlar için ise `min-width` metodu ile sadece yeni özellikler (genişlik kuralları) ekleyerek ilerledim.
- **Hangi elemanlar breakpoint'lerde değişiyor?** : Başlıca Header ve menü (dikeyken yatay oldu), Hakkımda içeriği (alt alta dururken, yan yana geldi) ve Projelerim gridi (`1` kolonda iken auto-fit veya `3` kolon formlarına oturdu) değişiklik gösterdi.
- **Görsel boyutlarını nasıl yönettim?** : Varsayılan CSS ayarlarında `max-width: 100%` ve `height: auto` vererek taşmaların önüne geçtim. Kart içerisindeki görsellerde de esneme olmasın diye belirli bir `height` verip `object-fit: cover` kullandım.
