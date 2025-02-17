
# excel2cleantibr

[![CRAN
Status](https://www.r-pkg.org/badges/version/excel2cleantibr)](https://cran.r-project.org/package=excel2cleantibr)
[![Build
Status](https://github.com/yourusername/excel2cleantibr/workflows/R-CMD-check/badge.svg)](https://github.com/yourusername/excel2cleantibr/actions)

## Overview

`excel2cleantibr` simplifies working with Excel files by reading all
sheets and transforming them into tidy tibbles. The package provides: -
Configurable data cleaning options. - Flexible naming conventions for
sheet and column names. - A robust system for loading and managing
configuration files.

------------------------------------------------------------------------

## Installation

### From CRAN:

``` r
install.packages("excel2cleantibr")
```

### From GitHub:

``` r
devtools::install_github("whjelmar/excel2cleantibr")
```

------------------------------------------------------------------------

## Features

- Automatically reads all sheets from an Excel file and converts them to
  tibbles.
- Configurable data cleaning options, including:
  - Removing empty rows/columns.
  - Standardizing column names (e.g., snake_case).
  - Filling missing values using forward-fill.
- Supports:
  - Default configuration saved in the user’s home directory.
  - Spreadsheet-specific configurations saved in the working directory.
- Output options:
  - Return as a named list.
  - Save directly into the global environment.

------------------------------------------------------------------------

## Example Usage

### Saving and Using Configurations

1.  **Save a Default Configuration** Save a default configuration file
    to the user’s home directory:

    ``` r
    save_default_config()
    ```

    This creates a file `.excel2cleantibr_config.json` in the user’s
    home directory with default cleaning options.

2.  **Save a Spreadsheet-Specific Configuration** Create a custom
    configuration for a specific spreadsheet in the working directory:

    ``` r
    save_spreadsheet_config(
        "example.xlsx",
        list(
            remove_empty_rows = TRUE,
            remove_empty_cols = FALSE,
            standardize_names = TRUE,
            fill_missing_values = TRUE
        )
    )
    ```

3.  **Automatically Load Configurations** When processing a spreadsheet,
    the package automatically:

    - Checks for a spreadsheet-specific configuration in the working
      directory.
    - Falls back to the default configuration in the home directory.

    ``` r
    tibbles <- read_excel_tibbles("example.xlsx")
    ```

------------------------------------------------------------------------

### Reading and Cleaning Excel Files

#### Basic Usage

Read all sheets from an Excel file and clean data using the default
configuration:

``` r
library(excel2cleantibr)

file <- system.file("extdata", "basic.xlsx", package = "excel2cleantibr")
tibbles <- read_excel_tibbles(file)

# Print the cleaned tibbles
print(tibbles)
```

#### Advanced Usage with Custom Configurations

Manually specify a custom configuration file:

``` r
config_file <- "path/to/config.json"
tibbles <- read_excel_tibbles("example.xlsx", config = config_file)
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
