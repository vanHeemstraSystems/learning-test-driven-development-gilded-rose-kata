# 100 - Initial unit test

The initial unit test (here: ```test_foo```) of the Gilded Rose Kata had been provided upfront:

```
...
    def test_foo(self):
       items = [Item("foo", 0, 0)]
       gilded_rose = GildedRose(items)
       gilded_rose.update_quality()
       self.assertEqual("foo", items[0].name) # changed "foo" to "fixme" to fix the test
...
```
python/tests/test_gilded_rose.py

We can see the structure of such a unit test.

This (```test_foo```) is a **method** within the ```GildedRoseTest``` class that inherits from ```unittest.TestCase```. The method starts with ```def``` (for definition) followed by the method name (here: ```test_foo```). The ```self``` parameter refers to the **instance** of the test class, allowing the method to access other methods and attributes of the test class. The method ends with a colon (```:```).

The test follows the **Arrange-Act-Assert** pattern:
- **Arrange**: Creates test data (```items = [Item("foo", 0, 0)]```)
- **Act**: Performs the action being tested (```gilded_rose.update_quality()```)
- **Assert**: Verifies the expected outcome (```self.assertEqual("foo", items[0].name)```)

This unit test verifies that the item name remains unchanged after calling the ```update_quality()``` method. The assertion ```self.assertEqual("foo", items[0].name)``` confirms that the item name stays as "foo" - it should **not** be modified by the ```update_quality()``` method. This is an important business rule: item names in the Gilded Rose system should remain constant regardless of quality updates.

Now to cover more of the requirements set by the Gilded Rose Kata, we will create additional unit tests in the next section.