# Security Scanner for Laravel - Github Actions

GitHub Action for running Security Scanner for Laravel in your CI/CD pipeline.

You can use the Action as follows:

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
          # specify either minimum-grade or checks
          minimum-grade: "F"
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
