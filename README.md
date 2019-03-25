# Code golfs

## Fibonacci

Currently #1 on [code-golf.io](https://code-golf.io).

- Run with `2>/dev/null`.
- Loop 31 times through `a` to `C`.
- `a-C` will appear in the output so `%d` is used to only print integers.
- The initial start value is run as a command (`1`) to set the `$_` variable.
- `$_` is then used in place of a regular variable.

```sh
1
printf %d"
" $[i+=_,_=i-_]{a..C}
```

## Fizz Buzz

Would be #1 on [code-golf.io](https://code-golf.io) if `\r` worked.

- `FizzBuzz` is used as a command to populate the `$_` variable.
- `^M` is used as a shorter alternative to `\r` or `\\r`.
- The `$_` variable which contains `FizzBuzz` is accessed by splicing the string.

**NOTE**: Literal `^M` is used in place of `Ctrl V+Ctrl Enter`.

```sh
FizzBuzz
echo ^M{1..100}^M${_::++i%3?0:4}${_:i%5?8:4}"
"
```

**Alternative attempts**

```sh
for((;i++<100;)){
FizzBuzz$i
echo ${_:i%3?i%5?8:4:0:i%15?4:8}
}
```
