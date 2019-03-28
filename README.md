# Code golfs

All of the below code snippets are MIT licensed and written solely by myself. These solutions will no longer be published on any code golfing websites as they are not credible regarding copycats and stolen code.

## Leap Years

Print all leap years between `1800` and `2400`.

- Set `$@` to all years between `1800` and `2400` which are divisible by `4`.
- Remove all years divisible by `100` which aren't `2000` and `2400`.
- Print using `history -p` which prints arguments line by line.

```sh
set {1804..2400..4}
history -p ${@%?[^04]00}
```

## Fibonacci

Print the Fibonacci sequence up to `31`.

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

Print Fizz Buzz up to 100.

- Run with `2>/dev/null`.
- Loop over `1-100`
- Run `FizzBuzz$i` as a command to populate `$_`.
- Use a string splice to output the portion of the string needed.

```sh
for((;i++<100;)){
FizzBuzz$i
echo ${_:i%3?i%5?8:4:0:i%15?4:8}
}
```
