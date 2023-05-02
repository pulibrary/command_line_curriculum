## jq: sed for JSON

`jq` is a command-line tool for processing JSON in every imaginable way; its website describes it as the `sed` of the JSON world. In the next section we will look at comparable ways of standard command-line utilities and show how they can easily be replicated with `jq`

Install the tool with the following command:

```bash
sudo apt -y install jq
```

In the same way that we used the `cat` command, we can view our example json data with:

```bash
jq . ~/command_line_curriculum/data_files/bike_rides.json
```

The `cat` command for that would be:

```bash
cat ~/command_line_curriculum/data_files/bike_rides.csv
```

In the same way that we used the `cut` command we can list the first field of our JSON example file anf the first and second field.

```bash
jq '.trip_id' ~/command_line_curriculum/data_files/bike_rides.json
jq '{trip_id, duration}' ~/command_line_curriculum/data_files/bike_rides.json
```

The similar command for that with `cut` is:

```bash
cut -d , -f 1 ~/command_line_curriculum/data_files/bike_rides.csv
cut -d , -f 1,2 ~/command_line_curriculum/data_files/bike_rides.csv
```

We can also create an array of data from the json fields with

```bash
jq '[.trip_id, .duration]' ~/command_line_curriculum/data_files/bike_rides.json
```

We used `head` and `tail` to select the first and last elements of a file respectively.

```bash
head -n 5 ~/command_line_curriculum/data_files/bike_rides.csv
tail -n 5 ~/command_line_curriculum/data_files/bike_rides.csv
```

We do this with `jq` with:

```bash
jq -s '.[:5]'  ~/command_line_curriculum/data_files/bike_rides.json
jq -s '.[-5:]' ~/command_line_curriculum/data_files/bike_rides.json
```

We used `wc` to count the number of values in a file with

```bash
wc -l ~/command_line_curriculum/data_files/bike_rides.csv
```
We can do the same with `jq` with:

```bash
jq -s length ~/command_line_curriculum/data_files/bike_rides.json
```

We seen how the `sort` command allows you to sort a file with:

```bash
sort ~/command_line_curriculum/data_files/bike_rides.csv
```

This is also possible with `jq` using:

```
jq -s sort ~/command_line_curriculum/data_files/bike_rides.json
```

`jq` allows us much like `sort` to do this by field

```bash
jq -s 'sort_by(.duration)' ~/command_line_curriculum/data_files/bike_rides.json
```

The results here are easier to follow than the comparable:

```bash
sort -k2,1 ~/command_line_curriculum/data_files/bike_rides.csv
```
