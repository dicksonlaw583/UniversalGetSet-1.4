# Universal Getter + Setter (GMS 1.4)

## Overview

This GML extension allows you to reach into deeply nested arrays and data structures in one line. It also adds the ability to use negative index numbers to count backwards from the end on arrays, lists and grids, similar to Python and Ruby.

## Examples

```
var json = '{ "a": [1, 2, { "b": 3 }]}',
    json_data = json_decode(json);
show_message(Get(json_data, "a", 2, "b")); //3
show_message(Get(json_data, "a", -2)); //2
```

```
var nested_array = array_create(3);
nested_array[0] = array_create(2, 1);
nested_array[1] = array_create(2, 4);
nested_array[2] = array_create(2, 9);
Set(nested_array, -1, 1, 16);
show_message(Get(nested_array, 2, 0)); //9
show_message(Get(nested_array, 2, 1)); //16
```

## Installation

- Download `UniversalGetSet.gmez` from the [Releases page](https://github.com/dicksonlaw583/UniversalGetSet-1.4/releases).
- In GMS 1.4, right-click on Extensions, then select Import Extension.
- Select `UniversalGetSet.gmez` and confirm.

## Functions

- `Get(array_or_ds, ...)`: Search the array or data structure recursively using the indexes in order, then return the value found there.
- `Set(array_or_ds, ..., newvalue)`: Search the array or data structure recursively using the indexes in order, then set the value there to the new value.
- `Pos(i, j)`: Return a 2-entry array containing `i` and `j` in that order. For use as a position index in a 2D array or grid.

### Position Index Format

- 1D array: Real number
- 2D array: 2-entry array of real numbers (see `Pos(x, y)`)
- Map: String
- List: Real number
- Grid: 2-entry array of real numbers (see `Pos(x, y)`)
- Stack: The special value `stack_top`
- Queue: The special value `queue_head` (note that this cannot be the last index in `Set`)
- Priority Queue: The special value `pq_min` for the minimum entry, or `pq_max` for the maximum entry (note that these cannot be the last index in `Set()`)

## Contribution Procedures

- Fork this repository.
- Open the project in GameMaker Studio 1.4 and make your additions/changes to the main GML file in the extension `UniversalGetSet`.
- Add the corresponding tests for new/changed functionality to the `UniversalGetSet_test` script group.
- Run the project to test your additions.
- Open a pull request.

## License

The 3 main scripts (`Get`, `Set`, `Pos`) are hereby released into the public domain.

The tests for the main scripts are written using [GMAssert](https://github.com/dicksonlaw583/gmassert) and [GMSugar](https://github.com/dicksonlaw583/gmsugar).
