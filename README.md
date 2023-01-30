# Javascript Regular Expression

This matches only character hello. But only once

```
/ hello /
```

g = global. This matches characters hello. If you have many hello word in a text file /g flag will find all

```
/ hello /g
```

g = global, i = insensitive. This means /gi can find hello, Hello, heLLo, hEollo etc

```
/ hello /gi
```

[ng] = Either 'h' or 'g'. It finds hello or gello

```
/ [hg]ello /g
```

[^ab] = Match everything except a and b

```
/ [^ab]ritra /
```

## Range

'-' = Range. This means a to z.

> Ex: It could be aritra, britra, critra, xritra etc

```
/ [a-z]ritra /
```

Only first character can be small or caps. For example - aritra or Aritra

```
/ [a-zA-Z]ritra /g
```

## Repeating

'+' = This symbol means one or more than one number/character

```
/ [0-9]+ /g
```

{10} = Must be 10 characters long.

```
/ [0-9]{10} /g
```

{5,8} = Must be 5 to 8 characters long

```
/ [0-9]{5,8} /g
```

{5,} = This symbol means minimum 5 characters long

```
/ [0-9]{5,} /g
```

## Metacharacter

```
\ = escape character

\w = matches any word character (equivalent to [a-zA-Z0-9_])

\s = matches white space character

\d = matches any digit

```

First two digit then one space and then 3 characters letters/numbers. ex: 23 abc

```
\d{2}\s\w{3}
```

## Special character (sc)

```
'?' = Anything before that sc is going to be optional

   ex: 1[a-z]?  = 1 is mandatory but a to z     is optional
      ab?cd?er = b and d are optional.

'.' = Matches any character (*Only once)

   ex: ab.  If you write 'abc' then its a match

'*' = match multiple times

   ex: a[a-z]*  = ajrfgijrgijrgj = It's a match

```

## Starting and Ending

```

   / [a-z]{3} /g  = the problem with this approach is that
         ex: abc = its a match
         ex: abcdefrg = its a match because abc present in the string

   we do not want that

    /^[a-z]{3}$/g  ~  ^ = starting
                   ~  $ = ending
                   ~ abc = its a match
                   ~ abcdfr = its not a match
```

## Pipe

This means hello all or bye all or good all

```
/ (hello|bye|good) all /g
```

## Match phone number

```
   /^[0-9]{10}$/g

   /^\d{10}$/g
```

## Here is the example to match phone number,password and a custom email address using regex

```javascript
const pattern = {
  contactNumber: /^[0-9]{10}$/gi,

  password: /^[a-z\d]{4,10}[@*%&]$/g,

  // aritra@gmail.com
  // aritra@xyzp.com.co  (.co sometimes is optional )

  email: /^([a-z\d-]+)@([a-z\d]+).([a-z]{2,7}).([a-z]{2,7})?$/g,
};

function validate(input, regex) {
  let valid = regex.test(input);

  return valid;
}

// match contact number
let number = "1234567890";
let res = validate(number, pattern.contactNumber);

// match password
let password = "abcd123@#";
let res1 = validate(password, pattern.password);

// match email address
let email = "aritra@xyzp.com.co";
let res2 = validate(email, pattern.email);
```
