# Code golfs

All of the below code snippets are MIT licensed and written solely by myself. These solutions will no longer be published on any code golfing websites as they are not credible regarding copycats and stolen code.


## Table of Contents

<!-- vim-markdown-toc GFM -->

* [Leap Years (44 bytes)](#leap-years-44-bytes)
* [Fibonacci (34 bytes)](#fibonacci-34-bytes)
* [Fizz Buzz (63 bytes)](#fizz-buzz-63-bytes)
* [Niven/Harshad Numbers (45 bytes)](#nivenharshad-numbers-45-bytes)
* [Prime Numbers (55 bytes)](#prime-numbers-55-bytes)

<!-- vim-markdown-toc -->


## Leap Years (44 bytes)

Print all leap years between `1800` and `2400`.

- Set `$@` to all years between `1800` and `2400` which are divisible by `4`.
- Remove all years divisible by `100` which aren't `2000` and `2400`.
- Print using `history -p` which prints arguments line by line.

```sh
set {1804..2400..4}
history -p ${@%?[^04]00}
```

## Fibonacci (34 bytes)

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

## Fizz Buzz (63 bytes)

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

## Niven/Harshad Numbers (45 bytes)

Print Niven/Harshad up to 100.

```sh
for((;i++<100;)){((i%(i%10+i/10)))||echo $i;}
```

## Prime Numbers (55 bytes)

Print prime numbers up to 100.

- Loop over `1` to `97`.
- Abuse brace expansion to check divisors.
- Abuse `let`.
- ...

```sh
for((;i++<97;)){
k= let k+=i%{1..97}?0:1 k^2||echo $i
}
```
