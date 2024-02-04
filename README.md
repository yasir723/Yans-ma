# Yansıma Problemi
Verilen bir ikili ağaçta, ağacı aynalı ağaca dönüştürme görevi vardır. İkili Ağacın aynalı hali M(T), tüm yaprak olmayan düğümlerin sol ve sağ çocuklarının yer değiştirdiği başka bir İkili Ağaçtır. Yani, her düğümün sol çocuğu sağ çocuk olur ve sağ çocuğu sol çocuk olur. Bu işlem sonucunda ağacın yansıması elde edilir

<div align="center">
    <h3>Örnek Ağaç</h3>
    <img src="https://github.com/yasir723/node-ekle/assets/111686779/a51a1c0c-1387-45ab-b199-46afd255d871" width="800">
    <br>
</div>

Bu C# sınıfı, binary ağaç veri yapısını oluşturmak için kullanılır

## `tree` Sınıfı

```csharp
class tree
{
    public int value;
    public tree right;
    public tree left;
}
```

### Özellikler

- `value`: Düğümün değerini temsil eder.
- `right`: Düğüme bağlı olan sağ alt düğümü belirtir.
- `left`: Düğüme bağlı olan sol alt düğümü belirtir.

## `mirror` Metodu
```csharp
        static tree mirror(tree node) 
        {
            if (node == null) return null;

            node.left = mirror(node.left);
            node.right = mirror(node.right);

            tree tmp = node.left;
            node.left = node.right;
            node.right = tmp;

            return node;
        }
```

## Parametreler

- `node`: Ağaçtaki mevcut düğüm.

## Dönüş Değeri

Metot, başlangıçta verilen ikili ağacın yansıması (mirror image) olarak bir ikili ağacı döndürür.

## İşleyiş

1. İlk olarak gönderilen ağaç null ise, null döndürülür.
2. Null değilse, sol tarafa gitmeye devam eder ve null bir düğüme ulaşana kadar ilerler.
3. Sonra sol tarafında sağa gitmeye başlar ve null bir düğüme ulaşana kadar devam eder.
4. Böylece sol tarafında en derin düğüme ulaşmış olur ve bu aşamada yer değiştirme işlemi başlar.
5. Asıl düşünce, ağacı aşağıdan yukarıya doğru, `her düğümü kardeşiyle yer değiştirmektir`.
6. Geçici bir değişken kullanarak düğümlerin yerlerini değiştirir.
7. Değiştirirken değerleri değil, düğümlerin yerlerini değiştirir.
8. Düğümlerin yer değiştirme işleminin amacı, düğümün alt düğümleriyle birlikte yer değiştirmesini sağlamaktır.
9. Kök düğümün sol tarafındaki düğümleri kardeşleriyle yer değiştirdikten sonra, kökün sağ tarafına gidilir ve aynı işlem yapılır.
10. Kök düğümün sağ tarafındaki düğümleri kardeşleriyle yer değiştirdikten sonra son yer değiştirme işlemine ulaşılır.
11. Son aşamada kökün sol düğümü ve sağ düğümü değiştirildiğinde, sol taraftaki tüm düğümler sağ tarafta, aynı zamanda sağ taraftaki tüm düğümler de sol tarafta olur.

<div align="center">
    <h3>Metodun çalışma adımları</h3>
</div>

[![3. durumun adlımları](https://github.com/yasir723/node-ekle/assets/111686779/334b7017-3d42-4650-91da-cc9f9210e108)](https://github.com/yasir723/node-ekle/assets/111686779/c2e70dd6-2238-420f-8b3a-ce00d2c79e2e)



