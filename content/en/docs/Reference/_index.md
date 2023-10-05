---
title: Command reference
description: All EZClassifier command syntax and options
weight: 9
---

All the services offered by EZClassifier can be accessed using the command through the `ezc` command. 
See the [getting started section](/docs/getting-started) for the instructions for  downloading and installing it.

## General syntax

For java JRE 17+ is required

The command returns 0 on success  or a value > 0 on failure. The logs are written on stdout by default and can be redirected.

All commands requires a valid api key in the environment variable `API_KEY`

```
export TC_API_KEY=<api-key>
```


**Usage:**

```bash
java -jar <path of the downloaded jar file> [-hV] [COMMAND]
```

A software agent that classifies text based on the provided prototypes

**Options:**

- `-h, --help`  
  Show this help message and exit.

- `-V, --version`  
  Print version information and exit.

**Commands:**

- `model`  
  Manage models

- `classify`  
  Perform classification


### Command `model train`

Train the model

```bash
model train [-hHSV] -C=<labelIndex> [-e=<apiEndpoint>]
                    [-i=<inputFilename>] [-k=<apiKey>] -n=<name> -P=<textIndex>
                    [-W=<weightIndex>]
```

You can enhance an already trained model  by adding new examples through multiple calls to the "model train" command.

**Options:**

- `-C, --class-index=<labelIndex>`  
  The column index in the CSV file that contains the field with the class attached to the text (from 0). By default is 1

- `-e, --endpoint=<apiEndpoint>`
  Api endpoint.  By default `https://api.mopso.io/v1/tc`

- `-h, --help`  
  Show this help message and exit.

- `-H, --header`  
  Will ignore the first line of the CSV file.

- `-i, --input=<inputFilename>`  
  The file containing the training data, by default “-” that means std in (e.g. -i - ). The stream is supposed to be in CSV format and MUST contain two fields (“prototype” and “class”) plus an optional field “weight” ranging from 0 to 1 (1 by default).

- `-k, --api-key=<apiKey>`  
  A registered API key. If not present, the value from the env variable TC_API_KEY is used.

- `-n, --name=<name>`  
  Name of the model to train, create a new model if the name is not found.

- `-P, --prototype-index=<textIndex>`  
  The column index in the CSV file that contains the field with the text to classify (from 0)

- `-S, --strict`  
  Runs the program in strict mode: any partially recoverable exception thrown during the execution will stop the training process. If not run in strict mode, the application will try to compensate for as many errors as possible.

- `-V, --version`  
  Print version information and exit.

- `-W, --weight-index=<weightIndex>`  
  The column index in the CSV file that contains the field with the classification weight (from 0). Set to -1 if not present.

### Command `model ls`

List models

```bash
model ls [-hV] [-e=<apiEndpoint>] [-k=<apiKey>]
```

**Options:**

- `-e, --endpoint=<apiEndpoint>`
  Api endpoint.  By default `https://api.mopso.io/v1/tc`

- `-h, --help`  
  Show this help message and exit.

- `-k, --api-key=<apiKey>`  
  A registered API key. If not present, the value from the env variable TC_API_KEY is used.

- `-V, --version`  
  Print version information and exit.

### Command `model rm`

```bash
model rm [-hV] [-e=<apiEndpoint>] [-k=<apiKey>] -n=<name>
```

**Options:**

- `-e, --endpoint=<apiEndpoint>`
  Api endpoint.  By default `https://api.mopso.io/v1/tc`

- `-h, --help`  
  Show this help message and exit.

- `-k, --api-key=<apiKey>`  
  A registered API key. If not present, the value from the env variable TC_API_KEY is used.

- `-n, --name=<name>`  
  Name of the model to remove.

- `-V, --version`  
  Print version information and exit.

### Command `classify`

**Usage:**  
`classify [-hHSV] [-e=<apiEndpoint>] [-i=<inFilename>] [-I=<textIndex>]`
`         [-k=<apiKey>] -n=<name> [-o=<outFilename>] [-t=<threshold>]`
`         [-T=<threads>]`

Perform classification

- **`-e, --endpoint=<apiEndpoint>`** 
  Api endpoint. By default `https://api.mopso.io/v1/tc`

- **`-h, --help`**  
  Show this help message and exit.

- **`-H, --header`**  
  If the flag is present, the first line of the input file is copied to the output with added columns 'CLASS' and 'SIMILARITY_SCORE'. By default, it is assumed that the input has no header.

- **`-i, --input=<inFilename>`**  
  The input filename; “-” means stdin (e.g. -i - ). The file must be in CSV format.

- **`-I, --index=<textIndex>`**  
  The index in the CSV file that contains the field to classify (from 0). By default, the index is 0.

- **`-k, --api-key=<apiKey>`**  
  A registered API key. If not present, the value from the env variable TC_API_KEY is used.

- **`-n, --name=<name>`**  
  Model name.

- **`-o, --output=<outFilename>`**  
  The output filename; “-” means stdout (e.g. -o - ).

- **`-S, --strict`**  
  Runs the program in strict mode: any partially recoverable exception thrown during the execution (i.e. a classification that fails or a row that can't be parsed) will stop the program, truncating the output to the last stable state. If not run in strict mode, the application will try to compensate for as many errors as it's possible.

- **`-t, --threshold=<threshold>`**  
  Number between 0 (not included) and 1 (included) that is used to determine whether a match ‘SIMILARITY_SCORE’ is too low to be considered valid. In this case, the ‘CLASS’ is set to ‘OTHER’. Default value is 0.2.

- **`-T, --threads=<threads>`**  
  The number of parallel jobs to be used by the classification services, by default is 1. If more than 1 is used, the output order is not preserved. The value is capped to the number of CPU cores.

- **`-V, --version`**  
  Print version information and exit.
