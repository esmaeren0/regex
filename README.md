# REGEX- GREP


# REGEX 
normal aramadan farklı olarak sabiit bir kelimeyi değil belirli kurallara uyan metinleri yaklar.


| Sembol | Açıklama                       | Örnek | Açıklama |
|--------|--------------------------------|-------|----------|
| `.`    | Herhangi bir karakter           | `a.b` | "aab", "acb" eşleşir |
| `^`    | Satır başına bakar                     | `^a`  | "abc" eşleşir ama "ba" eşleşmez a ile başlamalı |
| `$`    | Satır sonuna bakar                  | `a$`  | "ba" eşleşir ama "ab" eşleşmez  a sonda olmalı |
| `*`    | 0 veya daha fazla tekrar        | `ab*` | "a", "ab", "abb" eşleşir |
| `+`    | 1 veya daha fazla tekrar        | `ab+` | "ab", "abb" eşleşir, "a" eşleşmez b olamdığı için |
| `?`    | 0 veya 1 tekrar                 | `ab?` | "a" veya "ab" eşleşir  "abb" eşlenmez b birden fazla |
| `[]`   | Karakter sınıfı parantez içinde belirtilen herhabgi bir karakteri bulursa eşlenir               | `[abc]` | "a", "b", "c" eşleşir |
| `[^]`  | içinde belirtilen karakterler dışında eşlenir          | `[^abc]` | "d", "e" eşleşir, "a", "b", "c" eşleşmez |
| `|`    | OR (veya)                       | `a|b` | "a" veya "b" eşleşir |
| `()`   | Grup, tekrarlarla çalışmak için kullanıyoruz.                           | `(ab)+` | "ab", "abab" eşleşir |
| `\d`   | Sayı rakmam arar eşleşir                | `\d+` | "123", "4" eşleşir |
| `\D`   | Sayı olmayan karakter ile eşleşir          | `\D+` | "abc", "#" eşleşir |
| `\w`   | Kelime karakteri (harf, sayı, _) özel karakterler ile eşleşmez  | `\w+` | "abc", "abc_123" eşleşir |
| `\W`   | özel  karakter          | `\W+` | "@#!", " " eşleşir |
| `\s`   | Boşluk karakteri  ile eşleşir               | `\s+` | " ", "\t", "\n" |
| `\S`   | Boşluk olmayan karakter         | `\S+` | "abc", "123" eşleşir |


örnek kullanım senaryoları 


| Amaç                               | Regex Örneği                 | Açıklama |
|-----------------------------------|-----------------------------|----------|
| Email kontrolü                     | `^[\w\.-]+@[\w\.-]+\.\w{2,}$` | Basit email doğrulama |
| Telefon numarası                    | `^\+?\d{1,3}?[-.\s]?\(?\d{1,4}?\)?[-.\s]?\d{1,4}[-.\s]?\d{1,9}$` | Uluslararası format |
| URL kontrolü                        | `https?://[\w.-]+(?:\.[\w.-]+)+[/\w\.-]*` | HTTP ve HTTPS URL'leri |
| Parola kontrolü (en az 8 karakter) | `^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$` | Harf ve sayı içerir |
| Tarih (YYYY-MM-DD)                  | `^\d{4}-\d{2}-\d{2}$`       | 2025-08-21 gibi |

regex özel karakter grupları 


| Grup / Karakter | Anlamı                   | Örnek   | Açıklama |
|-----------------|--------------------------|---------|----------|
| `(abc)`          | Grup                      | `(ab)+` | "ab", "abab" |
| `(?:abc)`        | Non-capturing grup        | `(?:ab)+` | Grup ama capture yok |
| `(?=abc)`        | Positive lookahead        | `a(?=b)` | "a" yalnızca "b" öncesindeyse eşleşir |
| `(?!abc)`        | Negative lookahead        | `a(?!b)` | "a" yalnızca "b" öncesinde değilse eşleşir |
| `(?<=abc)`       | Positive lookbehind       | `(?<=a)b` | "b" yalnızca "a" sonrası eşleşir |
| `(?<!abc)`       | Negative lookbehind       | `(?<!a)b` | "b" yalnızca "a" sonrası değilse eşleşir |




# GREP REHBERİ

grep, belirli bir metni dosya veya çıktı içinde bulmak için kullanılan güçlü bir araçtır. Özellikle log analizi, sistem izlemesi ve otomasyonlarda sıkça kullanılır.

## Temel Syntax
grep [seçenekler] "aranan_metin" dosyaadi.txt

## Önemli Seçenekler

| Seçenek          | Açıklama |
|-----------------|----------|
| -i               | Büyük/küçük harf duyarsız arama |
| -n               | Satır numarasıyla birlikte göster |
| -v               | Eşleşmeyen satırları göster (tersi) |
| -r / -R          | Klasör ve alt klasörlerde rekürsif arama |
| -l               | Sadece eşleşen dosya adını göster |
| -c               | Eşleşen satır sayısını göster |
| -w               | Tam kelime eşleşmesi yapar |
| --color=auto     | Eşleşen kısmı renkli gösterir |
| -E               | Genişletilmiş regex desteği sağlar |
| -o               | Sadece eşleşen kısmı gösterir |
| --exclude-dir    | Belirli dizinleri taramadan hariç tutar |


### Harf duyarsız arama
``` bash
grep -i "veri" sistem.log
```
### Satır numaralarıyla birlikte göster
```
grep -n "login" /var/log/auth.log // hangi satırda hata ve ya işlem gerçekleştirildiğini bulmak için kullanılır.
```
### Ters eşleşme
```
grep -v "DEBUG" uygulama.log //"DEBUG" hariç tutulacak kelime, debug mesajını çıkararak sadece önemli logları görmeyi sağlar.
```
### Tam kelime eşleşmesi
```
grep -w "error" sistem.log // yanlış eşleşmeleri önelmek sadece belirli hataları buolmak içi kullnaılır.
```
### Klasör içindeki tüm dosyalarda arama

```
grep -r "timeout" /etc
```
*  -r → recursive, dizin ve alt dizinlerde arama yapar, "timeout" → aranacak kelime, /etc → aranacak dizin,tem yapılandırma dosyalarında belirli bir parametreyi veya ayarı aramak için kullanılır



### Belirli dizinleri hariç tutma
```
grep -r --exclude-dir="node_modules" "config" .
```
*Projelerde gereksiz büyük dizinleri aramadan logları veya konfig dosyalarını taramak için kullanırız.

### Süzgeçli arama (pipeline)
```
grep "ERROR" uygulama.log | grep -v "ignore"
```
* İlk grep → ERROR geçen satırları alır
* Pipe (|) → çıktı ikinci grepe yönlendirilir
* İkinci grep -v "ignore" → ignore içeren satırları çıkarır
* Kullanım: Hataları filtreleyip sadece önemli olanları görmek için kulaınırız

### Sadece eşleşen dosya adlarını bulma
```
grep -rl "production" ./config
```
### Başarısız SSH girişlerinin IP’lerini tespit et ve sırala
```
grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr | head
```
* grep "Failed password" → başarısız SSH girişlerini alır
* awk '{print $(NF-3)}' → satırdaki IP adresini çeker (sondan üçüncü sütun)
* sort → IP’leri sıralar
* uniq -c → tekrar eden IP’leri sayar
* sort -nr → sayıya göre azalan sıralamasını yapar
* head → en çok deneme yapanları gösterir
* Kullanım: Brute force saldırılarını veya sık başarısız denemeleri tespit etmek için kullanırız
  
### Web sunucu loglarından en çok istenen URL’leri bulma
```
grep '"GET' /var/log/apache2/access.log | awk '{print $7}' | sort | uniq -c | sort -nr | head
```
### Hata kodlarına göre sayım
```
grep '"404' /var/log/apache2/access.log | wc -l
```

