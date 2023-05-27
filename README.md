# Migrate for GitHub Actions

A wrapper for [golang-migrate](https://github.com/golang-migrate/migrate) cli.  

## Input variables

See [action.yml](./action.yml) for more detailed information.

* `path` - relative path to your migration folder
* `database` - a command to connect to the database
* `command` - migrate cli command to run
* `prefetch` - Number of migrations to load in advance before executing (default 10)
* `lockTimeout` - Allow N seconds to acquire database lock (default 15)
* `verbose` - Print verbose logging
* `version` - Print version

[Migrate CLI docs](https://github.com/golang-migrate/migrate/tree/master/cmd/migrate)


## Usage

Executing remote ssh commands.

```yaml
name: run migration
on: [push]
jobs:

  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
        name: Checkout
        uses: actions/checkout@v3
      - name: Check with version flag
        uses: VoVaVc/migrate-github-action 
        with:
            path: ./backend/migrate
            database: postgres://username:password@localhost:5432/database_name?sslmode=disable
            command: up
```

## Contributing

Pull requests are welcome at [VoVaVc/migrate-github-action](https://github.com/VoVaVc/migrate-github-action/pulls)

## License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
