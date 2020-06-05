# Kibana Community Translations

This plugin centralize all translations for kibana created by the community. The aim is to help the kibana team to translate the application.

## How to use it

### Installation

  TODO

### Kibana configuration

Change / Add the parameter ``i18n.locale`` in the config file of kibana (config/kibana.yml). The value of this parameter is the locale id that you can found in the list of available languages below.

For example, if you want use the french translation, add the following line in your kibana config file:

``` yaml
i18n.locale: fr
```

## Available languages

We are working on it, so any help is welcomed :-)

### Kibana 7.7.x

Language | Locale | Translation progression
-------- | ------ | -----------------------
French | fr | 0.00 %

### Kibana 7.6.x

Language | Locale | Translation progression
-------- | ------ | -----------------------
French | fr | 0.02 %

## Traductor needed

- Italian
- Spanish

## Contributing

Anyone can contribute to this project

### Git workflow

#### Master branch

The master branch is master. This branch always contains the current working.

#### Release branch

A release branch is created when release the plugin for a new major version of Kibana.

A release branch is always created from the master branch.

Example: For a release for 7.6.0, we have to create a branch from master named release/v7.6.
All future works on the 7.6.x of kibana will be added in this branch

#### Feature branch

Feature branches can be used by contributors to work on specific feature.

### Add a new language

If the language doesn't exist yet, you can add it to this repository.
You have to follow these steps:

- Create a file named ``{locale}.json`` in the ``translations`` directory
  where ``{locale}`` is [ISO 639 language code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)

- Add this content to your file:

``` json
{
  "formats": {
    "number": {
      "currency": {
        "style": "currency"
      },
      "percent": {
        "style": "percent"
      }
    },
    "date": {
      "short": {
        "month": "numeric",
        "day": "numeric",
        "year": "2-digit"
      },
      "medium": {
        "month": "short",
        "day": "numeric",
        "year": "numeric"
      },
      "long": {
        "month": "long",
        "day": "numeric",
        "year": "numeric"
      },
      "full": {
        "weekday": "long",
        "month": "long",
        "day": "numeric",
        "year": "numeric"
      }
    },
    "time": {
      "short": {
        "hour": "numeric",
        "minute": "numeric"
      },
      "medium": {
        "hour": "numeric",
        "minute": "numeric",
        "second": "numeric"
      },
      "long": {
        "hour": "numeric",
        "minute": "numeric",
        "second": "numeric",
        "timeZoneName": "short"
      },
      "full": {
        "hour": "numeric",
        "minute": "numeric",
        "second": "numeric",
        "timeZoneName": "short"
      }
    },
    "relative": {
      "years": {
        "units": "year"
      },
      "months": {
        "units": "month"
      },
      "days": {
        "units": "day"
      },
      "hours": {
        "units": "hour"
      },
      "minutes": {
        "units": "minute"
      },
      "seconds": {
        "units": "second"
      }
    }
  },
  "messages": {
  }
}
```

- Add in the ``.i18nrc.json`` file, the path to the new translation file

- Update this README to add your language in the available languages part

#### Note
DO NOT Translate the text between {} (example : {title})

### Debugging tools

I18n tools are available in the Kibana repository.  
You can found details about these tools [here](https://github.com/elastic/kibana/blob/master/src/dev/i18n/README.md)

#### Create a file containing all defaults message to translate

To have an overview of all messages to translate, you can use this command that will generate a JSON file with default messages.

``` shell
node scripts/i18n_extract --path . --output-dir OUTPUT_DIR
```

where ``OUTPUT_DIR`` is the path where you want generate the JSON file.

The generated JSON file contains formats object and messages object with id: message or id: {text, comment} pairs. Messages are sorted by id.

#### Verifying your locale file

To verify your locale file, find unused / missing messages, key duplications and value references mismatches. You can use the following command.

``` shell
node scripts/i18n_integrate --source plugins/kibana_community_translations/translations/{locale}.json
```
