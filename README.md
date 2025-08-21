# regex

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
