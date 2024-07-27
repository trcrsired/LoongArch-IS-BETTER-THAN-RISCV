# LoongArch-IS-BETTER-THAN-RISCV
This is an example showing you why RISCV is bad and LoongArch is good

```cpp
using uint_least64_t = __UINT_LEAST64_TYPE__;

uint_least64_t testbswap(uint_least64_t a) noexcept
{
    return __builtin_bswap64(a);
}

template<typename T>
constexpr T my_rotr(T a, int x) noexcept
{
    constexpr int bits{sizeof(uint_least64_t)*__CHAR_BIT__};
    return (a>>x)|(a<<(bits-x));
}

uint_least64_t testrotr(uint_least64_t a) noexcept
{
    return my_rotr(a,10);
}
```

LoongArch

clang: [https://godbolt.org/z/xv3brnzvc](godbolt)
gcc (I guess gcc has some bugs here but still good enough to show the issue): [https://godbolt.org/z/bYvq7b8cs](godbolt)

RISC-V

clang: [https://godbolt.org/z/x774GvMx4](godbolt)
gcc: [https://godbolt.org/z/hTj9c3r63](godbolt)
