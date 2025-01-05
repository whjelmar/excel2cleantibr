
# excel2cleantibr

[![CRAN
Status](https://www.r-pkg.org/badges/version/excel2cleantibr)](https://cran.r-project.org/package=excel2cleantibr)
[![Build
Status](https://github.com/yourusername/excel2cleantibr/workflows/R-CMD-check/badge.svg)](https://github.com/yourusername/excel2cleantibr/actions)

## Overview

`excel2cleantibr` is an R package that simplifies working with Excel
files by reading all sheets and transforming them into tidy tibbles. It
provides configurable options for data cleaning, sheet naming
conventions, and output formats to make your workflow more efficient.

------------------------------------------------------------------------

## Installation

### From CRAN:

``` r
install.packages("excel2cleantibr")
```

### From GitHub:

``` r
devtools::install_github("yourusername/excel2cleantibr")
```

------------------------------------------------------------------------

## Features

- Automatically reads all sheets from an Excel file and converts them to
  tibbles.
- Configurable data cleaning options, including:
  - Removing empty rows/columns.
  - Standardizing column names (e.g., snake_case).
  - Filling missing values using forward-fill.
- Supports custom sheet and column naming conventions.
- Output as a named list or directly into the global environment.
- User-defined configurations using JSON or YAML files.

------------------------------------------------------------------------

## Example Usage

### Basic Example

``` r
library(excel2cleantibr)

# Path to your Excel file
file <- system.file("extdata", "basic.xlsx", package = "excel2cleantibr")

# Read all sheets into a list of tibbles
tibbles <- read_excel_tibbles(file)

# Print the tibbles
print(tibbles)
```

### Advanced Example: Custom Configuration

Save your configuration as a JSON file:

``` json
{
  "remove_empty_rows": true,
  "remove_empty_cols": true,
  "standardize_names": true,
  "fill_missing_values": true
}
```

Then use it in your workflow:

``` r
config_file <- "path/to/config.json"

# Apply custom configurations
tibbles <- read_excel_tibbles(file, config = config_file)
```

------------------------------------------------------------------------

## Contributing

We welcome contributions! To contribute:

1.  Fork the repository.
2.  Create a new branch for your feature/bug fix.
3.  Submit a pull request for review.

Please check the `CONTRIBUTING.md` file for detailed guidelines.

------------------------------------------------------------------------

## License

This package is licensed under the MIT License. See the `LICENSE` file
for details.

------------------------------------------------------------------------

## Acknowledgments

- Built using `readxl`, `janitor`, `zoo`, `purrr`, and `tibble`.
- Inspired by the tidyverse philosophy.

------------------------------------------------------------------------