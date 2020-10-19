# siwon

![repo-size badge](https://img.shields.io/github/repo-size/jdeokkim/siwon)
![license badge](https://img.shields.io/github/license/jdeokkim/siwon)

A single-header library for handling [CP949](https://en.wikipedia.org/wiki/Unified_Hangul_Code) (EUC-KR) strings.

## Examples

```c
#include <stdio.h>
#include "siwon.h"

int main(void) {
    const char *str = "string-文字列-문자열";
    const char *str_u8 = _U8("안녕하세요!");

    printf("`cp949_char_at(str, 4)` -> %s\n", cp949_char_at(str, 4));
    printf("`cp949_check_locale()` -> %s\n", cp949_check_locale() ? "true" : "false");
    printf("`cp949_hamming_dist(\"스마트폰\", \"스타트업\")` -> %d\n", cp949_hamming_dist("스마트폰", "스타트업"));
    printf("`cp949_next_codepoint(str, NULL)` -> %s\n", cp949_next_codepoint(str, NULL));
    printf("`cp949_strlen(str)` -> %d\n", cp949_strlen(str));
    printf("`cp949_substr(str, 1, 8)` -> %s\n", cp949_substr(str, 1, 8));
    printf("`cp949_to_uc(\"가\")` -> %d\n", cp949_to_uc("가"));
    printf("`cp949_valid_codepoint(str)` -> %d\n\n", cp949_valid_codepoint(str));

    printf("`_U8()` macro demo: ");

    while (*str_u8)
        printf("\\x%02X", *(str_u8++) & 0xff);

    return 0;
}
```

```
`cp949_char_at(str, 4)` -> n
`cp949_check_locale()` -> true
`cp949_hamming_dist("스마트폰", "스타트업")` -> 2
`cp949_next_codepoint(str, NULL)` -> s
`cp949_strlen(str)` -> 14
`cp949_substr(str, 1, 8)` -> tring-文字
`cp949_to_uc("가")` -> 44032
`cp949_valid_codepoint(str)` -> 1

`_U8()` macro demo: \xEC\x95\x88\xEB\x85\x95\xED\x95\x98\xEC\x84\xB8\xEC\x9A\x94\x21
```

## License

MIT License
