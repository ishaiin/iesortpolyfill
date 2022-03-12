# iesortpolyfill

In ie, the javascript function sort solves what is different from chrome.

```
With dataset '[A,B,C,D]' Chrome and FF sort with by the combinations (A,B)(B,C)(C,D) for me IE 11 is comparing the items as (B,A)(C,B)(D,C)
```

for example

```javascript
var data = [
  { day: "20220301", idx: "b" },
  { day: "20220301", idx: "a" },
  { day: "20220304", idx: "e" },
  { day: "20220304", idx: "f" },
  { day: "20220307", idx: "g" },
  { day: "20220307", idx: "h" },
  { day: "20220302", idx: "d" },
  { day: "20220302", idx: "c" },
];

var sort = data.sort(function (a, b) {
  console.log(a);
  console.log(b);
  //   In ie and chrome, a and b are different.
  return a.day - b.day;
});
```

then use Array idx

```javascript
var sort = arr.sort(function (a, b) {
  // ie11 fix
  var aVal = arr.indexOf(a) > arr.indexOf(b) ? a : b;
  var bVal = arr.indexOf(a) > arr.indexOf(b) ? b : a;

  if (aVal.day === bVal.day) {
    // then ie value === chrome value
  }

  return aVal.day - bVal.day;
});
```
