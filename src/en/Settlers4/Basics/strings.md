# String Handling
Settlers 4 uses the `std::wstring` class from the C++ Standard Library to handle strings.

This means it's structure looks more or less like this:
```cpp
struct wstring
{
    union {
      __int16 *text;
      __int16 buffer[8];
    } storage; // (1)
    int size;
    int capacity;
};
```

1. See [this blog post](https://devblogs.microsoft.com/oldnewthing/20230803-00/?p=108532)<br/>
   In short: Small strings (up to 7 characters) are stored directly in the `wstring` object, longer strings are allocated on the heap and the `text` pointer points to that memory.

Main problem is, that the compiler rather aggressively inlined a lot of string functions, especially the check whether a string is small or not.
This means that you will often find code like this:
```cpp
wstring *dest;
if ( src->capacity < 8u )
    dest = src;
else
    dest = (wstring *)src->storage.text;
```
