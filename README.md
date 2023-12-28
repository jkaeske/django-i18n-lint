# Django i18n Lint

[![codecov](https://codecov.io/gh/jkaeske/django-i18n-lint/graph/badge.svg?token=8t1WWUxxav)](https://codecov.io/gh/jkaeske/django-i18n-lint)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/jkaeske/django-i18n-lint/master.svg)](https://results.pre-commit.ci/latest/github/jkaeske/django-i18n-lint/master)

A simple script to find non-i18n text in a Django template.

Note: Since Django 3.1 the template tag was update from `{% trans "" %}` to `{% translate "" %}` and from `{% blocktrans "" %}` to `{% blocktranslate "" %}`.
The old `trans` versions are still recognized by the linter but the string wrapping will change the string to the new `translate` version.

## Usage

To use the Django Template i18n lint tool, you can run the `django_i18n_lint.py` script from the command line like so:

```bash
python django_i18n_lint.py [options] <path_to_your_template>
```

Running this command without any additonal options will output any non-i18n text found in the specified Django template to the command line.

Please replace `<path_to_your_template>` with the actual path to your Django template file.

### Options
- `-r`, `--replace`: Ask to wrap the strings in the file in `{% translate "" %}` tags.
- `-o`, `--overwrite`: When replacing the strings, overwrite the original file. If not specified, the file will be saved in a separate file named `X_translated.html`.
- `-f`, `--force`: Force to wrap strings with no questions.
- `-e`, `--exclude`: Exclude these filenames from being linted. This option can be used multiple times to exclude multiple files.
- `-x`, `--accept`: Exclude these regexes from results. This option can be used multiple times to exclude multiple regexes.

### Examples


```bash
# Lint all files in the current directory, excluding `exclude1.html` and `exclude2.html`
python django_i18n_lint.py -e exclude1.html -e exclude2.html

# Lint `file.html`, replacing strings in the file and overwriting the original file
python django_i18n_lint.py -r -o file.html

# Lint `file.html`, replacing strings in the file without asking for confirmation
python django_i18n_lint.py -r -f file.html
```

Code is copyright Rory McCann 2013, and dual licenced under the GNU GPL version3 (or at your option a later version), and the BSD licence. See the files LICENCE.GPLv3 and LICENCE.BSD for more information
