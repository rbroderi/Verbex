Verbex: Python verbal based regular expressions
================================================

<!-- ![Build Status](https://github.com/rbroderi/Verbex/actions/workflows/main.yml/badge.svg?event=push) -->
<!-- [![GitHub License](https://img.shields.io/github/license/rbroderi/Verbex)](https://github.com/rbroderi/Verbex/blob/master/LICENSE) -->
[![Generic badge](https://img.shields.io/badge/license-GPL‐3.0-orange.svg)](https://github.com/rbroderi/Verbex/blob/master/LICENSE)
[![Code style: black](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![PyPI pyversions](https://img.shields.io/pypi/pyversions/verbex)](https://pypi.python.org/pypi/Verbex/)
[![Generic badge](https://img.shields.io/badge/mypy-typed-purple.svg)](http://mypy-lang.org/)
[![Generic badge](https://img.shields.io/badge/beartype-runtime_typed-cyan.svg)](https://github.com/beartype/beartype)
[![Generic badge](https://img.shields.io/badge/bandit-checked-magenta.svg)](https://bandit.readthedocs.io/en/latest/)
[![Generic badge](https://img.shields.io/badge/uv-requirements-yellow.svg)](https://github.com/astral-sh/uv)
[![Dynamic TOML Badge](https://img.shields.io/badge/dynamic/toml?url=https%3A%2F%2Fraw.githubusercontent.com%2Frbroderi%2FVerbex%2Fmaster%2Fpyproject.toml&query=%24.project.version&label=Version)](https://github.com/rbroderi/Verbex/releases)


## Installation
```bash
pip install Verbex
```
## Usage
```python
from verbex import Verbex
verbex = Verbex()
```

## Documentation
[API](https://rbroderi.github.io/Verbex/)
## Examples

### Testing if we have a valid URL
```python
# Create an example of how to test for correctly formed URLs
verbex = Verbex()
tester = (verbex.
            start_of_line().
            find('http').
            maybe('s').
            find('://').
            maybe('www.').
            anything_but(' ').
            end_of_line()
)

# Create an example URL
test_url = "https://www.google.com"

# Test if the URL is valid
if re.match(test_url.regex,test_url):
    print("Valid URL")

# Print the generated regex
print(tester) # => ^(http)(s)?(\:\/\/)(www\.)?([^\ ]*)$
```
### Replacing strings
```python
# Create a test string
replace_me = "Replace bird with a duck"

# Create an expression that looks for the word "bird"
expression = Verbex().find('bird')

# Compile and use the regular expression using re
import re
regexp = expression.compile()
result_re = regexp.sub('duck', replace_me)
print(result_re)
```

## Developer setup : running the tests
```bash
just tests
```
## Other implementations
You can view all implementations on [VerbalExpressions.github.io](http://VerbalExpressions.github.io)
