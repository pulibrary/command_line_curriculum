## catmandu: the data processing toolkit

### Introductipn to catmandu

[Catmandu](https://librecat.org/) is a command line client and a Perl API to ease the export (E) transformation (T) and loading (L) of data into databases or data file, ETL in short.

Catmandu is specialized in processing, converting, creating library metadata from various input sources.

Catmandu can process: MARC, MAB, XML, Aleph X-services, BagIt, BibTeX, EAD, LIDO, JSON Markdown, MODS, OAI-PMH, ORCID, PLoS, PNX, RDF, RIS, SRU, XML, XLS, XSD , YAML, Z39.50 and many other formats. 

It can be installed via the following command:

```bash
cpanm install Catmandu::MARC
cpanm install Catmandu::XLS
```

We will look at Catmandu, a data processing toolkit. For the purposes of this workshop we will walk through processing data following the project's advent calendar examples:

```bash
cat ~/command_line_curriculum/data_files/weather.json
```
We will convert this into human friendly YAML using catmandu with:

```bash
catmandu convert JSON to YAML < ~/command_line_curriculum/data_files/weather.json
```
Catmandu can be used to process structured information like the UNIX `grep` command can process unstructured information. For instance let's try to filter out the name of this report. Type in this command:

```bash
catmandu convert JSON --fix 'retain_field(name)' to YAML < ~/command_line_curriculum/data_files/weather.json
```
The –fix option in `catmandu` is used to ‘massage’ the input weather.json filtering fields we would like to see. Only one fix was used ‘retain_field’, which throws away all the data from the input except the ‘name’ field. By the way, the file weather.json wasn’t changed! We only read the file and displayed the output of `catmandu` command.

The temperature in Gent is in the ‘temp’ part of the ‘main’ section in weather.json. To filter this out we need two retain_field fixes: one for the main section, one for the temp section:

```bash
catmandu convert JSON --fix 'retain_field(main); retain_field(main.temp)' to YAML < ~/command_line_curriculum/data_files/weather.json
```
When massaging data you often need to create many fixes to process a data file in the format you need. With your preferred editor you can write all the fixes in a file named `weather.fix` with the following content

```bash
retain_field(main)
retain_field(main.temp)
```
With this file it will be a bit easier to create many fixes. The name of the fix file can be used to repeat the commands above:

```bash
catmandu convert JSON --fix weather.fix to YAML < ~/command_line_curriculum/data_files/weather.json
```
To add more fixes we can again edit the weather.fix file and add the following two lines Type:

```bash
prepend(main.temp,"The temperature is")
append(main.temp," degrees Kelvin")
```

### catmandu JSON paths

From the previous sessions we know many commands how to examine data set. For instance, to get a quick overview of the content of `verbannte-buecher.json` we can use the `cat` command:

```bash
cat ~/command_line_curriculum/data_files/rows.json
```
Or, we could use the less command:

```
less ~/command_line_curriculum/data_files/rows.json
```
To count the number of lines, words and characters in `verbannte-buecher.json` we can use the `wc` command:

```bash
wc ~/command_line_curriculum/data_files/rows.json
```
This output shows that `verbannte-buecher.json` contains 3950 lines , 124454 words and 1084106 characters. Generic UNIX programs like `wc` have trouble with counting words in structured information. The command doesn’t know this file is in the JSON format which contains fields and values. You need to use specialized tools like `catmandu` to make sense of this output.

We also saw in the previous session how you can use `catmandu` to transform the JSON format into the YAML format which is easier to read and contains the same information:

```bash
catmandu convert JSON to YAML < ~/command_line_curriculum/data_files/rows.json
```
We also learned some fixes to retrieve information out of the JSON file like `retain_field(main.temp)`.

In this session we delve a bit deeper into ways how to point to fields in a JSON file.

This `main.temp` is called a JSON Path and points to a part of the JSON data you are interested in. The data, is structured like a tree. There are top level simple fields like: `data,meta` which contain only text values or numbers. There are also fields within the `data` coord that contain a deeper structure.

Using a JSON path you can point to every part of the JSON file using a dot-notation. For simple top level fields the path is just the name of the field:

* meta
* data

For the fields with deeper structure you add a dot ‘.’ to point to the leaves:

* meta.view.name

```bash
jq '.meta' ~/command_line_curriculum/data_files/rows.json | less
```

### Processing MARC with Catmandu

We've looked at JSON data in brief. We will now look at MARC data by running the following:

```bash
cat ~/command_line_curriculum/data_files/ebook.mrc
```
Like JSON the MARC file contains structured data but the format is different. All the data is on one line, but there isn’t at first sight a clear separation between fields and values. The field/value structure there but you need to use a MARC parser to extract this information. Catmandu contains a MARC parser which can be used to interpret this file. Type the following command to transform the MARC data into YAML:

```bash
catmandu convert MARC to YAML < ~/command_line_curriculum/data_files/ebook.mrc
```
When transforming MARC into YAML it looks like something with a simple top level field _id containing the identifier of the MARC record and a record field with a deeper array structure (or more correct an array-of-an-array structure).

We can use catmandu to read the \_id fields of the MARC record with the retain_field:

```bash
catmandu convert MARC --fix 'retain_field(_id)' to YAML < ~/command_line_curriculum/data_files/ebook.mrc
```
What is happening here? The MARC file `< ~/command_line_curriculum/data_files/ebook.mrc` contains more than one MARC record. For every MARC record catmandu extracts the `_id` field.

Extracting data out of the MARC record itself is a bit more difficult. MARC is an array-an-array, you need indexes to extract the data. For instance the MARC leader is usually in the first field of a MARC record. Indexing usually begins from 0 for the first field of an array.

```bash
catmandu convert MARC --fix 'retain_field(record.0)' to YAML < ~/command_line_curriculum/data_files/ebook.mrc
```
The leader value itself is the fifth entry in the resulting array. So, we need index 4 to extract it:

```bash
catmandu convert MARC --fix 'copy_field(record.0.4,leader); retain_field(leader)' to YAML < ~/command_line_curriculum/data_files/ebook.mrc
```
We used here a `copy_field` fix to extract the value into a field called leader. The `retain_field` fix is used to keep only this leader field in the result. To process MARC data this way would be very verbose, plus you need to know at which index position the fields are that you are interested in. This is something you usually don’t know.

Catmandu introduces Carsten Klee’s MARCspec to ease the extraction of MARC values out of a record. With the marc_map fix the command above would read:

```bash
marc_map("LDR",leader)
retain_field(leader)
```
Let's create a file named `myfixes.txt` with the content above, so we can run.

```bash
catmandu convert MARC --fix myfixes.txt to YAML < ~/command_line_curriculum/data_files/ebook.mrc
```
To extract the title fields, the field 245 remember?😉, you can write:

```bash
marc_map("245",title)
retain_field(title)
```
Or, if you are only interested in the $a subfield you could write:

```bash
marc_map("245a",title)
retain_field(title)
```
More elaborate mappings are possible which we will see shortly. As a warming up, here is some code to extract all the record identifiers, titles and isbn numbers in a MARC file into a CSV listing (which you can open in ~~Excel~~).

* Step 1, create a fix file myfixes.txt containing:

```bash
marc_map("245",title)
marc_map("020a",isbn.$append)
join_field(isbn,",")
remove_field(record)
```
* Step 2, execute this command:

```bash
catmandu convert MARC --fix myfixes.txt to CSV < ~/command_line_curriculum/data_files/ebook.mrc
```
In the fix above we mapped the 245-field to the title. The ISBN is in the 020-field. Because MARC records can contain one or more 020 fields we created an isbn array using the `isbn.$append` syntax. Next we turned the isbn array back into a comma separated string using the `join_field` fix. As last step we deleted all the fields we didn’t need in the output with the `remove_field` syntax.

