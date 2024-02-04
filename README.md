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

