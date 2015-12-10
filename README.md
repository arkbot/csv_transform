# csv_transform

## Usage

1. Create a `foo.csv.yml` config for each `foo.csv`.
2. `require 'csv_transform'`
3. `table = Importer.import('foo.csv', HashWithIndifferentAccess)`
4. Post-process the returned hash as you please.

## Configuration Options

* `field`: top-level key which defines the header value for that field
* `type`: snake_case representation of the class
* `default_value`: default if a value is ommitted
* `lexicon`: value transforms
* `translations`: header transforms

## Configuration Example


```yaml
{
  # Global Options
  global: {
    headers: {
      formatters: [ ]
    }
  },

  # Field-specific Options
  fields: {
    genus: {
      type: symbol
    },
    period: {
      type: symbol
    },
    continent: {
      type: symbol,
      default_value: africa
    },
    diet: {
      type: symbol,
      lexicon: {
        'yes': carnivore,
        'no': herbivore
      },
      translations: [ carnivore ]
    },
    weight: {
      type: integer
    },
    locomotion_type: {
      type: symbol,
      translations: [ walking ]
    },
    description: {
      type: string
    }
  }
}
```
