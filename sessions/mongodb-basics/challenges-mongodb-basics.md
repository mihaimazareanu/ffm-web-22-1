# MongoDB Basics

## Exercise 1 (Create)

- Switch to a new database `neuefische`.
- Add the following document to the collection `students`:

```js
{ name: 'Sue', age: 24, points: 23, happiness: 5 }
```

- Then add these documents to the collection `students`:

```js
[
  { name: "Lucille", age: 30, points: 26, happiness: 5 },
  { name: "Gilbert", age: 45, points: 0, happiness: 1 },
  { name: "Jennie", age: 47, points: 39, happiness: 5 },
  { name: "Lydia", age: 29, points: 14, happiness: 2 },
  { name: "Agnes", age: 34, points: 39, happiness: 4 },
];
```

## Exercise 2 (Read)

- Find **one** entry from `students` with `0` `points`.
- Find **all** entries from `students` with
  1. `happiness` of `5`
  2. `age` greater than or equal to `30`.
  3. `age` greater than or equal to `30` **and** `happiness` of `5`
  4. `name` `"Agnes"`, `"Sue"` or `"Jennie"`
  5. `name` not equal to `"Lydia"`.
  6. `name` not `"Lydia"`, `"Sue"` or `"Gilbert"`.
  7. `points` not equal to `0`.
  8. `points` less than `20` **or** `happiness` less than `3`
- Count entries with more than `20` `points`

## Exercise 3 (Read)

- Find **all** entries from `students` with
  1. `happiness` greater than `2`,
     sorted by `age` in ascending order,
     limited to 2 documents
  2. `happiness` greater than `2`,
     sorted by `age` in ascending order,
     limited to 2 documents,
     with 2 skipped Documents

<div style="page-break-after: always;"></div>

## Exercise 4 (Update)

- Change **one** entry with the `name` `"Gilbert"`,
  and set the `points` to `13`.

- Change **an** entry with the `name` `"Gilbert"`,
  and increase the `happiness` by `3`.

- Change **all** entries with `happiness` less than `4`,
  and subtract `5` from `points`.

> Hint: `$inc` also supports negative numbers ;)

## Exercise 5 (Delete)

- Delete **one** entry with the `name` `"Jennie"`

- Delete **all** entries with less than `20` `points`
