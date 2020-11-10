# Google Keep Stats

Google Keep Task List statistics exporter tool.

![Example user flow](./example_flow.png)

Features:

- Calculate overall completion rate for task lists by keyword
- Aggregate task list completion daily/weekly/monthly/yearly
- Export time series data and aggregates as CSV
- Configurable date formats

Supported metrics:

- Number of checked items
- Number of unchecked items
- Total items
- Completion rate

## Installation

This script requires Python 3 and https://github.com/kiwiz/gkeepapi to run. Install the pre-requisite libraries via Pip3:

```
pip3 install gkeepapi keyring
```

Optional: make the script executable:

```
chmod +x gkeepstats.py
```

## Usage

This tool is configured via a config file, to avoid reentering parameters on every call. Copy the example config file:

```
cp gkeepstats.example.ini gkeepstats.ini
```

And edit it to come up with your own setup.

Then you can simply call the script in one of the available ways:

```
python3 gkeepstats.py
# or
./gkeepstats.py
```

For available command line options see the help page:

```
./gkeepstats.py -h
```

### Authentication

GKeepStats can use the operating system key ring to save the access token securely. First time you need to authenticate with your password by adding an `--auth`:

```
./gkeepstats.py --auth
```

If it authenticates successfully and your operating system supports key ring, access token is saved and from the next time onwards you can use it without `--auth` and password prompt won't be necessary:

```
./gkeepstats.py
```

### Output

By default, CSV export is written to files in the current folder. Each metric is written in a separate file called `{Metric}_{mode}_{timestamp}.csv`.

You can disable CSV export by adding `--dry` option:

```
./gkeepstats.py --dry
```

Use the `--verbose` or `-v` option to enable verbose printing of the results in the console, e.g.:

```
./gkeepstats.py -v
./gkeepstats.py -v --dry
```

## Credits

This tool uses the unofficial Google Keep API https://github.com/kiwiz/gkeepapi by [kiwiz](https://github.com/kiwiz). Google Keep is of course a registered trademark of Google and neither the API nor this script are affiliated with Google.
