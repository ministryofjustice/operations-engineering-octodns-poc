# OctoDNS Proof of Concept


This repository demonstrates how to use OctoDNS to manage DNS records.

## Setup

1. Clone the repository to your local machine:

```bash
git clone https://github.com/ministryofjustice/operations-engineering-octodns-poc.git
```

2. Navigate to the cloned repository:

```bash
cd operations-engineering-octodns-poc
```

3. Create a new virtual environment and activate it:

```bash
python3 -m venv env
source env/bin/activate
```

4. Install OctoDNS:

```bash
pip install octodns
```
## Configuration

The DNS configuration is defined in the config.yaml file. Here's an example of what it might look like:

```yaml
providers:
    config:
        class: octodns.provider.yaml.YamlProvider
        directory: ./config   # directory where your YAML files are located
        default_ttl: 300      # default TTL for records

zones:
    example.com.:
        sources:
            - config
        targets:
            - config
```

## Usage

To sync your DNS configuration, run the following command:

```bash
octodns-sync --config-file=./config.yaml
```

## CI/CD

This repository uses GitHub Actions to automatically sync the DNS configuration whenever changes are pushed to the main branch. See the .github/workflows/main.yml file for the workflow configuration.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
