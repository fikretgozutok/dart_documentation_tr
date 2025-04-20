# Dart Türkçe Rehber

## İçindekiler

- [Giriş ve Temel Bilgiler](#1-giriş-ve-temel-bilgiler)
- [Değişkenler ve Veri Tipleri](#2-değişkenler-ve-veri-tipleri)
- [Operatörler](#3-operatörler)
- [Kontrol Yapıları ve Döngüler](#4-kontrol-yapıları-ve-döngüler)
- [Fonksiyonlar](#5-fonksiyonlar)
- [Koleksiyonlar](#6-koleksiyonlar)
- [Sınıflar ve Nesne Tabanlı Programlama](#7-sınıflar-ve-nesne-tabanlı-programlama)
- [Kalıtım ve Polimorfizm](#8-kalıtım-ve-polimorfizm)
- [Hata Yönetimi](#9-hata-yönetimi)
- [Null Safety](#10-null-safety)
- [Asenkron Programlama](#11-asenkron-programlama)
- [Modüler Kodlama ve Paketler](#12-modüler-kodlama-ve-paketler)
- [Test Yazımı](#13-test-yazımı)
- [İleri Seviye Konular](#14-i̇leri-seviye-konular)
- [Dart ile Flutter Arasında Köprü](#15-dart-ile-flutter-arasında-köprü)

## 1. Giriş ve Temel Bilgiler

### 1.1 Dart Nedir?

Dart, Google tarafından geliştirilen açık kaynaklı, genel amaçlı bir programlama dilidir. Özellikle kullanıcı ara yüzleri geliştirmek için tasarlanmıştır. Dart dilinin en yaygın kullanıldığı alan, yine Google tarafından geliştirilen Flutter framework'üdür. Flutter ile mobil, web ve masaüstü uygulamaları geliştirilebilir ve Dart bu altyapının temel programlama dilidir.

Dart şu ihtiyaçlara yönelik geliştirilmiştir:

- Hızlı çalışması
- Kolay öğrenilmesi
- Modern dillerle benzer sözdizimine sahip olması (Java, C#, JavaScript'e benzer)
- Web, mobil ve masaüstü platformlarını desteklemesi
- Geliştirici deneyimini iyileştirecek araçlara sahip olması

### 1.2 Dart Nerelerde Kullanılır?

- Flutter ile mobil (Android/iOS), web ve masaüstü uygulamaları
- Komut satırı (CLI) uygulamaları
- Sunucu tarafı uygulamalar (örneğin REST API servisleri)
- Web uygulamaları (Dart, JavaScript'e derlenebilir)

### 1.3 Dart ile İlk Program

Dart'ta bir program genellikle `main()` fonksiyonu ile başlar. Bu fonksiyon programın başlangıç noktasıdır.

Basit bir "Hello, World!" örneği şu şekildedir:

```dart
void main() {
  print('Hello, World!');
}
```

#### Açıklamalar:
- `void` anahtar kelimesi, `main` fonksiyonunun geriye değer döndürmediğini belirtir.
- `main()` parametre almadan da çalışabilir, ama istenirse `List<String> args` şeklinde argümanlar alınabilir.
- `print()` fonksiyonu, ekrana veri yazdırmak için kullanılır.

### 1.4 Dart Çalıştırma Yöntemleri

Dart kodları birkaç farklı yolla çalıştırılabilir:

#### 1. DartPad (tarayıcı üzerinden)
Google tarafından sağlanan online bir editördür. Adresi: https://dartpad.dev  
Yazılan Dart kodları doğrudan tarayıcıda çalıştırılabilir.

#### 2. Lokal Geliştirme Ortamı
Aşağıdaki adımlarla sistemine Dart kurabilirsin:

1. [https://dart.dev/get-dart](https://dart.dev/get-dart) adresinden sistemine uygun kurulumu yap.
2. Terminal veya komut satırında şu komutla Dart versiyonunu kontrol edebilirsin:
   ```
   dart --version
   ```

#### 3. Dart dosyası oluşturup çalıştırmak
Örnek olarak bir `hello.dart` dosyası oluştur ve içine şu kodu yaz:

```dart
void main() {
  print("Merhaba Dart!");
}
```

Sonra terminalden bu komutla çalıştır:

```
dart hello.dart
```

Bu komut, Dart yorumlayıcısı aracılığıyla dosyayı çalıştırır ve sonucu ekrana yazdırır.

## 2. Değişkenler ve Veri Tipleri

Dart dilinde bir programın temel yapı taşlarından biri değişkenlerdir. Değişkenler, veriyi bellekte tutmak için kullanılır. Dart, statik tür denetimi olan bir dildir, yani her değişkenin bir veri tipi vardır. Bu tipler açıkça belirtilmiş olabilir veya Dart derleyicisi tarafından otomatik olarak çıkarılabilir (type inference).

### 2.1 Değişken Tanımlama

Değişken tanımlamak için çeşitli yollar vardır:

#### 1. Tür Belirterek Tanımlama

```dart
int yas = 25;
double pi = 3.14;
String isim = "Ahmet";
bool aktifMi = true;
```

Burada değişkenlerin türü açıkça belirtilmiştir.

#### 2. `var` Anahtar Kelimesi ile Tanımlama

```dart
var sehir = "Ankara";
var sayi = 100;
```

`var` ile tanımlanan değişkenin türü, atanan değere göre otomatik olarak belirlenir. Sonradan bu değişkene farklı türden bir değer atanamaz.

#### 3. `dynamic` Anahtar Kelimesi ile Tanımlama

```dart
dynamic veri = "metin";
veri = 123;     // Geçerli
veri = true;    // Geçerli
```

`dynamic` tipi, çalışma zamanında tür kontrolü yapmaz. Bir değişkene istenen türden veri atanabilir. Ancak bu durum tür güvenliğini ortadan kaldırır, hatalara neden olabilir.

### 2.2 `final` ve `const` Anahtar Kelimeleri

Dart dilinde değişkenlerin sabit olup olmayacağını belirlemek için `final` ve `const` anahtar kelimeleri kullanılır.

#### `final`

```dart
final zamanDamgasi = DateTime.now();
```

`final` ile tanımlanan bir değişkenin değeri **ilk atamadan sonra değiştirilemez**. Ancak değeri çalışma zamanında hesaplanabilir.

#### `const`

```dart
const pi = 3.14159;
```

`const` ile tanımlanan değişkenin değeri **derleme zamanında sabit** olmalıdır. Yani sabit değerler alır ve program çalışırken hesaplanamaz.

Farkı daha net görmek için:

```dart
final tarih = DateTime.now();  // Geçerli
const tarih2 = DateTime.now(); // Hata verir
```

### 2.3 Temel Veri Tipleri

#### Sayılar

- `int`: Tam sayılar (örn: 1, -5, 100)
- `double`: Ondalıklı sayılar (örn: 3.14, -0.5)

```dart
int sayi = 10;
double oran = 2.5;
```

#### Metinler (String)

```dart
String ad = 'Ali';
String soyad = "Yılmaz";
String tamAd = '$ad $soyad';  // Değişken interpolasyonu
```

- `'$degisken'` ile string içinde değişken değeri kullanılabilir.
- `'${ifade}'` ile karmaşık ifadeler yazılabilir.

#### Boolean (Mantıksal)

```dart
bool durum = true;
bool aktifMi = false;
```

Mantıksal ifadelerde `true` ve `false` kullanılır.

### 2.4 Null Safety

Dart dili, null değerlerin neden olduğu hataları azaltmak amacıyla null safety özelliği sunar. Bu özellik sayesinde bir değişkenin null olup olmayacağı belirlenebilir.

```dart
String isim = "Ali";        // null olamaz
String? soyad = null;       // null olabilir
```

- `?` operatörü, bir değişkenin null olabileceğini belirtir.
- Bu özellik Dart 2.12 ve sonrasında varsayılan olarak etkin durumdadır.

### 2.5 Tür Dönüştürme

```dart
int a = 10;
String b = a.toString();        // int → String

String s = "25";
int c = int.parse(s);           // String → int

double d = double.parse("3.14"); // String → double
```

Eğer dönüştürülecek değer yanlış biçimliyse `FormatException` hatası alınabilir. Bu yüzden `try-catch` ile birlikte kullanmak önerilir.


## 3. Operatörler

Dart dilinde operatörler, değişkenler ve değerler üzerinde işlem yapmamızı sağlar. Bu operatörler; aritmetik, karşılaştırma, mantıksal ve özel operatörler olarak gruplandırılabilir.

### 3.1 Aritmetik Operatörler

Matematiksel işlemleri gerçekleştirmek için kullanılır.

| Operatör | Açıklama                | Örnek          |
|----------|-------------------------|----------------|
| `+`      | Toplama                 | `a + b`        |
| `-`      | Çıkarma                 | `a - b`        |
| `*`      | Çarpma                  | `a * b`        |
| `/`      | Bölme (double döner)    | `a / b`        |
| `~/`     | Tamsayı bölme           | `a ~/ b`       |
| `%`      | Mod (kalan)             | `a % b`        |

```dart
void main() {
  int a = 10;
  int b = 3;
  print(a + b);     // 13
  print(a ~/ b);    // 3
  print(a % b);     // 1
}
```

### 3.2 Atama Operatörleri

Bir değişkene değer atamak veya mevcut değeri değiştirmek için kullanılır.

| Operatör | Açıklama                  | Örnek         |
|----------|---------------------------|---------------|
| `=`      | Atama                     | `x = 5`       |
| `+=`     | Toplayıp ata              | `x += 2`      |
| `-=`     | Çıkarıp ata               | `x -= 1`      |
| `*=`     | Çarpıp ata                | `x *= 3`      |
| `/=`     | Bölüp ata (double döner)  | `x /= 2`      |
| `~/=`    | Tamsayı bölüp ata         | `x ~/= 2`     |

### 3.3 Karşılaştırma Operatörleri

İki değeri karşılaştırır ve sonuç olarak `true` veya `false` döner.

| Operatör | Açıklama           | Örnek          |
|----------|--------------------|----------------|
| `==`     | Eşittir            | `a == b`       |
| `!=`     | Eşit değil         | `a != b`       |
| `>`      | Büyüktür           | `a > b`        |
| `<`      | Küçüktür           | `a < b`        |
| `>=`     | Büyük eşittir      | `a >= b`       |
| `<=`     | Küçük eşittir      | `a <= b`       |

### 3.4 Mantıksal Operatörler

Koşullu ifadeleri birleştirmek için kullanılır.

| Operatör | Açıklama       | Örnek            |
|----------|----------------|------------------|
| `&&`     | Ve             | `a > 5 && b < 10`|
| `\|\|`   | Veya         | `a > 5 \|\| b < 10`|
| `!`      | Değil (not)    | `!(a == b)`      |

### 3.5 Artırma / Azaltma Operatörleri

| Operatör | Açıklama           | Örnek         |
|----------|--------------------|---------------|
| `++x`    | Önce artır, sonra kullan | `++a` |
| `x++`    | Önce kullan, sonra artır | `a++` |
| `--x`    | Önce azalt, sonra kullan| `--a` |
| `x--`    | Önce kullan, sonra azalt| `a--` |

```dart
void main() {
  int a = 5;
  print(++a); // 6
  print(a++); // 6 (sonra 7 olur)
  print(a);   // 7
}
```

### 3.6 Null Aware (Null Kontrolü) Operatörleri

Dart'ta null güvenliğiyle ilgili özel operatörler de vardır:

| Operatör | Açıklama                                  | Örnek                   |
|----------|--------------------------------------------|-------------------------|
| `??`     | Null ise sağdaki değeri kullan             | `x = y ?? 10`           |
| `??=`    | Null ise atama yap                         | `x ??= 5`               |
| `?.`     | Null ise çağırmaz                          | `kullanici?.ad`         |

### 3.7 Tip Dönüştürme ve Kontrol Operatörleri

| Operatör | Açıklama                            | Örnek             |
|----------|-------------------------------------|-------------------|
| `is`     | Tip kontrolü (true/false döner)     | `x is String`     |
| `is!`    | Belirtilen tipte değil mi?          | `x is! int`       |
| `as`     | Tip dönüştürme                      | `x as String`     |

## 4. Kontrol Yapıları ve Döngüler

Dart dilinde kontrol yapıları, programın akışını belirli koşullara göre yönlendirmek için kullanılır. Koşullar ve döngüler, temel kontrol yapılarıdır.

### 4.1 `if` - `else` Yapısı

Koşullu dallanmalar için kullanılır.

```dart
void main() {
  int not = 85;

  if (not >= 90) {
    print("Pekiyi");
  } else if (not >= 70) {
    print("İyi");
  } else {
    print("Geçer");
  }
}
```

- `if` bloğu yalnızca koşul doğruysa çalışır.
- `else if` ile başka bir koşul tanımlanabilir.
- `else` bloğu ise diğer tüm durumlar için çalışır.

Koşulda boolean ifade beklenir.

### 4.2 Ternary (Üçlü) Operatör

`if-else` yapısının kısa halidir.

```dart
var sonuc = (not >= 50) ? "Geçti" : "Kaldı";
```

Yukarıdaki ifade, `not` 50'den büyükse `"Geçti"`, değilse `"Kaldı"` değerini verir.

### 4.3 `switch` - `case` Yapısı

Bir değişkenin farklı sabit değerlere göre kontrol edilmesini sağlar. Genellikle sayılar ve sabit `String` ifadeler için kullanılır.

```dart
void main() {
  String gun = "Pazartesi";

  switch (gun) {
    case "Pazartesi":
      print("Haftanın ilk günü");
      break;
    case "Cuma":
      print("Haftanın son iş günü");
      break;
    default:
      print("Hafta içi");
  }
}
```

- Her `case` ifadesinden sonra `break` kullanılır. Aksi takdirde diğer bloklara da girer.
- `default` bloğu, eşleşen hiçbir durum yoksa çalışır.

Dart 3.0 ile birlikte pattern matching desteklenmeye başlamıştır; ancak temel kullanım yukarıdaki gibidir.

### 4.4.1 `for` Döngüsü

Belirli sayıda tekrar için kullanılır.

```dart
for (int i = 0; i < 5; i++) {
  print(i);
}
```

- `i = 0`: Başlangıç değeri
- `i < 5`: Koşul
- `i++`: Her döngüde ne yapılacağı

### 4.4.2 `while` Döngüsü

Koşul doğru olduğu sürece çalışır.

```dart
int i = 0;
while (i < 3) {
  print(i);
  i++;
}
```

### 4.4.3 `do-while` Döngüsü

Önce kod çalışır, sonra koşul kontrol edilir. En az bir kez çalışır.

```dart
int i = 0;
do {
  print(i);
  i++;
} while (i < 3);
```

### 4.4.4 `for-in` Döngüsü

Bir koleksiyonun elemanları üzerinde gezinmek için kullanılır.

```dart
var liste = [1, 2, 3];
for (var eleman in liste) {
  print(eleman);
}
```

### 4.4.5 `break` ve `continue`

- `break`: Döngüyü tamamen sonlandırır.
- `continue`: O anki adımı atlar, bir sonraki adıma geçer.

```dart
for (int i = 0; i < 5; i++) {
  if (i == 3) break;
  print(i);  // 0, 1, 2 yazdırır
}
```

```dart
for (int i = 0; i < 5; i++) {
  if (i == 3) continue;
  print(i);  // 0, 1, 2, 4 yazdırır
}
```

## 5. Fonksiyonlar

Fonksiyonlar, belirli bir görevi yerine getiren, tekrar kullanılabilir kod bloklarıdır. Dart dilinde fonksiyonlar, belirli bir işlemi gerçekleştirmek için kullanılır ve genellikle bir giriş alır, bir çıkış döndürür.

### 5.1 Fonksiyon Tanımlama

Dart dilinde fonksiyonlar `void` veya belirli bir türde değer döndüren fonksiyonlar olabilir. Fonksiyonlar, genellikle bir işlevi yerine getiren bir blok olarak tanımlanır.

#### Temel Fonksiyon Tanımlaması

```dart
void selamla() {
  print("Merhaba, Dart!");
}

void main() {
  selamla(); // Fonksiyonu çağırıyoruz
}
```

- `void`: Fonksiyonun bir değer döndürmediğini belirtir.
- `selamla`: Fonksiyon adı.
- `main()`: Dart programlarında başlangıç noktası olan fonksiyon.

### 5.2 Parametreli Fonksiyonlar

Fonksiyonlara parametreler de geçilebilir. Parametreler, fonksiyonun işlevini yerine getirirken kullandığı dışsal verilerdir.

```dart
void merhaba(String isim) {
  print("Merhaba, $isim!");
}

void main() {
  merhaba("Ali"); // Ali'ye selam verir
}
```

Bu örnekte, `merhaba` fonksiyonu bir `String` parametresi alır ve bu parametreyi kullanarak bir mesaj yazdırır.

### 5.3 Değer Döndüren Fonksiyonlar

Bir fonksiyon, `return` anahtar kelimesiyle bir değer döndürebilir. Bu değer, fonksiyonun işlevi tamamlandığında dışarıya iletilir.

```dart
int topla(int a, int b) {
  return a + b;
}

void main() {
  int sonuc = topla(5, 7);
  print(sonuc); // 12
}
```

- `int`: Fonksiyonun döndüreceği türü belirtir.
- `return`: Fonksiyondan dönen değeri belirtir.

### 5.4 Fonksiyonun Parametre Türleri

Dart dilinde, fonksiyonlara parametre olarak farklı türde değerler geçirebilirsiniz. Bu parametreler belirli türlerde olabilir.

#### Parametre Türü Belirtme

```dart
double carpma(double a, double b) {
  return a * b;
}

void main() {
  double sonuc = carpma(4.5, 2.0);
  print(sonuc); // 9.0
}
```

Bu fonksiyonda, `double` türünde iki parametre alınır ve sonucu yine `double` olarak döndürür.

### 5.5 Varsayılan Parametreler

Fonksiyonlarda parametrelerin varsayılan değerleri de olabilir. Eğer bir parametre fonksiyona geçilmezse, o zaman varsayılan değer kullanılır.

```dart
void selamla(String isim, [String soyisim = "Bilinmiyor"]) {
  print("Merhaba, $isim $soyisim!");
}

void main() {
  selamla("Ali"); // Soyisim varsayılan olarak "Bilinmiyor"
  selamla("Ayşe", "Kara"); // Soyisim "Kara" olarak belirtilmiş
}
```

- `[]`: Parametrelerin opsiyonel olduğunu belirtir.
- Varsayılan değer, parametre sağlanmazsa kullanılır.

### 5.6 İsimli Parametreler

Dart dilinde, fonksiyonlara isimli parametreler de eklenebilir. Bu, fonksiyonları daha okunabilir ve esnek hale getirir.

```dart
void merhaba({required String isim, required int yas}) {
  print("Merhaba, $isim! Yaşınız: $yas");
}

void main() {
  merhaba(isim: "Ali", yas: 25); // Parametreler isimli olarak belirtilir
}
```

- `{}`: Parametrelerin isimli olduğunu belirtir.
- `required`: Parametrenin zorunlu olduğunu belirtir.

### 5.7 Fonksiyonların Fonksiyon Olarak Kullanılması (First-Class Functions)

Dart, fonksiyonları birinci sınıf vatandaş olarak kabul eder. Bu, fonksiyonların değişkenlere atanabileceği, diğer fonksiyonlara parametre olarak geçilebileceği ve fonksiyonlardan döndürülebileceği anlamına gelir.

#### Fonksiyonları Değişken Olarak Kullanmak

```dart
void selamla() {
  print("Merhaba!");
}

void main() {
  var fonksiyon = selamla;
  fonksiyon(); // Merhaba! yazdırılır
}
```

### 5.8 Anonim (Lambda) Fonksiyonlar

Fonksiyonlar, anonim olarak (isim verilmeden) da tanımlanabilir. Bu tür fonksiyonlar genellikle kısa işlemler için kullanılır.

```dart
var topla = (int a, int b) => a + b;

void main() {
  print(topla(3, 5)); // 8
}
```

`=>`: Tek satırlık fonksiyonlar için kullanılan kısa yazım şeklidir.

## 6. Koleksiyonlar

### 6.1 `List` (Liste)

Dart'taki `List`, sıralı bir koleksiyon yapısıdır ve içinde birden fazla öğe saklayabilir. Listeler, öğelerin sırasına göre erişim sağlar ve öğeler üzerinde değişiklik yapmanıza imkan tanır.

#### List Tanımlama

```dart
void main() {
  // Boş bir liste tanımlamak
  List<int> sayilar = [];

  // Öğelerle bir liste oluşturmak
  List<int> sayilar2 = [1, 2, 3, 4, 5];

  // Farklı türde öğe içeren liste
  List<dynamic> karisik = [1, 'Dart', true];
}
```

- `List<int>`: Tam sayı türünde bir liste.
- `List<dynamic>`: Farklı türde öğe içeren bir liste.

#### Listeye Ekleme ve Çıkarma

```dart
void main() {
  List<int> sayilar = [1, 2, 3];
  
  // Listeye öğe eklemek
  sayilar.add(4);
  
  // Listeye birden fazla öğe eklemek
  sayilar.addAll([5, 6]);
  
  // Bir öğeyi çıkarmak
  sayilar.remove(3);
  
  // Belirli bir index'teki öğeyi çıkarmak
  sayilar.removeAt(0);  // İlk öğeyi çıkarır
}
```

#### Listeye Erişim

```dart
void main() {
  List<int> sayilar = [1, 2, 3, 4, 5];
  
  // Belirli bir öğeye erişim
  print(sayilar[2]);  // 3
  
  // Listenin uzunluğuna erişim
  print(sayilar.length);  // 5
}
```

### 6.2 `Set` (Küme)

`Set`, tekrarsız öğeler içeren sırasız bir koleksiyon yapısıdır. Küme veri yapısı, öğelerin sırasız olması ve her öğenin yalnızca bir kez bulunmasıyla karakterizedir.

#### Set Tanımlama

```dart
void main() {
  Set<int> sayilar = {1, 2, 3, 4, 5};
  Set<String> meyveler = {'elma', 'armut', 'portakal'};
}
```

#### Set'e Ekleme ve Çıkarma

```dart
void main() {
  Set<int> sayilar = {1, 2, 3};

  // Eleman eklemek
  sayilar.add(4);  // Küme tekrarlanan öğeleri kabul etmez.
  
  // Eleman çıkarmak
  sayilar.remove(2);
}
```

#### Set’e Erişim

Setlerde öğelere indeksli olarak erişilemez. Ancak `contains()` fonksiyonu ile öğe olup olmadığını kontrol edebilirsiniz.

```dart
void main() {
  Set<int> sayilar = {1, 2, 3, 4};

  // Set'te bir öğe var mı kontrolü
  print(sayilar.contains(3));  // true
}
```

### 6.3 `Map` (Harita)

`Map`, anahtar-değer çiftlerinden oluşan bir koleksiyon yapısıdır. Her anahtar bir değere karşılık gelir ve her anahtar sadece bir kez kullanılabilir.

#### Map Tanımlama

```dart
void main() {
  // String anahtarlar ve String değerler
  Map<String, String> kisiler = {
    'Ali': 'Öğrenci',
    'Ayşe': 'Öğretmen',
    'Mehmet': 'Mühendis'
  };
  
  // Anahtarlar ve değerler ile Map
  Map<int, String> kisiler2 = {
    1: 'Ali',
    2: 'Ayşe',
    3: 'Mehmet'
  };
}
```

#### Map’e Ekleme ve Çıkarma

```dart
void main() {
  Map<String, String> kisiler = {'Ali': 'Öğrenci'};

  // Anahtar-değer eklemek
  kisiler['Ayşe'] = 'Öğretmen';

  // Anahtar-değer çıkarmak
  kisiler.remove('Ali');
}
```

#### Map’e Erişim

```dart
void main() {
  Map<String, String> kisiler = {
    'Ali': 'Öğrenci',
    'Ayşe': 'Öğretmen'
  };

  // Anahtar üzerinden değere erişim
  print(kisiler['Ali']);  // Öğrenci
}
```

### 6.4 Koleksiyon Fonksiyonları

Dart dilinde koleksiyonlar üzerinde işlem yapmak için kullanabileceğiniz birçok fonksiyon bulunur. Bu fonksiyonlar genellikle koleksiyonun her bir elemanı üzerinde işlem yapar.

#### `map()` Fonksiyonu

`map()` fonksiyonu, koleksiyonun her bir elemanı üzerinde dönüşüm yapar ve yeni bir koleksiyon döndürür.

```dart
void main() {
  List<int> sayilar = [1, 2, 3, 4];
  
  // Sayıları iki katına çıkaran bir map fonksiyonu
  var yeniSayilar = sayilar.map((sayi) => sayi * 2).toList();
  
  print(yeniSayilar);  // [2, 4, 6, 8]
}
```

#### `where()` Fonksiyonu

`where()` fonksiyonu, koleksiyondaki öğeler üzerinde filtreleme yapar ve bir koşula uyan öğeleri döndürür.

```dart
void main() {
  List<int> sayilar = [1, 2, 3, 4, 5];
  
  // 3'ten büyük sayıları seç
  var sonuc = sayilar.where((sayi) => sayi > 3).toList();
  
  print(sonuc);  // [4, 5]
}
```

#### `reduce()` Fonksiyonu

`reduce()` fonksiyonu, koleksiyondaki öğeleri birleştirerek tek bir sonuç döndürür. Örneğin, sayıları toplamak için kullanılabilir.

```dart
void main() {
  List<int> sayilar = [1, 2, 3, 4];
  
  // Sayıları toplamak
  int toplam = sayilar.reduce((deger1, deger2) => deger1 + deger2);
  
  print(toplam);  // 10
}
```

#### `fold()` Fonksiyonu

`fold()` fonksiyonu, `reduce()`'e benzer ancak bir başlangıç değeri kabul eder. Bu değer, koleksiyonun ilk öğesi ile işlemi başlatır.

```dart
void main() {
  List<int> sayilar = [1, 2, 3, 4];
  
  // Başlangıç değeri ile toplama
  int toplam = sayilar.fold(0, (deger1, deger2) => deger1 + deger2);
  
  print(toplam);  // 10
}
```

### 6.5 Spread ve Null-Aware Spread Operatörleri

#### Spread Operatörü (`...`)

Spread operatörü, bir koleksiyonun öğelerini başka bir koleksiyona eklemek için kullanılır.

```dart
void main() {
  List<int> sayilar = [1, 2, 3];
  List<int> yeniSayilar = [...sayilar, 4, 5];
  
  print(yeniSayilar);  // [1, 2, 3, 4, 5]
}
```

#### Null-Aware Spread Operatörü (`...?`)

Null-aware spread operatörü, koleksiyonun null olup olmadığını kontrol eder ve eğer null değilse öğeleri ekler.

```dart
void main() {
  List<int>? sayilar = [1, 2, 3];
  List<int> yeniSayilar = [...?sayilar, 4, 5];
  
  print(yeniSayilar);  // [1, 2, 3, 4, 5]
}
```

### 6.6 Koleksiyon `if` ve `for` Kullanımı

Dart dilinde, koleksiyonlara öğe eklerken `if` ve `for` yapıları da kullanılabilir.

#### Koleksiyon `if` Kullanımı

```dart
void main() {
  List<int> sayilar = [1, 2, 3];
  bool ekle = true;

  var yeniSayilar = [
    0,
    if (ekle) 4,
    5
  ];

  print(yeniSayilar);  // [0, 4, 5]
}
```

#### Koleksiyon `for` Kullanımı

```dart
void main() {
  List<int> sayilar = [1, 2, 3];

  var yeniSayilar = [
    for (var sayi in sayilar) sayi * 2
  ];

  print(yeniSayilar);  // [2, 4, 6]
}
```

## 7. Sınıflar ve Nesne Tabanlı Programlama

### 7.1 Sınıf ve Nesne Tanımı

Dart dilinde, sınıflar nesnelerin yapılarını ve davranışlarını tanımlar. Bir sınıf, verileri (özellikler) ve bu verilere karşılık gelen işlemleri (metodlar) içerir. 

#### Sınıf Tanımlama

```dart
class Araba {
  // Özellikler
  String marka;
  String model;
  int yil;

  // Constructor (kurucu metod)
  Araba(this.marka, this.model, this.yil);

  // Metodlar
  void bilgileriGoster() {
    print('Marka: $marka, Model: $model, Yıl: $yil');
  }
}

void main() {
  // Nesne oluşturma
  var araba1 = Araba('Toyota', 'Corolla', 2020);
  araba1.bilgileriGoster();  // Marka: Toyota, Model: Corolla, Yıl: 2020
}
```

- `Araba` sınıfı, 3 özellik (`marka`, `model`, `yil`) ve 1 metod (`bilgileriGoster()`) içerir.
- `this.marka`, `this.model` ve `this.yil`, nesne oluşturulurken verilen değerleri alır.

### 7.2 Constructor (Kurucu Metodlar)

Constructor, bir sınıftan nesne oluşturulurken otomatik olarak çağrılan bir metoddur. Sınıfın özelliklerine başlangıç değerlerini atamak için kullanılır. Dart'ta constructor iki şekilde tanımlanabilir:

#### 7.2.1 Klasik Constructor

```dart
class Araba {
  String marka;
  String model;
  int yil;

  // Constructor
  Araba(String marka, String model, int yil)
      : this.marka = marka,
        this.model = model,
        this.yil = yil;

  void bilgileriGoster() {
    print('Marka: $marka, Model: $model, Yıl: $yil');
  }
}
```

#### 7.2.2 Kısa Constructor

Dart, constructor tanımlarken daha kısa bir sözdizimi sunar. `this` anahtar kelimesi ile doğrudan özelliğe değer ataması yapılabilir.

```dart
class Araba {
  String marka;
  String model;
  int yil;

  // Kısa constructor
  Araba(this.marka, this.model, this.yil);

  void bilgileriGoster() {
    print('Marka: $marka, Model: $model, Yıl: $yil');
  }
}
```

### 7.3 `this` Anahtar Kelimesi

`this` anahtar kelimesi, sınıfın içinde bulunduğunuz nesneye referans verir. Özellikle constructor içinde, nesnenin özelliklerine değer atamak için kullanılır.

```dart
class Kisi {
  String isim;

  // Constructor
  Kisi(this.isim);

  // Metod
  void selamVer() {
    print('Merhaba, benim adım $isim!');
  }
}

void main() {
  var kisi = Kisi('Ahmet');
  kisi.selamVer();  // Merhaba, benim adım Ahmet!
}
```

- `this.isim`, `Kisi` sınıfındaki `isim` özelliğine referans verir.

### 7.4 Getter & Setter

Getter ve setter, bir sınıfın özel (private) özelliklerine erişimi kontrol etmek için kullanılır. Dart’ta getter ve setter metotları, özellikle veri kapsülleme (encapsulation) sağlamak için faydalıdır.

#### Getter

```dart
class Daire {
  double _yaricap;  // private değişken

  Daire(this._yaricap);

  // Getter
  double get yaricap => _yaricap;
}

void main() {
  var daire = Daire(5.0);
  print(daire.yaricap);  // 5.0
}
```

#### Setter

```dart
class Daire {
  double _yaricap;

  Daire(this._yaricap);

  // Getter
  double get yaricap => _yaricap;

  // Setter
  set yaricap(double yeniYaricap) {
    if (yeniYaricap > 0) {
      _yaricap = yeniYaricap;
    }
  }
}

void main() {
  var daire = Daire(5.0);
  print(daire.yaricap);  // 5.0

  // Setter kullanarak yarıçapı değiştirme
  daire.yaricap = 10.0;
  print(daire.yaricap);  // 10.0
}
```

- `_yaricap` private bir değişkendir. `yaricap` getter ve setter kullanılarak kontrol edilir.

### 7.5 `static` Üyeler

`static` anahtar kelimesi, bir sınıfın özelliğinin veya metodunun nesneye bağlı olmadığını, sınıfın kendisine ait olduğunu belirtir. `static` üyeler sınıfın her örneği tarafından paylaşılan bir özelliktir.

#### Static Özellik ve Metodlar

```dart
class Matematik {
  static double pi = 3.14;

  static double alanHesapla(double yaricap) {
    return pi * yaricap * yaricap;
  }
}

void main() {
  print(Matematik.pi);  // 3.14
  print(Matematik.alanHesapla(5));  // 78.5
}
```

- `pi` ve `alanHesapla()` metodu, `Matematik` sınıfına aittir ve nesne oluşturulmadan sınıf adı üzerinden erişilebilir.

### 7.6 `late` Anahtar Kelimesi

`late` anahtar kelimesi, bir değişkenin başlatılacağını, ancak başlatılmadan önce kullanılmayacağı anlamına gelir. Bu, özellikle nullable tipler için, bir değişkenin null olmayan bir değere daha sonra atanacağı durumlar için kullanılır.

```dart
class Kullanici {
  late String ad;  // `late` ile değişken bildirilir

  void isimAta(String yeniAd) {
    ad = yeniAd;
  }

  void bilgileriGoster() {
    print('Kullanıcının adı: $ad');
  }
}

void main() {
  var kisi = Kullanici();
  kisi.isimAta('Ahmet');
  kisi.bilgileriGoster();  // Kullanıcının adı: Ahmet
}
```

- `late` anahtar kelimesi, değişkenin başlatılmadan önce kullanılmayacağı garantisini verir.

### 7.7 Factory Constructor (Fabrika Constructor)

`factory` constructor, nesne oluşturulmadan önce bazı işlemleri yapabilen ve nesne döndürebilen özel bir constructor türüdür. Bu, nesne oluşturulmadan önce bazı hesaplamalar yapmanıza veya aynı nesneyi tekrar kullanmanıza olanak tanır.

#### Factory Constructor Kullanımı

```dart
class Singleton {
  static final Singleton _instance = Singleton._private();

  // Private constructor
  Singleton._private();

  // Factory constructor
  factory Singleton() {
    return _instance;
  }

  void mesajYaz() {
    print('Bu bir Singleton örneğidir!');
  }
}

void main() {
  var obj1 = Singleton();
  var obj2 = Singleton();
  print(identical(obj1, obj2));  // true, çünkü aynı nesne kullanılıyor
}
```

- `Singleton` sınıfı, yalnızca bir nesne örneği yaratılmasına olanak sağlar. `factory` constructor, `_instance` nesnesini döndürerek aynı nesneyi sürekli kullanır.

## 8. Kalıtım ve Polimorfizm

### 8.1 `extends`, `super`, `@override`

#### `extends` Anahtar Kelimesi

Kalıtım, bir sınıfın başka bir sınıfın özelliklerini ve metodlarını devralmasına olanak tanır. Dart’ta kalıtım `extends` anahtar kelimesi ile yapılır.

```dart
class Hayvan {
  void sesCikar() {
    print('Hayvan ses çıkarıyor');
  }
}

class Kedi extends Hayvan {
  @override
  void sesCikar() {
    print('Miyav');
  }
}

void main() {
  var kedi = Kedi();
  kedi.sesCikar();  // Miyav
}
```

- `Kedi` sınıfı, `Hayvan` sınıfından kalıtım alır ve `sesCikar` metodunu override eder.
- `@override` anahtar kelimesi, bir metodun üst sınıfta var olan bir metodla değiştirildiğini belirtir.

#### `super` Anahtar Kelimesi

`super`, üst sınıfın metodlarına ve özelliklerine erişim sağlar. Bu, kalıtım aldığınız sınıfın fonksiyonelliklerini kullanırken faydalıdır.

```dart
class Hayvan {
  String isim;

  Hayvan(this.isim);

  void bilgiYazdir() {
    print('Hayvanın adı: $isim');
  }
}

class Kedi extends Hayvan {
  Kedi(String isim) : super(isim);  // super, üst sınıfın constructor'ını çağırır
}

void main() {
  var kedi = Kedi('Maviş');
  kedi.bilgiYazdir();  // Hayvanın adı: Maviş
}
```

- `super(isim)`, `Hayvan` sınıfının constructor’ını çağırarak `isim` değerini üst sınıfa iletir.

### 8.2 Soyut Sınıflar: `abstract` Anahtar Kelimesi

Soyut sınıflar, doğrudan nesne oluşturulamaz ancak diğer sınıflar tarafından kalıtım alınabilir. Soyut sınıflar, belirli metodları alt sınıflara bırakabilir. `abstract` anahtar kelimesi ile tanımlanır.

```dart
abstract class Sekil {
  double alanHesapla();  // Soyut metod, alt sınıflar implement etmek zorunda

  void yazdir() {
    print('Bu bir şekildir');
  }
}

class Daire extends Sekil {
  double yaricap;

  Daire(this.yaricap);

  @override
  double alanHesapla() {
    return 3.14 * yaricap * yaricap;
  }
}

void main() {
  var daire = Daire(5.0);
  print('Alan: ${daire.alanHesapla()}');  // Alan: 78.5
}
```

- `Sekil` soyut sınıfı, `alanHesapla()` metodunun alt sınıflarda tanımlanmasını zorunlu kılar. `yazdir()` ise hem soyut hem de implementasyonu sağlanmış bir metoddur.

### 8.3 Arayüzler ve Mixin Kullanımı: `implements`, `with`

#### `implements` Anahtar Kelimesi

Arayüzler, sadece metodların imzalarını içerir; metodlar alt sınıflar tarafından implement edilmek zorundadır. Dart’ta bir sınıf, bir arayüzü `implements` anahtar kelimesi ile implement edebilir.

```dart
class Ucan {
  void ucmak();
}

class Kus implements Ucan {
  @override
  void ucmak() {
    print('Kuş uçuyor');
  }
}

void main() {
  var kus = Kus();
  kus.ucmak();  // Kuş uçuyor
}
```

- `Kus` sınıfı, `Ucan` arayüzünü implement eder ve `ucmak()` metodunu kendisi tanımlar.

#### `with` Anahtar Kelimesi (Mixin Kullanımı)

Mixin, bir sınıfın özelliklerini başka bir sınıfa eklemek için kullanılır. Bir sınıf, bir veya birden fazla mixin ile davranışlarını genişletebilir.

```dart
mixin Yuzme {
  void yuz() {
    print('Yüzüyorum');
  }
}

class Insan {
  void konus() {
    print('Merhaba');
  }
}

class Yuzucu extends Insan with Yuzme {
  void yuzmeYap() {
    yuz();
  }
}

void main() {
  var yuzucu = Yuzucu();
  yuzucu.konus();  // Merhaba
  yuzucu.yuzmeYap();  // Yüzüyorum
}
```

- `Yuzme` mixini, `Yuzucu` sınıfına `yuz()` metodunu ekler. Burada `with Yuzme` kullanılarak mixin sınıfın işlevselliğine dahil edilir.

### 8.4 Polimorfizm

Polimorfizm, bir nesnenin farklı türlerde davranmasını sağlar. Dart'ta polimorfizm, genellikle bir sınıfın metodunun alt sınıflarda farklı şekillerde implement edilmesiyle sağlanır.

```dart
class Sekil {
  void alanHesapla() {
    print('Şeklin alanı hesaplanıyor');
  }
}

class Daire extends Sekil {
  @override
  void alanHesapla() {
    print('Dairenin alanı hesaplanıyor');
  }
}

class Kare extends Sekil {
  @override
  void alanHesapla() {
    print('Karenin alanı hesaplanıyor');
  }
}

void main() {
  Sekil daire = Daire();
  Sekil kare = Kare();

  daire.alanHesapla();  // Dairenin alanı hesaplanıyor
  kare.alanHesapla();  // Karenin alanı hesaplanıyor
}
```

- `Sekil` sınıfı, `Daire` ve `Kare` sınıflarının ortak bir üst sınıfıdır. Her iki sınıf da `alanHesapla()` metodunu farklı şekillerde implement eder. Bu, polimorfizmi sağlar.

## 9. Hata Yönetimi

### 9.1 `try`, `catch`, `finally`

#### `try` Bloku

Bir hata meydana gelmesi muhtemel olan kodları `try` bloğu içine alırsınız. Eğer bir hata meydana gelirse, bu hata `catch` bloğunda yakalanır.

```dart
void sayiBölme() {
  try {
    var sonuc = 10 ~/ 0;  // Hata meydana gelir (sıfıra bölme)
    print('Sonuç: $sonuc');
  } catch (e) {
    print('Hata oluştu: $e');
  }
}

void main() {
  sayiBölme();  // Hata oluştu: IntegerDivisionByZeroException
}
```

- Burada `try` bloğunda, sıfıra bölme hatası yapılmaktadır. Bu hata `catch` bloğunda yakalanır ve hata mesajı yazdırılır.

#### `catch` Bloku

Hata meydana geldiğinde, `catch` bloğu devreye girer. `catch` bloğunda hata ile ilgili daha fazla bilgi alabilirsiniz. Hata objesinin `e` olarak alınması yaygın bir yöntemdir.

```dart
void sayiBölme() {
  try {
    var sonuc = 10 ~/ 0;
    print('Sonuç: $sonuc');
  } catch (e) {
    print('Hata oluştu: $e');
  }
}
```

- `catch (e)` ifadesi, hata mesajını almak için kullanılır. `e` burada hata objesini temsil eder.

#### `finally` Bloku

`finally` bloğu, hata oluşup oluşmamasına bakılmaksızın her durumda çalıştırılır. Genellikle kaynakların serbest bırakılması, dosya kapama veya bağlantı sonlandırma gibi işlemler için kullanılır.

```dart
void dosyaIslemi() {
  try {
    print('Dosya açıldı');
    // Dosya işlemleri burada yapılabilir
  } catch (e) {
    print('Hata oluştu: $e');
  } finally {
    print('Dosya kapatıldı');
  }
}

void main() {
  dosyaIslemi();
  // Çıktı:
  // Dosya açıldı
  // Dosya kapatıldı
}
```

- `finally` bloğu her durumda çalışır ve burada dosyanın kapatılması sağlanır.

### 9.2 `throw` Kullanımı

Bir hata meydana geldiğinde, hata fırlatmak için `throw` anahtar kelimesi kullanılır. `throw` ile, programınıza özel hata mesajları oluşturabilirsiniz.

```dart
void pozitifSayi(int sayi) {
  if (sayi < 0) {
    throw FormatException('Negatif sayılar kabul edilmez');
  }
  print('Sayı pozitif: $sayi');
}

void main() {
  try {
    pozitifSayi(-5);
  } catch (e) {
    print('Hata: $e');
  }
}
```

- `throw` ile özel bir hata fırlatılır. Burada negatif sayılarla ilgili bir hata kontrolü yapılır ve hata mesajı `FormatException` ile birlikte fırlatılır.

### 9.3 Özel Exception Sınıfı Tanımlama

Kendi özel hata sınıflarınızı tanımlayarak daha anlaşılır ve özel hata mesajları oluşturabilirsiniz. Bunun için Dart’ta `Exception` sınıfından türeyen yeni bir sınıf oluşturabilirsiniz.

```dart
class NegatifSayiException implements Exception {
  String cause;
  NegatifSayiException(this.cause);

  @override
  String toString() {
    return 'NegatifSayiException: $cause';
  }
}

void pozitifSayi(int sayi) {
  if (sayi < 0) {
    throw NegatifSayiException('Negatif sayı verilemez');
  }
  print('Sayı pozitif: $sayi');
}

void main() {
  try {
    pozitifSayi(-5);
  } catch (e) {
    print(e);  // NegatifSayiException: Negatif sayı verilemez
  }
}
```

- `NegatifSayiException` özel bir hata sınıfı olarak tanımlandı. `implements Exception` ile Dart’ın yerleşik `Exception` sınıfını implement ettik. `toString` metodunu override ederek daha anlaşılır bir hata mesajı döndürüyoruz.

## 10. Null Safety

### 10.1 Nullable ve Non-Nullable Tipler

Dart 2.12 ve sonrasında, Dart diline null güvenliği (null safety) özelliği eklenmiştir. Bu, değişkenlerin null olup olamayacağına dair kesin kurallar getirir. Varsayılan olarak, bir değişkenin null olabilmesi için onu açıkça nullable olarak belirtmeniz gerekir. 

#### **Non-Nullable Tipler**

Non-nullable tipler, null olamayacak veri türleridir. Eğer bir değişken non-nullable olarak tanımlanmışsa, bu değişkenin mutlaka bir değer alması gerekir.

```dart
int sayi = 10;  // Non-nullable, bu değişken null olamaz
```

Burada `sayi` değişkeni `int` türünde olup, null olamaz. Eğer null bir değer atamaya çalışırsak, derleme hatası alırız.

```dart
int sayi;
sayi = null;  // Hata: A non-nullable variable must be initialized.
```

#### **Nullable Tipler**

Nullable tipler, null değerini kabul edebilen veri türleridir. Bir değişkenin nullable olması için türün sonuna `?` eklenir.

```dart
int? sayi = null;  // Nullable, bu değişken null olabilir
```

Burada `sayi` değişkeni nullable olup null değerini alabilir. Ancak, null bir değer ile işlem yapılmadan önce bu kontrol edilmelidir.

### 10.2 Null Kontrolü ve Operatörler

#### **Null-aware Operatörler**

Null değerler ile çalışırken, programın hata vermemesi için çeşitli operatörler kullanılır. Dart, null kontrolü için bir dizi operatör sağlar.

- **`?` Operatörü (Null-aware Access)**

Bir nullable değişkenin bir özelliğine veya metoduna erişmek için `?` operatörü kullanılır. Bu, eğer değişken `null` ise, null döndürmesini sağlar.

```dart
String? isim = null;
print(isim?.length);  // null döndürür, çünkü isim null
```

- **`??` Operatörü (Null-coalescing Operator)**

Eğer bir nullable değişkenin değeri `null` ise, `??` operatörü ile alternatif bir değer sağlanabilir.

```dart
String? isim = null;
print(isim ?? 'Bilinmiyor');  // 'Bilinmiyor' döndürülür
```

- **`!` Operatörü (Null Check)**

Nullable bir değişkenin kesinlikle `null` olmadığından emin olunduğunda, `!` operatörü ile null değerinin atlanması sağlanır. Ancak, bu operatör yalnızca değişkenin null olmayacağı kesinse kullanılmalıdır.

```dart
String? isim = 'Ali';
print(isim!.length);  // Bu, null değilse çalışır. null ise hata verir.
```

#### **Null-aware Collection Operatörleri**

- **Null-aware spread (`...?`)**: Bir koleksiyonun `null` olmasını kontrol eder ve `null` ise koleksiyona ekleme işlemi yapmaz.

```dart
List<int>? sayilar = [1, 2, 3];
List<int> yeniSayilar = [...?sayilar];  // sayilar null değilse elemanlar eklenir
print(yeniSayilar);  // [1, 2, 3]
```

Eğer `sayilar` null olursa, `yeniSayilar` boş bir liste olur.

### 10.3 `late` ve `required` Kullanım Senaryoları

#### **`late` Anahtar Kelimesi**

`late` anahtar kelimesi, bir değişkenin başlangıçta `null` olacağını, ancak sonradan mutlaka bir değer alacağını belirtir. Bu, özellikle değişkenlerin hemen başlatılamadığı durumlarda kullanılır.

```dart
late String isim;
isim = 'Ahmet';
print(isim);  // Ahmet
```

- `late` anahtar kelimesi, değişkenin değeri sonradan atanacağı garantisini verir. Eğer `late` ile işaretlenmiş bir değişkeni null olarak kullanmaya çalışırsanız, runtime hatası alırsınız.

```dart
late String isim;
print(isim);  // Hata: LateInitializationError: Field 'isim' has not been initialized.
```

#### **`required` Anahtar Kelimesi**

`required` anahtar kelimesi, özellikle fonksiyon parametrelerinde kullanılır ve parametrenin null olamayacağını belirtir. Bu, özellikle nullable tipleri kullanırken, parametrelerin doğru şekilde verilmesini garanti eder.

```dart
void selamVer({required String isim}) {
  print('Merhaba, $isim!');
}

void main() {
  selamVer(isim: 'Ahmet');  // Çalışır
  // selamVer();  // Hata: The parameter 'isim' is required.
}
```

- `required` ile işaretlenmiş parametreler, fonksiyona çağrıldığında mutlaka verilmelidir.

## 11. Asenkron Programlama

### 11.1 `Future`, `async`, `await`

#### **`Future`**

Bir `Future`, gelecekte bir noktada tamamlanacak bir işlemi temsil eder. Bu, genellikle bir ağ isteği veya dosya okuma gibi zaman alacak işlemler için kullanılır. `Future` bir değeri veya bir hata döndürebilir.

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));  // 2 saniye bekler
  return 'Veri başarıyla alındı';
}

void main() async {
  String veri = await fetchData();
  print(veri);  // 'Veri başarıyla alındı'
}
```

- `Future.delayed` metodu, belirtilen süre kadar bekler ve ardından sonucu döndürür.
- `await` anahtar kelimesi, `Future` tamamlanana kadar işlem sırasını durdurur.

#### **`async`**

Bir fonksiyonu asenkron hale getirmek için `async` anahtar kelimesi kullanılır. Bu fonksiyon, bir `Future` döndürecektir.

```dart
Future<String> getData() async {
  await Future.delayed(Duration(seconds: 3));
  return 'Asenkron veri';
}

void main() async {
  String data = await getData();
  print(data);  // 'Asenkron veri'
}
```

- `async` anahtar kelimesi, fonksiyonun asenkron olduğunu belirtir ve `await` kullanarak asenkron işlemlerin beklenmesini sağlar.

#### **`await`**

`await`, bir `Future`'ın tamamlanmasını bekler ve sonucu geri döndürür. `await` sadece `async` fonksiyonları içinde kullanılabilir.

```dart
Future<int> getNumber() async {
  return 42;
}

void main() async {
  int num = await getNumber();
  print(num);  // 42
}
```

### 11.2 `Stream` ve `await for`

#### **`Stream`**

Bir `Stream`, bir dizi asenkron veriyi temsil eder. Özellikle sürekli olarak veri üreten kaynaklardan (örneğin, sensörler, kullanıcı etkileşimleri, veri akışları) gelen veriyi işlemek için kullanılır. `Stream` veriyi parçalar halinde yayar ve her yeni veri geldiğinde `Stream` dinleyicisi (`listener`) devreye girer.

```dart
Stream<int> countStream() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

void main() async {
  await for (var number in countStream()) {
    print(number);  // 1, 2, 3, 4, 5 sırasıyla yazdırılır
  }
}
```

- `async*` ile bir `Stream` fonksiyonu oluşturulur. `yield` anahtar kelimesi, her adımda bir veri parçası yayınlar.
- `await for` ile bir `Stream`'i dinleriz ve gelen her yeni veriyi işleyebiliriz.

#### **`await for`**

`await for`, bir `Stream`'den gelen verileri asenkron bir şekilde alır ve her yeni veriyi işlemeye başlar.

```dart
Stream<int> numberStream() async* {
  yield 1;
  yield 2;
  yield 3;
}

void main() async {
  await for (var number in numberStream()) {
    print(number);  // 1, 2, 3 sırasıyla yazdırılır
  }
}
```

- Burada, `await for` ile `numberStream`'den gelen her sayıyı alıyoruz ve hemen işlem yapıyoruz.

### 11.3 `then()`, `catchError()`, `onError()`

#### **`then()`**

`then()` metodu, bir `Future` tamamlandığında çalıştırılacak bir fonksiyon belirtir. Bu, gelen sonucu işlemenizi sağlar.

```dart
Future<int> fetchNumber() async {
  return 42;
}

void main() {
  fetchNumber().then((value) {
    print('Sonuç: $value');  // Sonuç: 42
  });
}
```

- `then()` metodu, `Future` tamamlandıktan sonra çalışacak kodu tanımlar.

#### **`catchError()`**

Bir `Future`'da bir hata oluşursa, bu hatayı `catchError()` ile yakalayabilirsiniz.

```dart
Future<int> riskyOperation() async {
  throw 'Bir hata oluştu';
}

void main() {
  riskyOperation().catchError((e) {
    print('Hata: $e');  // Hata: Bir hata oluştu
  });
}
```

- `catchError()` metodu, `Future` hatası olduğunda çağrılır ve hatayı işler.

#### **`onError()`**

`onError()` metodu, hata durumunda alternatif bir işleyiş sağlar.

```dart
Future<int> riskyOperation() async {
  throw 'Bir hata oluştu';
}

void main() {
  riskyOperation().then((value) {
    print('Sonuç: $value');
  }).onError((error, stackTrace) {
    print('Hata oluştu: $error');
  });
}
```

- `onError()` metodu, `Future` işleminde bir hata meydana geldiğinde hata mesajını ve yığın izini yakalar.

### 11.4 `FutureBuilder` ve `StreamBuilder` (Flutter tarafında)

#### **`FutureBuilder`**

`FutureBuilder`, bir `Future`'ın durumunu izleyerek UI'yi günceller. Bu, genellikle ağ istekleri gibi zaman alıcı işlemlerden sonra UI'yi güncellemek için kullanılır.

```dart
Future<String> fetchData() async {
  await Future.delayed(Duration(seconds: 2));
  return 'Veri başarıyla alındı';
}

Widget build(BuildContext context) {
  return FutureBuilder<String>(
    future: fetchData(),
    builder: (context, snapshot) {
      if (snapshot.connectionState == ConnectionState.waiting) {
        return CircularProgressIndicator();  // Yükleniyor
      } else if (snapshot.hasError) {
        return Text('Hata: ${snapshot.error}');
      } else {
        return Text('Sonuç: ${snapshot.data}');
      }
    },
  );
}
```

- `FutureBuilder`, `future` parametresindeki `Future` tamamlandığında UI'yi günceller.

#### **`StreamBuilder`**

`StreamBuilder`, bir `Stream`'i dinler ve her veri geldiğinde UI'yi günceller.

```dart
Stream<int> countStream() async* {
  for (int i = 1; i <= 5; i++) {
    await Future.delayed(Duration(seconds: 1));
    yield i;
  }
}

Widget build(BuildContext context) {
  return StreamBuilder<int>(
    stream: countStream(),
    builder: (context, snapshot) {
      if (snapshot.connectionState == ConnectionState.waiting) {
        return CircularProgressIndicator();  // Yükleniyor
      } else if (snapshot.hasError) {
        return Text('Hata: ${snapshot.error}');
      } else {
        return Text('Sayac: ${snapshot.data}');
      }
    },
  );
}
```

- `StreamBuilder`, `stream` parametresindeki `Stream`'den gelen verileri alır ve UI'yi her yeni veriyle günceller.

## 12. Modüler Kodlama ve Paketler

### 12.1 Dosya Yapısı, `import` Kullanımı

Dart dilinde modüler bir yapı kurmak için dosya ve klasörler kullanılır. Projelerde, her dosya belirli bir sorumluluğu üstlenir ve kodun daha yönetilebilir olmasını sağlar. Modüler yapıyı kurarken, dosyaları organize etmek ve birbirleriyle etkileşime girmelerini sağlamak için `import` kullanılır.

#### Dosya Yapısı

Bir Dart projesinin tipik dosya yapısı aşağıdaki gibi olabilir:

```
my_project/
  lib/
    main.dart
    utils.dart
    models/
      user.dart
    services/
      api_service.dart
  pubspec.yaml
```

Bu yapıda:

- `lib/`: Uygulamanın ana kodlarının bulunduğu klasördür. Uygulama dışındaki kaynaklar (görseller, statik dosyalar) burada yer almaz.
- `main.dart`: Uygulamanın başlangıç noktasıdır.
- `utils.dart`: Yardımcı fonksiyonların bulunduğu dosya.
- `models/`: Veritabanı modelleri, iş mantığı gibi verileri temsil eden sınıfların bulunduğu klasör.
- `services/`: API bağlantıları gibi servislerin bulunduğu klasör.

#### `import` Kullanımı

Dosyalar arasında etkileşim kurmak için `import` anahtar kelimesi kullanılır. Örneğin, `utils.dart` dosyasındaki fonksiyonları `main.dart` dosyasına almak için şu şekilde yazabiliriz:

```dart
// utils.dart
String greet(String name) {
  return 'Hello, $name!';
}

// main.dart
import 'utils.dart';

void main() {
  print(greet('Dart'));  // Hello, Dart!
}
```

- `import` ile bir dosya diğer dosyada tanımlanan fonksiyonları, sınıfları ve değişkenleri kullanabilir hale gelir.

### 12.2 Kendi Dosyalarını Modül Olarak Kullanmak

Kendi dosyalarınızı modül olarak kullanmak için, dışarıya açmak istediğiniz fonksiyonları, sınıfları veya değişkenleri doğru bir şekilde tanımlamanız gerekir. Örneğin, bir dosyada tanımlı fonksiyonları başka bir dosyada kullanabilmek için o dosyayı import etmek yeterlidir.

```dart
// utilities.dart
int add(int a, int b) {
  return a + b;
}

// main.dart
import 'utilities.dart';

void main() {
  print(add(2, 3));  // 5
}
```

Bu şekilde, `utilities.dart` dosyasındaki `add` fonksiyonu `main.dart` dosyasına aktarılır ve kullanılır.

### 12.3 `pubspec.yaml` ve Paket Yönetimi

Dart projelerinde dış kütüphaneleri yönetmek için `pubspec.yaml` dosyası kullanılır. Bu dosya, projede kullanılan paketlerin listesini içerir ve uygulamanın bağımlılıklarını belirtir. Örneğin:

```yaml
name: my_project
description: A new Dart project
dependencies:
  http: ^0.13.3
  path: ^1.8.0
```

Bu örnekte:

- `dependencies` altında kullanılan paketlerin sürüm bilgileri belirtilir.
- `http` ve `path` gibi popüler paketler, proje için gerekli olan dış kütüphanelerdir.

`pubspec.yaml` dosyasındaki değişikliklerin ardından bağımlılıkları güncellemek için terminalde şu komut çalıştırılır:

```bash
dart pub get
```

Bu komut, belirtilen paketleri indirir ve proje için hazır hale getirir.

### 12.4 Yaygın Kullanılan Paketler

Dart ekosisteminde, farklı türde projelerde kullanabileceğiniz birçok popüler paket bulunmaktadır. İşte bazıları:

#### `http` Paketi

- HTTP istekleri göndermek ve almak için kullanılır.
- Web API’leri ile iletişim kuran projelerde yaygın olarak kullanılır.

Örnek kullanım:

```dart
import 'package:http/http.dart' as http;

Future<void> fetchData() async {
  final response = await http.get(Uri.parse('https://jsonplaceholder.typicode.com/posts'));

  if (response.statusCode == 200) {
    print('Başarı: ${response.body}');
  } else {
    print('Hata: ${response.statusCode}');
  }
}

void main() {
  fetchData();
}
```

#### `path` Paketi

- Dosya yolu işlemleri için kullanılır. Dosya yolunu düzenlemek, çözümlemek gibi işlemleri kolaylaştırır.

Örnek kullanım:

```dart
import 'package:path/path.dart';

void main() {
  String filePath = '/user/documents/file.txt';
  String fileName = basename(filePath);
  print('Dosya adı: $fileName');  // file.txt
}
```

#### `intl` Paketi

- Uluslararasılaştırma ve yerelleştirme işlemleri için kullanılır. Tarih, saat, sayı formatlama gibi işlemleri kolaylaştırır.

Örnek kullanım:

```dart
import 'package:intl/intl.dart';

void main() {
  var now = DateTime.now();
  var formatter = DateFormat('yyyy-MM-dd');
  String formatted = formatter.format(now);
  print('Bugünün tarihi: $formatted');  // 2025-04-21
}
```

#### `shared_preferences` Paketi

- Uygulama içi basit veri saklama işlemleri için kullanılır. Örneğin, kullanıcının tercihleri veya geçici veriler.

Örnek kullanım:

```dart
import 'package:shared_preferences/shared_preferences.dart';

void saveData() async {
  final prefs = await SharedPreferences.getInstance();
  await prefs.setString('user_name', 'Dart');
}

void loadData() async {
  final prefs = await SharedPreferences.getInstance();
  String? userName = prefs.getString('user_name');
  print('Kullanıcı adı: $userName');
}
```

## 13. Test Yazımı

### 13.1 Unit Test ve Integration Test

#### Unit Test

Birim testleri, yazılımın küçük parçalarını (genellikle fonksiyonları veya metodları) bağımsız bir şekilde test etmek amacıyla yazılır. Birim testlerinde her şey izole edilmiştir ve dışsal faktörlerden bağımsız olarak sadece test edilen fonksiyonun doğruluğu kontrol edilir.

Birim testlerinin avantajları:
- Hızlı çalışır.
- Hata ayıklama işlemi daha kolaydır.
- Genellikle sınıfların veya fonksiyonların beklenen şekilde çalışıp çalışmadığını doğrulamak için kullanılır.

#### Integration Test

Entegrasyon testleri, farklı modüllerin veya sistem bileşenlerinin bir arada nasıl çalıştığını test etmek için kullanılır. Bu test türü, birim testlerine kıyasla daha büyük kapsamlıdır ve genellikle birden fazla bileşeni test eder.

Entegrasyon testlerinin avantajları:
- Birimlerin birlikte çalışıp çalışmadığını kontrol eder.
- Uygulama içindeki veri akışı ve bileşenler arasındaki etkileşimleri test eder.

### 13.2 `test` Paketi

Dart, birim ve entegrasyon testlerini yazmak için `test` paketini kullanır. Bu paket, testlerin yazılmasını ve çalıştırılmasını kolaylaştırır. Testler, genellikle `test` klasöründe bulunur ve `.dart` uzantılı dosyalar olarak yazılır.

#### **`test` Paketini Projeye Dahil Etme**

İlk adım, `pubspec.yaml` dosyanıza `test` paketini eklemektir:

```yaml
dev_dependencies:
  test: ^any
```

Daha sonra, terminalde şu komutu çalıştırarak bağımlılığı indirin:

```bash
dart pub get
```

#### Test Yazma

Bir test dosyası, genellikle `test` fonksiyonlarını kullanarak yazılır. `test()` fonksiyonu bir test senaryosu oluşturur ve beklenen sonuçları tanımlar. Test senaryoları, `expect()` fonksiyonu ile doğrulanır.

Örnek:

```dart
import 'package:test/test.dart';

void main() {
  test('Basit bir toplama testi', () {
    var result = 2 + 3;
    expect(result, 5);
  });

  test('String uzunluğu testi', () {
    var str = 'Dart';
    expect(str.length, 4);
  });
}
```

Burada:

- `test()` fonksiyonu, her bir test senaryosunu tanımlar.
- `expect()` fonksiyonu, beklenen sonucu kontrol eder.

#### Test Çalıştırma

Testlerinizi çalıştırmak için terminalde şu komutu kullanabilirsiniz:

```bash
dart test
```

Bu komut, tüm test dosyalarınızı çalıştırır ve sonuçları terminalde gösterir.

### 13.3 `mockito` Kullanımı

Testlerde genellikle dış bağımlılıkları (API çağrıları, veritabanı bağlantıları vb.) izole etmek ve kontrol etmek gerekir. Bunun için `mockito` paketini kullanarak bu bağımlılıkları taklit edebiliriz. `mockito`, Dart'ta nesne taklidi yapmanızı sağlar ve testlerinizi izole etmenize yardımcı olur.

#### `mockito` Paketini Projeye Dahil Etme

`pubspec.yaml` dosyanıza `mockito` paketini ve `mockito` ile uyumlu `build_runner` paketini eklemeniz gerekir:

```yaml
dev_dependencies:
  mockito: ^5.0.0
  build_runner: ^2.1.7
```

Daha sonra bağımlılıkları indirmek için şu komutu çalıştırın:

```bash
dart pub get
```

#### Mock Nesne Oluşturma

Bir sınıfı taklit etmek için, sınıfı ve onun metodlarını `mockito` kullanarak mock (taklit) edebilirsiniz. İşte bir örnek:

```dart
import 'package:test/test.dart';
import 'package:mockito/mockito.dart';

// Taklit sınıfı
class DatabaseService {
  String fetchData() => 'Gerçek veri';
}

// Taklit sınıfını oluşturma
class MockDatabaseService extends Mock implements DatabaseService {}

void main() {
  group('Veritabanı Servisi Testi', () {
    test('fetchData() doğru veri döndürmeli', () {
      // Mock nesnesi oluştur
      var mockDatabase = MockDatabaseService();

      // Beklenen davranışı tanımla
      when(mockDatabase.fetchData()).thenReturn('Test verisi');

      // Testi çalıştır
      var result = mockDatabase.fetchData();
      expect(result, 'Test verisi');
    });
  });
}
```

Bu örnekte:

- `MockDatabaseService` sınıfı, `DatabaseService` sınıfının bir mock versiyonudur.
- `when()` fonksiyonu ile, mock nesnesinin belirli bir metodunun nasıl davranacağını tanımlıyoruz.
- `thenReturn()` fonksiyonu, metodun döndüreceği değeri belirtir.

#### Mock Nesne Çalıştırma

Mock nesneleri kullanarak testlerinizi çalıştırdığınızda, dış bağımlılıklardan bağımsız şekilde işlevleri test edebilirsiniz. Böylece API istekleri veya veritabanı erişimi gibi dış etkenlerin testi etkilemesi engellenir.

### 13.4 Test Kapsamı ve İyi Uygulamalar

Test yazarken dikkat edilmesi gereken bazı iyi uygulamalar:

- **Testler küçük ve izole olmalı**: Her test yalnızca bir şey test etmeli ve dış bağımlılıklardan izole olmalıdır.
- **Testler anlaşılır olmalı**: Testlerinizi yazarken, testin amacı ve neyi doğruladığını açıkça belirtmelisiniz.
- **Mocking kullanımı**: Dış bağımlılıklar yerine mock nesneleri kullanarak testlerinizi izole edin.
- **Testlerinizi sık çalıştırın**: Testlerinizin sürekli geçerli olup olmadığını kontrol etmek için düzenli olarak testleri çalıştırın.

## 14. İleri Seviye Konular

### 14.1 Generics: `<T>` Kullanımı

Generics, Dart'ta tür güvenliğini sağlamak ve aynı kodu farklı veri türleriyle kullanabilmek için kullanılır. Generics, özellikle koleksiyonlar ve sınıflar için faydalıdır. Generics, belirli bir türü tanımlamadan, tip güvenliğiyle işlem yapmanıza olanak tanır.

#### Generics Tanımlaması

Bir generic sınıf veya fonksiyon tanımlarken, tür parametresi kullanılır. Tür parametresi, genellikle `T` harfiyle gösterilir, ancak istenirse başka isimler de kullanılabilir.

Örnek:

```dart
class Box<T> {
  T value;
  Box(this.value);

  T getValue() {
    return value;
  }
}

void main() {
  var intBox = Box<int>(10); // Integer tipiyle çalışan bir kutu
  print(intBox.getValue());  // 10

  var stringBox = Box<String>("Hello"); // String tipiyle çalışan bir kutu
  print(stringBox.getValue()); // Hello
}
```

Burada:

- `Box<T>` sınıfı, her türdeki veri ile çalışabilen bir generic sınıftır.
- `T` tür parametresidir, burada `int` ve `String` türleri kullanılmıştır.

#### Generics Fonksiyonlar

Fonksiyonlar da generic olarak tanımlanabilir. Bu şekilde, farklı türler için aynı fonksiyonu kullanabilirsiniz.

```dart
T printValue<T>(T value) {
  print(value);
  return value;
}

void main() {
  printValue<int>(5);   // 5
  printValue<String>("Dart"); // Dart
}
```

### 14.2 Extension Methods

Extension Methods (Uzantı Metodları), Dart'ın sınıflarına yeni metodlar eklemenize olanak tanır, ancak mevcut sınıfın kodunu değiştirmeden. Bu, özellikle dış kütüphaneleri kullanırken veya bazı sınıfların metodlarını genişletmek istediğinizde çok faydalıdır.

#### Extension Method Tanımlama

Extension method'lar, `extension` anahtar kelimesiyle tanımlanır ve belirli bir tür üzerinde yeni metodlar ekler.

Örnek:

```dart
extension StringReversal on String {
  String reverse() {
    return this.split('').reversed.join('');
  }
}

void main() {
  String str = "Dart";
  print(str.reverse());  // traD
}
```

Burada:

- `StringReversal` adında bir extension sınıfı tanımlanmış ve `String` türüne `reverse()` metodunu eklemişiz.
- `this` anahtar kelimesi, mevcut nesneyi temsil eder.

### 14.3 Isolates (Çoklu Thread)

Isolates, Dart'ta paralel işleme için kullanılan bir tekniktir. Dart, geleneksel çoklu iş parçacığı (thread) kullanımından farklı olarak, `Isolate` kullanır. Isolates, birbirinden bağımsız çalışan iş parçacıklarıdır ve kendi hafıza alanlarına sahiptirler. Bu, paralel işlem yaparken veri yarışması (race condition) gibi sorunların önüne geçer.

#### Isolate Kullanımı

Isolate'ler, `Isolate.spawn()` fonksiyonu ile başlatılır. Bu fonksiyon bir iş parçacığı oluşturur ve çalıştırılır.

Örnek:

```dart
import 'dart:async';
import 'dart:io';

void isolateFunction(String message) {
  print('Isolate: $message');
}

void main() {
  Isolate.spawn(isolateFunction, "Merhaba Isolate!");
  print('Main function');
}
```

Bu örnekte:

- `Isolate.spawn()` fonksiyonu ile yeni bir isolate başlatılır.
- `isolateFunction` fonksiyonu, izolasyonda çalıştırılacak işlemi tanımlar.

### 14.4 Meta-programlama (Annotations, `@override`, `@required`, vb.)

Meta-programlama, program kodunu çalışırken analiz etme veya değiştirme işlemidir. Dart'ta meta-programlama için anotasyonlar (annotations) ve `reflective` programlama kullanılabilir. 

#### Anotasyonlar (Annotations)

Dart'ta, sınıf, metod veya değişkenler üzerinde özel anotasyonlar eklenebilir. Bu, genellikle kodun daha anlaşılır olmasını sağlamak için kullanılır.

Örnek:

```dart
class Person {
  @override
  String toString() {
    return 'Person';
  }
}

void main() {
  var person = Person();
  print(person.toString());  // Person
}
```

Burada:

- `@override` anotasyonu, metodun bir üst sınıftan override (geçersiz kılma) edilmesini belirtir.
- `@required` ise, parametrelerin zorunlu olduğunu belirtir.

#### Reflection

Reflection, program kodunu çalışırken incelemeyi ve değiştirmeyi mümkün kılar. Ancak, Dart'ta reflection sınırlıdır ve çoğu zaman runtime refleksiyonuna sınırlı erişim sağlanır. Dart'ın reflection desteği, yalnızca sınıf isimlerini ve metotlarını dinamik olarak incelemenizi sağlar.

#### Reflection Kullanımı (Sınırlı)

Dart'ta sınıflar ve metodlar üzerinde reflection yapmak için `dart:mirrors` paketini kullanabilirsiniz. Ancak, Flutter projelerinde reflection sınırlıdır, bu yüzden genellikle bu tür kullanımlar önerilmez.

### 14.5 Reflection (Sınırlı Kullanım)

Dart'ın `dart:mirrors` paketini kullanarak sınıflar ve nesneler hakkında meta-veri elde edebilirsiniz, ancak bu paket sadece bazı platformlarda (örneğin, Dart VM üzerinde) kullanılabilir ve Flutter'da genellikle sınırlıdır.

Örnek:

```dart
import 'dart:mirrors';

class Person {
  String name;

  Person(this.name);
}

void main() {
  var person = Person("Dart");
  var mirror = reflect(person);
  var field = mirror.getField(Symbol('name'));
  print(field.reflectee);  // Dart
}
```

Bu örnekte:

- `reflect()` fonksiyonu, bir nesneyi yansıtarak, nesne hakkında meta-veri elde etmenizi sağlar.
- `getField()` fonksiyonu, nesnenin belirli bir alanını alır.

## 15. Dart ile Flutter Arasında Köprü

Flutter, Dart dilini kullanarak uygulama geliştirme için güçlü bir araçtır. Flutter'da kullanıcı arayüzü (UI) oluştururken, Dart'ın temel özelliklerinden faydalanırız. Bu bölümde, Dart ve Flutter arasındaki ilişkiyi ele alacağız.

### 15.1 Widget Yapısının Dart Temelleriyle İlişkisi

Flutter uygulamaları, temelde **widget**lerden oluşur. Widget'lar, Flutter uygulamanızdaki her görsel bileşeni tanımlar. Örneğin, metin, düğmeler, resimler ve düzenler birer widget'tır.

Dart ile Flutter arasındaki ilişki, çoğunlukla sınıf yapıları ve fonksiyonlarla şekillenir. Flutter widget'ları, Dart sınıflarını kullanarak tanımlanır ve bu sınıfların yapısı genellikle Dart dilinin temellerine dayanır.

#### Widget Yapısının Dart Sınıflarıyla Bağlantısı

Flutter'da widget'lar, çoğunlukla bir Dart sınıfı olarak tanımlanır. İki ana türde widget vardır: **StatelessWidget** ve **StatefulWidget**.

1. **StatelessWidget**: Durumsuz widget'lardır. Yani, içlerinde herhangi bir değişken durum barındırmazlar.
2. **StatefulWidget**: Durumlu widget'lardır. Yani, bu widget'lar zaman içinde değişebilecek verilere sahiptir.

Flutter'da her widget, Dart sınıfları olarak yapılandırılır. Bu nedenle, widget yapıları Dart dilindeki sınıfların mantığıyla paralellik gösterir.

---

### 15.2 `setState()` ve State Management Prensipleri

State management, Flutter uygulamalarında, widget'ların durumunun nasıl yönetileceğini ve değiştirileceğini belirleyen önemli bir konsepttir. Flutter'da `setState()` fonksiyonu, widget'ın durumunu güncellemek için kullanılır.

#### `setState()` Fonksiyonu

`setState()`, Stateful widget'larda kullanılır ve widget'ın durumunda bir değişiklik yapıldığında UI'yi yeniden oluşturur. Bu, UI'nın güncellenmesini sağlar.

Örnek:

```dart
class Counter extends StatefulWidget {
  @override
  _CounterState createState() => _CounterState();
}

class _CounterState extends State<Counter> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Counter')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('Button pressed $_counter times'),
            ElevatedButton(
              onPressed: _incrementCounter,
              child: Text('Increment'),
            ),
          ],
        ),
      ),
    );
  }
}
```

Burada:

- `_counter` değişkeni, widget'ın durumunu tutar.
- `setState()` fonksiyonu, `_counter` değerini artırarak widget'ı yeniden oluşturur.

#### State Management Prensipleri

- **Local State**: Bir widget'ın kendi durumunu yönetmesi. `setState()` bu yaklaşımı kullanır.
- **Global State**: Uygulama genelinde birden fazla widget'ın durumunu yönetme. Bunun için **Provider**, **Riverpod**, **Bloc**, **Redux** gibi paketler kullanılır.

---

### 15.3 Stateless vs Stateful Widgets

Flutter'da widget'lar iki ana kategoriye ayrılır: **StatelessWidget** ve **StatefulWidget**. Bu fark, widget'ın durumuna göre değişiklik gösterir.

#### StatelessWidget

`StatelessWidget`, herhangi bir durumu olmayan ve her zaman sabit kalan widget'lardır. UI değişmeden sabit kalır.

Örnek:

```dart
class MyStatelessWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Text('I am a StatelessWidget'),
    );
  }
}
```

- Stateless widget, yalnızca `build()` metodunu içerir ve durumu değiştiremez.

#### StatefulWidget

`StatefulWidget`, dinamik olarak değişebilen widget'lardır. Bu widget'lar, iç durumlarına göre UI'yi yeniden oluşturabilir.

Örnek:

```dart
class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}

class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int counter = 0;

  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisAlignment: MainAxisAlignment.center,
      children: <Widget>[
        Text('Counter: $counter'),
        ElevatedButton(
          onPressed: () {
            setState(() {
              counter++;
            });
          },
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

Burada:

- `StatefulWidget`, `createState()` metodu aracılığıyla bir durum sınıfı (`_MyStatefulWidgetState`) oluşturur.
- `setState()` ile durum güncellenir ve UI yeniden oluşturulur.

---

### 15.4 `build()` Fonksiyonu ve Tree Mantığı

Flutter'da her widget, bir **build()** fonksiyonu içerir. `build()` fonksiyonu, widget'ın görünümünü oluşturur ve her defasında UI'yi yeniden yapılandırmak için çağrılır.

#### Tree Mantığı (Widget Tree)

Flutter'da tüm widget'lar, bir **widget tree** (widget ağacı) oluşturur. Bu ağaç, widget'ların birbirleriyle nasıl ilişkili olduğunu gösterir. Her widget, bir üst widget'a ve alt widget'lara sahiptir. Flutter, her widget'ı ekranın belirli bir bölümüne yerleştirerek bir ağaç yapısı oluşturur.

Örnek:

```dart
class MyTreeWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Row(
          children: [
            Text('Hello'),
            Icon(Icons.star),
          ],
        ),
        Text('World'),
      ],
    );
  }
}
```

Burada:

- `Column` ve `Row` widget'ları, birbirlerini kapsayan widget'lar olarak bir ağaç yapısı oluşturur.
- `Text` ve `Icon` widget'ları, `Row` içinde alt widget'lar olarak yer alır.

---
