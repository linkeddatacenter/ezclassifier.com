---
title: Training file
menu: {main: {weight: 30}}
weight: 4
---

To train your model you need a CSV file containing an example for each row.

Each example can contain a set of fields, some mandatory some optional. The index, staring from 0, of the fields in the record can be communicated to EZClassifier [model train command](http://localhost:1313/docs/reference/#command-model-train) with a set of command options

If the index of the fileld doe not exists in the record or the field format is not a valid value, the default value is used:

| field name | field description | required | type | default value | default |
| ---------- | ----------------- | -------- | ---- | ------------- | ------- |
| prototype  | a text that exemplifies a typical element in the category specified in the second field | YES | String | N.A. | --prototype-index=0 |
| class | a short text that represent a category name | YES | String | N.A. | --class-index=1 | 
| weight | a multiplicative factor for predicted similarity  | NO | positive real number | 1.0 | --weight-index=2 | 
| bias | a additive value factor for predicted similarity  | NO | real number | 0.0 | --bias-index=2 | 

If an  header raw is present, please do not forget to use the `--header` option in `model train` command


Here is an example of a model trainig file to find strings about cats:

```csv
prototype, class, weight, bias
"Persian Cat: Known for their long, luxurious fur and sweet temperament, Persian cats are one of the most popular breeds", cat
"siamese animal", cat, 0.8
"from siam", cat, 0.8, -0.5
```

In this example:
- the first row is the header (to be discarded using -H option during model training)
- the second row assumes a weight = 1.0 and a bias = 0.0
- the third row assumes a weight = 8.8 and a bias = 0.0
- the fourth row assumes a weight = 8.8 and a bias = -0.5
