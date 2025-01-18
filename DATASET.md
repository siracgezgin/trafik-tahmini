# Veri Seti Dokümantasyonu

Bu dosya, projede kullanılan trafik yoğunluğu veri setinin özelliklerini açıklamaktadır.

## Veri Seti Kaynağı

Veri seti, İstanbul Büyükşehir Belediyesi'nin [Açık Veri Portalı](https://data.ibb.gov.tr) üzerinden alınmıştır. Veri seti İstanbul'un farklı bölgelerindeki trafik yoğunluğunu ve ilgili verileri içermektedir.

## Veri Seti Özellikleri

Veri seti aşağıdaki özelliklere sahiptir:

1. **Zaman Damgası**: Trafik yoğunluğunun ölçüldüğü zaman dilimi (tarih ve saat).
2. **Bölge Kodları**: Trafiğin ölçüldüğü İstanbul'un farklı bölgelerine ait kodlar.
3. **Trafik Yoğunluk Değerleri**: Yola bağlı olarak ölçülen trafik yoğunluğu (0 ile 1 arasında bir değer).
4. **Hava Durumu Bilgileri**: O anki hava durumu verisi (örneğin, yağışlı, güneşli, vb.).
5. **Özel Gün/Etkileşim Bilgileri**: Özel günler veya etkinliklerin trafik yoğunluğu üzerinde etkisi (örneğin, bayram günleri).

## Veri Seti Yapısı

Veri seti, aşağıdaki gibi sütunlardan oluşmaktadır:

| Sütun Adı              | Açıklama                                      |
|------------------------|-----------------------------------------------|
| `timestamp`            | Zaman damgası (tarih ve saat)                 |
| `region_code`          | Bölge kodu (İstanbul ilçeleri)               |
| `traffic_density`      | Trafik yoğunluğu (0-1 arası bir değer)        |
| `weather_conditions`   | Hava durumu (örneğin: Sunny, Rainy, Foggy)    |
| `special_event`        | Özel gün veya etkinlik bilgisi (1: Evet, 0: Hayır) |

## Veri Seti Kullanımı

Bu veri seti, İstanbul'un trafik yoğunluğu hakkında öngörülerde bulunmak ve makine öğrenmesi modelleri ile tahminler yapmak için kullanılmaktadır.

## Veri Seti İzinleri

Bu veri seti, [İBB Açık Veri Portalı](https://data.ibb.gov.tr) üzerinden kamuya açık olarak sunulmaktadır ve kullanılabilir.
