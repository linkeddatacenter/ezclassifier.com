---
title: Getting Started
description: What you need to know to use EZClassifier
weight: 2
---

Data classification is the process of organizing and categorizing data based on specific criteria or attributes. 
It helps make data more structured, accessible, and understandable. 


## HW & SW Prerequisites
To run EZClassifier you need any computer with Java Runtime Environment installed (JRE). You can download for free the JRE from the [official Java site](https://www.java.com/download/)

Than you need to [download the ezc.jar file](/download/ezc.jar)

Last, you need an API Key that enables the services [see prices](/docs/prices). POC plans are [available on requests](/about).


## Try it out!

{{% alert title="sampe data" color="info" %}}
Here are some sample data:
- [examples file](/usecase/sample/examples.csv)
- [data do be classified](/usecase/sample/data.csv).
- [resultfile](/usecase/sample/out.csv)
{{% /alert %}}

Create a new model:
```
java -jar "path-to/ezc.jar" model -k "your-api-key-here" -i examples.csv 
```

This command will generate the file model.tc containing the learned model

Classify your data using the created model:
```
java -jar "path-to-/ezc.jar" classify -k "your-api-key-here" -H -i data.csv
```

This command will generate the results in the file out.csv




## How it works?
You'll require a CSV file containing a list of examples. In this file, each example corresponds to a row and comprises two fields: 'prototype' and 'class'. Optionally, you can include a 'weight' field, which ranges from 0 to 1 (default value is 0.5). 

The "prototype" is a string (quote it if needed) that exemplifies a typical element in the category specified in the second field ("class"). 

You can add as many examples an categories you want. You can optionally add to  each field coupe a third field that suggests to the algorithm your confidence in the provided example classification. For example:

| prototype                                                                                                                                             | class |
|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------|
| Persian Cat: Known for their long, luxurious fur and sweet temperament, Persian cats are one of the most popular breeds                               | cat   |
| Maine Coon: These are among the largest domestic cat breeds. They have tufted ears, a bushy tail, and a friendly, gentle personality                  | cat   |
| Siamese Cat: Siamese cats are known for their striking blue almond-shaped eyes, short coat, and vocal nature                                          | cat   |
| Ragdoll Cat: Ragdolls are large, affectionate cats known for their tendency to go limp when you hold them, hence the name Ragdoll                     | cat   |
| German Shepherd: Intelligent and versatile, often used in police and military work                                                                    | dog   |
| Rottweiler: Strong and loyal, originally bred for herding and guarding                                                                                | dog   |
| Siberian Husky: Known for their endurance and striking appearance, used as sled dogs                                                                  | dog   |
| Doberman Pinscher: Agile and protective, often used as guard dogs                                                                                     | dog   |
| Meryl Streep: Known for her incredible talent and versatility, Meryl Streep is one of the most acclaimed and decorated actresses in Hollywood history | actor |
| Leonardo DiCaprio: Leonardo DiCaprio is a highly respected actor who has starred in a wide range of critically acclaimed films                        | actor |
| Viola Davis: Viola Davis is a talented actress known for her powerful performances                                                                    | actor |


EZClassifier accepts till 1000 examples.


Than you can provide a set of data to classify according the provided example. For instance:

| data                                                                                                                                    |
|-----------------------------------------------------------------------------------------------------------------------------------------|
| Bengal Cat: Bengal cats have a wild appearance with rosette-shaped spots on their coat, reminiscent of a leopard.                       |
| Scottish Fold: Scottish Fold cats are recognized by their unique folded ears, which give them an endearing appearance.                  |
| Sphynx Cat: Sphynx cats are a hairless breed with wrinkled skin.                                                                        |
| Shovel: A shovel is a tool with a flat, wide blade and a long handle, used for digging, lifting, and moving soil, gravel, or materials. |
| Garden Fork: A garden fork has sturdy tines and a handle, used for loosening soil, breaking up clumps, and mixing in compost.           |
| Denzel Washington: Denzel Washington is an iconic American actor with a commanding presence on screen.                                  |
| Cate Blanchett: Cate Blanchett is an Australian actress known for her elegance and versatility.                                         |
| British Shorthair: British Shorthairs are known for their dense, plush coat and round faces.                                            |
| Russian Blue: Russian Blue cats have a distinctive bluish-gray coat and striking green eyes.                                            |
| Abyssinian: Abyssinian cats are active and playful with a short, ticked coat.                                                           |
| Rake: Rakes have curved or straight teeth attached to a handle and are used for leveling soil, removing debris, and spreading mulc      |
| Poodle: Poodles are highly intelligent and come in different sizes: Standard, Miniature, and Toy.                                       |
| Dachshund: Dachshunds, or wiener dogs, are known for their long bodies and short legs.                                                  |
| Yorkshire Terrier: Yorkies are small but spirited dogs with long, silky hair                                                            |
| Boxer: Boxers are medium to large dogs with strong, muscular bodies.                                                                    |
| Denzel Washington: Denzel Washington is an iconic American actor with a commanding presence on screen.                                  |
| Cate Blanchett: Cate Blanchett is an Australian actress known for her elegance and versatility.                                         |
| Tom Hanks: Tom Hanks is a beloved American actor known for his likable and relatable on-screen persona.                                 |
| Siberian Husky: Huskies are known for their striking appearance, with a thick double coat and blue or multicolored eyes.                |
| British Shorthair: British Shorthairs are known for their dense, plush coat and round faces.                                            |
| Russian Blue: Russian Blue cats have a distinctive bluish-gray coat and striking green eyes.                                            |
| Hoe: A hoe has a flat, blade-like head and a long handle, used for weeding, cultivating, and breaking up soil.                          |
| Pruning Shears: Prunin                                                                                                                  | 

On success EZClassifier will create a table with two additional fields:


| data | class | similarity |
| --- | --- | --- |
| Bengal Cat: Bengal cats have a wild appearance with rosette-shaped spots on their coat, reminiscent of a leopard. | cat | 0.864848 |
| Scottish Fold: Scottish Fold cats are recognized by their unique folded ears, which give them an endearing appearance. | cat | 0.858967 |
| Sphynx Cat: Sphynx cats are a hairless breed with wrinkled skin. | cat | 0.858745 |
| Shovel: A shovel is a tool with a flat, wide blade and a long handle, used for digging, lifting, and moving soil, gravel, or materials. | OTHER | 0.760553 |
| Garden Fork: A garden fork has sturdy tines and a handle, used for loosening soil, breaking up clumps, and mixing in compost. | OTHER | 0.764859 |
| Denzel Washington: Denzel Washington is an iconic American actor with a commanding presence on screen. | actor | 0.855533 |
| Cate Blanchett: Cate Blanchett is an Australian actress known for her elegance and versatility. | actor | 0.876928 |
| British Shorthair: British Shorthairs are known for their dense, plush coat and round faces. | cat | 0.878253 |
| Russian Blue: Russian Blue cats have a distinctive bluish-gray coat and striking green eyes. | cat | 0.891379 |
| Abyssinian: Abyssinian cats are active and playful with a short, ticked coat. | cat | 0.865725 |
| Rake: Rakes have curved or straight teeth attached to a handle and are used for leveling soil, removing debris, and spreading mulc | OTHER | 0.755273 |
| Poodle: Poodles are highly intelligent and come in different sizes: Standard, Miniature, and Toy. | dog | 0.843957 |
| Dachshund: Dachshunds, or wiener dogs, are known for their long bodies and short legs. | dog | 0.845551 |
| Yorkshire Terrier: Yorkies are small but spirited dogs with long, silky hair | dog | 0.853720 |
| Boxer: Boxers are medium to large dogs with strong, muscular bodies. | dog | 0.860509 |
| Denzel Washington: Denzel Washington is an iconic American actor with a commanding presence on screen. | actor | 0.855477 |
| Cate Blanchett: Cate Blanchett is an Australian actress known for her elegance and versatility. | actor | 0.876928 |
| Tom Hanks: Tom Hanks is a beloved American actor known for his likable and relatable on-screen persona. | actor | 0.841147 |
| Siberian Husky: Huskies are known for their striking appearance, with a thick double coat and blue or multicolored eyes. | dog | 0.931415 |
| British Shorthair: British Shorthairs are known for their dense, plush coat and round faces. | cat | 0.878175 |
| Russian Blue: Russian Blue cats have a distinctive bluish-gray coat and striking green eyes. | cat | 0.891341 |
| Hoe: A hoe has a flat, blade-like head and a long handle, used for weeding, cultivating, and breaking up soil. | OTHER | 0.760036 |
| Pruning Shears: Prunin | OTHER | 0.781802 |

Elements with a confidence less than 0.8 (configurable) will be assigned to the "OTHER" category
