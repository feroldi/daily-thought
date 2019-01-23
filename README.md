# daily-thought

This is a personal utility for quickly logging anything, such as thoughts, events, tasks etc.

Logs are separated into markdown files by date.
The date format follows ISO 8601.
For instance, a file named `2019-01-29.md` represents all logs from January 29th, 2019.
It's possible to choose which date you're going to log, which means you may modify or remove previous logged text.

All changes (text addition, removal, modification etc) are kept as history through git (in case it's installed).
This turned out to be very pleasant, as commit messages may be used to give logs a title.

## Usage

    usage: daily-thought.py [-h] [-d YYYY-MM-DD] [-o PATH]

    optional arguments:
      -h, --help            show this help message and exit
      -d YYYY-MM-DD, --date YYYY-MM-DD
                            specify the date of the report in UTC format
      -o PATH, --work-dir PATH
                            the working directory where logs are kept

Example:

    daily-thought.py --work-dir /path/to/logs -d 2019-01-29

First of all, the utility needs to know where the logs should be kept.
This is set with the `--work-dir` parameter.
If this parameter is not provided, then the current directory is used.
If you want the git part to work, you will have to initialize it manually:

    git init /path/to/logs

The directory is expected to exist beforehand, either way.

The `-d` date parameter is optional, and is there only to provide a way to choose dates other than the current one.
By default, it opens a log to the current date.
The date format for `-d` is `YYYY-MM-DD`, where `YYYY` is the year, `MM` is the month with a leading zero, and `DD` is the day with a leading zero.

It's tiresome to type the entire date when you just want to log something to yesterday.
So, instead of typing it all, you may give `-d` an offset, such as `-1`, to mean *log to yesterday's date*.
It accepts any positive or negative number, which is added to the current date to form the desired date.

Once the command is run, it tries to open your favorite text editor provided by the `EDITOR` environment variable.
If this variable is not set, then it fires up `vi` instead.
If `vi` is not present, then I'm sorry.
Please, kindly set your `EDITOR` environment variable.

## License

This project is licensed under the MIT License. See LICENSE.
