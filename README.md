# Italian gender detection tagger

Gender detection tagger based on OpenNLP 1.8.1 for italian fullnames.

It tags each word of the fullname with MALE / FEMALE / SURNAME class.

The fullname format can be:

- first name only
- last name only
- first name + last name
- last name + first name

## USAGE:

### API (Java):

```
try (InputStream modelIn = new FileInputStream("it-gender-tagger.bin"){
    POSModel model = new POSModel(modelIn);
    POSTaggerME tagger = new POSTaggerME(model);
    String fullName[] = new String[] {"Damiano", "Porta"};
    
    // Get the tags
    String tags[] = tagger.tag(fullName);
        
    // Get the confidence score for each tag
    double probs[] = tagger.probs();
}
```

### OPENNLP COMMAND:

```
opennlp POSTagger it-gender-tagger.bin
```

### TESTING (via OpenNLP command line tool):

```
opennlp POSTagger it-gender-tagger.bin
Loading POS Tagger model ... done (1,236s)

damiano
> damiano_MALE
damiano porta
> damiano_MALE porta_SURNAME
porta damiano
> porta_SURNAME damiano_MALE
porta
> porta_SURNAME
```

### ACCURACY (cross-validation):

```
0.99395
```

### LINKS

OpenNLP
http://opennlp.apache.org

### LICENSE

The model is released under Apache License, version 2.0
(http://www.apache.org/licenses/LICENSE-2.0.html).
