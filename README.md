# dep-scan-threshold-analyzer-action

Fully open-source GitHub Action for checking whether vulnerability reports from dep-scan comply with predefined security
thresholds.

## Licenses

![GNU General Public License v3](https://www.gnu.org/graphics/gplv3-127x51.png)

### What does that mean?

- Anyone can run the software licensed under GPLv3 for any purpose without restrictions.
- GPLv3 ensures that users have access to the software's source code, allowing them to study, modify, and improve it.
- Users can distribute copies of the software, but they must do so under the terms of GPLv3. This ensures that the
  original freedoms are maintained in new versions.
- If someone modifies the software and distributes it, they must do so under the same GPLv3 terms and provide the source
  code for their modifications as well.
- If you are interested in knowing more details about the license, please visit the following links:
    - Spanish: https://www.gnu.org/licenses/gpl-3.0.es.html
    - English: https://www.gnu.org/licenses/gpl-3.0.en.html

## Inputs

The action accepts the following inputs:

- **report_file** (optional):
    - Description: Specifies the filepath where the reports are stored.
    - Default: `/github/workspace/reports/sbom-universal.vdr.json`

- **threshold** (optional):
    - Description: Defines the threshold level used to determine when a vulnerability or issue should be considered a
      failure.
    - Default: `5.0`

## Usage

To use this action in your GitHub workflow, you can include it in your `.github/workflows/your-workflow.yml` file as
follows:

```yaml
name: Example Workflow

on: [ push ]

jobs:
  analyze:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Run dep-scan-threshold-analyzer
        uses: cob0/dep-scan-threshold-analyzer@main
        with:
          report_file: 'path/to/your/report.json'  # Optional
          threshold: '5.0'  # Optional
```

## Running the Action

This action runs in a Docker container. The action uses the following Docker image:

```plaintext
ghcr.io/cob0/dep-scan-threshold-analyzer:1.0.0
```

The main script executed is `dep_scan_threshold_analyzer.py`, which takes the following arguments:

- `-f`: Specifies the report file.
- `-t`: Specifies the threshold value.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or bug fixes.