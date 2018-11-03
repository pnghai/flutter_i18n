## [0.2.0]

*flutter_i18n* now manage strings that contain parameters; an example can be: "Hello, ***{user}***!"
For a correct translation, you must use the third parameter of the *translate* method, a *Map<String, String>* where:
- the keys are the placeholders used in the *.json* file (i.e. user)
- the values are what you want to display

## [0.3.0]

*flutter_i18n* now supports language change at runtime. To use it, you ***must*** invoke the method
```sh
await FlutterI18n.refresh(buildContext, languageCode, {countryCode});
```

***NOTE***: *countryCode* is optional.

## [0.4.0]

*flutter_i18n* now supports plurals. To use it, invoke the method:
```sh
FlutterI18n.plural(buildContext, "your.key", pluralValue);
```

Where pluralValue is the integer value that will be used to determinate the plural form of the translation.

Here is an example of configuration of the *.json* file:

```sh
"clicked": {
    "times-0": "You clicked {times} times!",
    "times-1": "You clicked {time} time!",
    "times-2": "You clicked {times} times!"
  }
```

With this configuration, you must invoke the *plural* method as follow:

```sh
FlutterI18n.plural(buildContext, "clicked.times", pluralValue);
```

FlutterI18n will choose the right key using the value of pluralValue: it will match the last key with a value <= of pluralValue.