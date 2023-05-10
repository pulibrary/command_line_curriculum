## marcli tool

`marcli` is a command-line tool for parse MARC records.

Install the tool with the following command:

```bash
wget https://github.com/hectorcorrea/marcli/releases/download/v1.1.0/marcli_linux
sudo mv marcli_linux /usr/local/bin/marcli
sudo chmod u+x /usr/local/bin/marcli
```

### Sample Usage

Borrowed from the project's page:

Output MARC data to the console in a line delimited format (`marcli` automatically detects whether the file provided is in MARC XML or MARC binary):

```bash
marcli -file ~/command_line_curriculum/data_files/test_1a.mrc
marcli -file ~/command_line_curriculum/data_files/test_10.xml
```

Extract MARC records on file that contain the string "wildlife"
```bash
marcli -file ~/command_line_curriculum/data_files/test_10.mrc -match wildlife
```

Extracts MARC records on file that contain the string "wildlife" but outputs only fields "LDR,001,040,245a,650" for each record, LDR means the leader of the MARC record. In the `-fields` parameter a letter (or letters) after the field tag indicates to output only those subfields. For example "907xz" means output subfield "x" and "z" in field "907".

```bash
marcli -file ~/command_line_curriculum/data_files/test_10.mrc -match wildlife -fields LDR,010,040,245a,650
```

The `-matchFields` parameter can be used to limit the fields where the match will be made:

```bash
marcli -file=~/command_line_curriculum/data_files/test_10.mrc -match=web -matchFields=530
```

You can also use the `exclude` option to indicate fields to exclude from the output (notice that only full fields are supported here, e.g. 970 is accepted but not 970a)

You can also filter based on the presence of certain fields in the MARC record (regardless of their value), for example the following will only output records that have a MARC 110 field:

```bash
marcli -file ~/command_line_curriculum/data_files/test_10.mrc -hasFields 110
```

The program supports a `format` parameter to output to other formats other than MARC line delimited (MRK) such as MARC XML, JSON, or MARC binary. Notice that not all the features are available in all the formats yet.

You can also pass `start` and `count` parameters to output only a range of MARC records.


More can be found at the [Project's Github Page](https://github.com/hectorcorrea/marcli)