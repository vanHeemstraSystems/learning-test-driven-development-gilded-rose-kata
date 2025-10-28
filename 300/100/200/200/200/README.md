# 200 - Additional unit tests

First of all, create Unit Tests automatically following the instructions given in [How to test legacy code with characterization tests (JavaScript)](https://www.youtube.com/watch?v=2q5PdGdlL8Y). 

Based on the requirements set by the Gilded Rose Kata we will create a unit test for each of those.

The requirements are:

## 100 - Basic System Rules

- All `items` have a `SellIn` value which denotes the number of days we have to sell the `items`
- All `items` have a `Quality` value which denotes how valuable the item is
- At the end of each day our system lowers both values for every item

See [README.md](./100/README.md)

## 200 - Quality Degradation Rules

- Once the sell by date has passed, `Quality` degrades twice as fast
- The `Quality` of an item is never negative
- The `Quality` of an item is never more than `50`

See [README.md](./200/README.md)

## 300 - Special Items

- **"Aged Brie"** actually increases in `Quality` the older it gets
- **"Sulfuras"**, being a legendary item, never has to be sold or decreases in `Quality` (Quality is `80` and never alters)
- **"Backstage passes"**, like aged brie, increases in `Quality` as its `SellIn` value approaches:
  - `Quality` increases by `2` when there are `10` days or less
  - `Quality` increases by `3` when there are `5` days or less
  - `Quality` drops to `0` after the concert

See [README.md](./300/README.md)

## 400 - New Feature Requirements

- **"Conjured"** items degrade in `Quality` twice as fast as normal items

See [README.md](./400/README.md)