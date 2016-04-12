# sizeof(data)
A listing of how much space data types occupy in memory for different programming languages.
Feel free to add to this, via pull request.

## Overview Table
In bits

| Language | Boolean | Char | Short | Int | Long | Float | Double | Array of Ints | Array of Reals |
| --- | --- | --- | --- |
| C       | 1 | 8 | 16 | 32 | 64 | 32 | 64 | 32*n* | 32*n* |
| Julia   | 8 | 8 | 16 | 32 | 64 | 32 | 64 | 64*n* | 64*n*
| Perl5   | 192 | - | - | - | 192 | - | 192 | 512 + 64*n* | 512 + 64*n* |
| Python2 | 192 | - | - | - | 192 | - | 192 | 576 + 64*n* | 576 + 64*n* |
| Python3 | 224 | - | - | - | 224 | - | 192 | 512 + 64*n* | 512 + 64*n* |


## C
Some data types in C can [vary](https://en.wikipedia.org/wiki/C_data_types) by platform, especially [integral data types][].
Nonetheless, they are fairly transparent, so you can enter the data type directly within `sizeof()`.  But for uniformity with other languages, data literals are also used below.

### x86-64, GCC
```
/* gcc -std=c99 -o sizeof sizeof.c */
#include <stdbool.h>
#include <stdio.h>
int main(int argc, char **argv) {
    printf("sizeof(bool) = %zd\n", sizeof(bool));
    printf("sizeof(true) = %zd\n", sizeof(true));
    printf("sizeof(1) = %zd\n", sizeof(1));
    printf("sizeof(char) = %zd\n", sizeof(char));
    printf("sizeof('a') = %zd\n", sizeof('a'));
    printf("sizeof(short) = %zd\n", sizeof(short));
    printf("sizeof(int) = %zd\n", sizeof(int));
    printf("sizeof(long) = %zd\n", sizeof(long));
    printf("sizeof(long long) = %zd\n", sizeof(long long));
    printf("sizeof(1.0) = %zd\n", sizeof(1.0));
    printf("sizeof(float) = %zd\n", sizeof(float));
    printf("sizeof(double) = %zd\n", sizeof(double));
    printf("sizeof("") = %zd\n", sizeof(""));
    printf("sizeof(\"a\") = %zd\n", sizeof("a"));
    printf("sizeof(\"ab\") = %zd\n", sizeof("ab"));
    printf("sizeof(\"abc\") = %zd\n", sizeof("abc"));
}
```

## [Julia](https://en.wikibooks.org/wiki/Introducing_Julia/Types)
```
sizeof(Bool)
sizeof(Int)
sizeof(1)
sizeof(Int8)
sizeof(Int16)
sizeof(Int32)
sizeof(Int64)
sizeof(Float16)
sizeof(Float32)
sizeof(Float64)
sizeof(1.0)
sizeof(Int[1 2 3 4])
sizeof(Float32[1.0 2.0 3.0 4.0])
sizeof("")
sizeof("a")
sizeof("ab")
sizeof("abc")
```

## Perl 5

`sudo apt-get install libdevel-size-perl`

```
use strict;
use Devel::Size qw(size total_size);
print(size(1) . "\n");
print(size(1.0) . "\n");
print(size([]) . "\n");
print(size([1]) . "\n");
print(size([1,1]) . "\n");
print(size([1,1,1]) . "\n");
print(size([1.0]) . "\n");
print(size([1.0,1.0]) . "\n");
print(size([1.0,1.0,1.0]) . "\n");
print(size('a') . "\n");
print(size("") . "\n");
print(size("a") . "\n");
print(size("ab") . "\n");
print(size("abc") . "\n");
```

## Python
```
import sys
sys.getsizeof(True)
sys.getsizeof(1)
sys.getsizeof(1.0)
sys.getsizeof([])
sys.getsizeof([1])
sys.getsizeof([1,1])
sys.getsizeof([1,1,1])
sys.getsizeof([1.0])
sys.getsizeof([1.0,1.0])
sys.getsizeof([1.0,1.0,1.0])
sys.getsizeof('')
sys.getsizeof('a')
sys.getsizeof('ab')
sys.getsizeof('abc')
```

## Swift

```
sizeof(Bool)
sizeof(Int)
sizeof(Int16)
sizeof(Int32)
sizeof(Int64)
sizeof(Float)
sizeof(Double)
```


[integral data types]: https://en.wikipedia.org/wiki/Integer_(computer_science)
