# C structure and JSON fast interchange library (English version)

---

## struct2json

[struct2json](https://github.com/armink/struct2json) Is an open source C structure with JSON fast interchange library，which can quickly implement the serialization between **structure objects** and **JSON objects** and deserialization requirements. Fast, simple API design, greatly reducing the use of JSON parsing library to achieve the functionality of such code complexity.

## Origin

把面向对象设计应用到C语言中，是当下很流行的设计思想。由于C语言中没有类，所以一般使用结构体 `struct` 充当类，那么结构体变量就是对象。有了对象之后，很多时候需要考虑对象的序列化及反序列化问题。C语言不像很多高级语言拥有反射等机制，使得对象序列化及反序列化被原生的支持。

对于C语言来说，序列化为 JSON 字符串是个不错的选择，所以就得使用 [cJSON](https://github.com/kbranigan/cJSON) 这类 JSON 解析库，但是使用后的代码冗余且逻辑性差，所以萌生对cJSON库进行二次封装，实现一个 struct 与 JSON 之间快速互转的库。 struct2json 就诞生于此。下面是 struct2json 主要使用场景：

- **Persistence** ：结构体对象序列化为 JSON 对象后，可直接保存至文件、Flash，实现对结构体对象的掉电存储；
- **Communication** ：High-level language is very friendly to JSON support, for example: Javascript、Groovy module JSON with native support，and so JSON can also be used as communication protocol format and object delivery format of C language and other programming languages;
- **Visualization** ：After serializing the object into JSON, you can more intuitive display to the console or UI, it can be used for product debugging, product development and other secondary scenes;

## How to use

### Declaring the structure

Declare the two structures as follows, the structure `Hometown` is the substructure of the structure `Student`

```C
/* Hometown */
typedef struct {
    char name[16];
} Hometown;

/* Student */
typedef struct {
    uint8_t id;
    uint8_t score[8];
    char name[10];
    double weight;
    Hometown hometown;
} Student;
```

### Serialize the structure object into a JSON object

|Before use（[Code Source](https://github.com/armink/struct2json/blob/master/docs/zh/assets/not_use_struct2json.c)）|After use（[Code Source](https://github.com/armink/struct2json/blob/master/docs/zh/assets/used_struct2json.c)）|
|:-----:|:-----:|
|![Structure to JSON (before use)](https://git.oschina.net/Armink/struct2json/raw/master/docs/zh/images/not_use_struct2json.png)| ![结构体转JSON-使用后](https://git.oschina.net/Armink/struct2json/raw/master/docs/zh/images/used_struct2json.png)|

### The JSON object is deserialized into a structure object

|Before use（[Code Source](https://github.com/armink/struct2json/blob/master/docs/zh/assets/not_use_struct2json_for_json.c)）|After use（[Code Source](https://github.com/armink/struct2json/blob/master/docs/zh/assets/used_struct2json_for_json.c)）|
|:-----:|:-----:|
|![JSON转结构体-使用前](https://git.oschina.net/Armink/struct2json/raw/master/docs/zh/images/not_use_struct2json_for_json.png)| ![JSON转结构体-使用后](https://git.oschina.net/Armink/struct2json/raw/master/docs/zh/images/used_struct2json_for_json.png)|

Welcome everybody **fork and pull request**([Github](https://github.com/armink/struct2json)|[OSChina](http://git.oschina.net/armink/struct2json)|[Coding](https://coding.net/u/armink/p/struct2json/git)). If you think this open source project is great，click on the **Star**，at the upper right corner and recommend it to friends in need.

## Documentation

Specific content reference[`\docs\zh\`](https://github.com/armink/struct2json/tree/master/docs/zh)Under the file. Make sure to **read the documentation** and then use it.

## License

MIT Copyright (c) armink.ztl@gmail.com
