# Security Scanner for Laravel - Github Actions

GitHub Action for running Security Scanner for Laravel in your CI/CD pipeline.

You can use the Action in two ways:

1. Scan your site expecting a minimum grade.
2. Scan your site expecting specific checks to succeed.

## Examples

### Scan your site expecting a minimum grade

```yaml
name: Security Scanner for Laravel

on: push

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Run Security Scanner for Laravel to check your site for vulnerabilities
        uses: ephort/security-scanner-actions/v1@main
        with:
          target-url: "https://my-laravel-site.tld"
          minimum-grade: "F"
```

Save the contents to a file in your GitHub repository in the `.github/workflows` directory, e.g. `.github/workflows/security_scanner.yml`

### Scan your site expecting specific checks to succeed

```yaml
name: Security Scanner for Laravel

on: push

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - name: Run Security Scanner for Laravel to check your site for vulnerabilities
        uses: ephort/security-scanner-actions/v1@main
        with:
          target-url: "https://my-laravel-site.tld"
          checks: "EnvChecker,CookieFlagsChecker"
```

Save the contents to a file in your GitHub repository in the `.github/workflows` directory, e.g. `.github/workflows/security_scanner.yml`

## Inputs

| Property      | Default | Required | Description                          |
|---------------|---------|----------|--------------------------------------|
| target-url    |         | Required | The URL of the site to scan.         |
| minimum-grade | F       | Optional | The minimum grade to pass the scan. Possible values are: `A+`, `A`, `B`, `C`, `D`, `E`, `F`. |
| checks        |         | Optional | The specific checks to run. Comma-separated string. Possible values are: CookieChecker, CookieFlagsChecker, PoweredByChecker, EnvChecker, ExposedPhpinfoChecker, ComposerChecker, HtAccessChecker, HtPasswordChecker, InsecureHeaderChecker, SSLChecker |

You should specify either 'checks' or 'minimum-grade'.

Grade is not calculated when you select specific checks to run.

## License
The MIT License (MIT). Please see [License File](LICENSE) for more information.
