# Pytest Decorators

Bu depo, Pytest kütüphanesinde kullanılan dekoratörlerin örnekleri ve kullanımlarıyla ilgili örnekler içerir.

## Kullanım

### @pytest.fixture

`@pytest.fixture` dekoratörü, test fonksiyonları arasında paylaşılan durumları sağlamak için kullanılır. Örnek kullanım:

```python
import pytest

@pytest.fixture
def my_fixture():
    data = "Bu bir örnek veridir"
    return data

def test_example(my_fixture):
    assert my_fixture == "Bu bir örnek veridir"

#@pytest.mark.parametrize
@pytest.mark.parametrize dekoratörü, aynı testi farklı parametrelerle çalıştırmak için kullanılır. Örnek kullanım:

import pytest

@pytest.mark.parametrize("input, expected_output", [
    (1, 2),
    (5, 10),
    (10, 20)
])
def test_multiply_by_two(input, expected_output):
    assert input * 2 == expected_output


#@pytest.mark.skip
@pytest.mark.skip dekoratörü, bir testi atlamak veya geçici olarak devre dışı bırakmak için kullanılır. Örnek kullanım:

import pytest

@pytest.mark.skip(reason="Bu test henüz hazır değil")
def test_incomplete_function():
    # Test içeriği
    pass

