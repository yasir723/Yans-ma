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

1. ilk olarak gönderilen ağaç null ise null döndürür.
2. null değilse sol tarafına gitmeye devam edecek null bir düğüme ulaşana kadar
3. sonra sol tarafında sağ gitmeye başlar null bir düğüme ulaşana kadar
4. böylece sol tarafında en derin düğüme ulaşmış olur ve bu aşamada yer değiştirme işlemi başlar
5. asıl düşünce ağacı aşağıdan başlayarak yukarıya doğru her düğüm kardeşiyle değiştirmektir.
6. geçici bir değişken kullanarak düğümlerin yerlerini değiştiriyor.
7. değiştirirken değerleri değil düğümlerin yerlerini değiştirir
8. düğümlerin yer değiştirme işlemin amacı, düğümün alt düğümleriyle beraber yer değiştirmesini sağlamaktır.
9. kök düğümün sol tarafın düğümleri kardeşleriyle yer değiştirdikten sonra kökün sol düğümü, kökün sağ düğümü değiştirme işlemi yapılınca sol tarafındaki tüm düğümler sağ tarafında olur, aynı zamanda sağ tarafındaki tüm düğümler sol tarafında olur.
10. ardından kalan düğümler için 

