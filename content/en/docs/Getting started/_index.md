---
title: Getting Started
description: What you need to know to use EZClassifier
weight: 2
---

Data classification is the process of organizing and categorizing data based on specific criteria or attributes. 
It helps make data more structured, accessible, and understandable. 

## Let's see an example
Suppose you need to categorize a set of texts that contain mixed references to cats, actors, dogs, and other things that don't matter.

You will need a CSV file containing a few examples. In this file, each example corresponds to a row that provides two fields: 
- **prototype**: a text that exemplifies a typical element in the category specified in the second field
- **class**: a short text that represent a category name

These examples are used by EZClassifier to create a personalized model. You can add to the model as many prototypes and categories as you like, as long as there is at least one example for each category. EZClassifier works with any language, even when used simultaneously in the same text or the same data file and/or examples.

Once you created your model, you use it to classify your data. 
EZClassifier will create a table adding two additional fields to your data:
- **class**: that is the predicted category for the described row
- **similarity**: a number from 0 to 1 that represents the confidence of EZClassifier about its classification (1=maxumum confidence , 0=no confidence).
  


{{< tabpane text=true >}}
{{% tab header="model examples"  %}}

Here are some examples you can use to train your model:

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


{{% /tab %}}
{{% tab header="input data"  %}}

Here are the data you want to classify:

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

{{% /tab %}}
{{% tab header="classified data"  %}}

Here are some results. Note that elements with a confidence less than 0.84 (configurable) are assigned to the "OTHER" category:

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

{{% /tab %}}
{{< /tabpane >}}

## Try it out!

### HW & SW Prerequisites
To run EZClassifier, you need any computer with Java 17+ installed. You can download the Java 17+ for  your architecture (Linux, macOS, Windows) from the [the official Java site](https://www.oracle.com/java/technologies/downloads/#java17).

### Install EZClassifier
Next, [download the latest version of the EZC JAR file](/download/ezc.jar) to  a directory of your choice.

Lastly, you'll need an API Key to enable the services ([see prices here](/docs/prices)). Proof of Concept (POC) and free plans are [available upon request](/about).

Create shortcut for launching the java command and set the TC_API_KEY environment with your api key:

For example, with bash, open a terminal and type:
```
export TC_API_KEY=HERE-IS-YOUR-API-KEY
alias ezc='java -jar ezc.jar' 
```

For example, in windows open a terminal windows (CMD) and type:
```
set TC_API_KEY=HERE-IS-YOUR-API-KEY
doskey ezc=java -jar "%USERPROFILE%\Downloads\ezc.jar" $*
```

Test that the system is working:
```
java --version
# be sure it reports a java version > 17 
ezc --version
```


### Run the example in two simple steps

{{% alert title="sampe data" color="info" %}}
Here you can download some sample data:
- [examples file](/tutorial1-data/examples.csv): some examples about cat, dog, and actor descriptions
- [data to be classified](/tutorial1-data/input-data.csv): some strings to classify
{{% /alert %}}

#### Step 1: create a model
Create a new model from your examples:

```
ezc model -n mymodel -H -i examples.csv -t 0.84
```

To list all the available models you can use `ezc model ls`

#### Step 2: classify your data using the created model:

```
ezc classify -n mymodel -H -i data.csv -o result.csv
```

The result.csv file will contain your classified data