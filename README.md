# Pytest Decorators

Pytest bir Python test çerçevesidir ve test fonksiyonlarını ve modüllerini yönetmek için bir dizi özellik ve decorator sağlar.
Dekoratörler, bir işlevin veya sınıfın davranışını değiştirmek için programcılara izin verdiği için Python'da oldukça güçlü ve kullanışlı bir araçtır. Dekoratörler, bir işlevin davranışını kalıcı olarak değiştirmeden genişletmek için başka bir işlevi sarmamıza olanak tanır. 

## Kullanım

 **@pytest.fixture**

`@pytest.fixture` dekoratörü, bir test fonksiyonuna veya bir başka fixture'a bağımlılık oluşturan bir işlevi belirtmek için kullanılır. Fixtures, test fonksiyonları arasında paylaşılan durumları sağlamak için kullanılır. Örnek kullanım:

   
    import pytest
    
    @pytest.fixture
    def my_fixture():
        data = "Bu bir örnek veridir"
        return data
    
    def test_example(my_fixture):
        assert my_fixture == "Bu bir örnek veridir" 

**@pytest.mark.parametrize**

Parametreli testler, geliştiricinin aynı testi farklı değerler üzerinde tekrar tekrar çalıştırmasını sağlar. `@pytest.mark.parametrize` dekoratörü, aynı testi farklı parametrelerle çalıştırmak için kullanılır. Örnek kullanım:

    import pytest
    
    @pytest.mark.parametrize("input, expected_output", [
        (1, 2),
        (5, 10),
        (10, 20)
    ])
    def test_multiply_by_two(input, expected_output):
        assert input * 2 == expected_output



**@pytest.mark.skip**  ve **@pytest.mark.skipif**

Bu dekoratörler, bir testi atlamak, koşullu olarak atlamak veya geçici olarak devre dışı bırakmak için kullanılır. Örnek kullanım:

    import pytest
    
    @pytest.mark.skip(reason="Bu test henüz hazır değil")
    def test_incomplete_function():
        # Test içeriği
        pass



Python sürümüne bağlı olarak bir testin atlanması gerektiğinde `@pytest.mark.skipif` kullanılabilir:

    import pytest
    import sys
    
    @pytest.mark.skipif(sys.version_info < (3, 6), reason="Python 3.6'dan önce çalışmaz")
    def test_functionality():
        # Test kodu buraya yazılır
        assert True

Bu örnek, `sys.version_info` kullanarak Python sürümünü kontrol eder. Eğer Python sürümü 3.6'dan küçükse, `test_functionality` fonksiyonu çalıştırılmaz ve atlanır.


**@pytest.mark.xfail** 

Pytest içinde kullanılan bir işaretleyicidir ve "başarısız olması beklenen test" anlamına gelir. Bu işaretleyici, bir testin bilerek veya geçici bir süre için başarısız olmasını beklediğiniz durumlarda kullanılır.

Bu işaretleyici, testin başarısız olması durumunda testin hala çalışmasını ve sonucun rapor edilmesini sağlar, ancak bu başarısızlığın bir hata olarak değil, beklenen bir durum olarak işaretlenmesini sağlar.

    import pytest
    
    @pytest.mark.xfail
    def test_something():
        assert False  # Bu test bilerek başarısız olacak şekilde yapılmıştır

