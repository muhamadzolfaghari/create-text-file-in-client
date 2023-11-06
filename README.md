# create-text-file-in-client
A simple way to create text file in client side

Data as a csv file which each cell is separated by comma and row by newline.
```js
const data = "id,title,price\n10,toyota,900";
```

Data is passed as blobParts and type determined as a sample text format

```js
const blob = new Blob([data], { type: "text/plain" });
```

A temporary resource is created in memory and accessed by its url.
```js
const createdObjectUrl = URL.createObjectURL(blob);
```

A sample link is created by an anchor html tag.
```js
const link = document.createElement("a");
link.href = createdObjectUrl;
```


download property when file downloading determine the filename
```js
link.download = "cars.csv";
```

Download is started by click on temporary anchor tag
```js
link.click();
```

To avoid memory leaks, created source and link must be deleted

```js
link.remove();
URL.revokeObjectURL(createdObjectUrl);
```
