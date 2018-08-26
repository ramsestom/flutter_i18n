# flutter_i18n
I18n made easy, for Flutter!

------------------------------------------------



## Why you should use flutter_i18n?

The main goal of *flutter_i18n* is to simplify the i18n process in Flutter.
I would like to recreate the same experience that you have with the Angular i18n: simple *json* files, one for each language that you want to support.



## Configuration

To use this library, you must create in your project's root the following subfolders:

> /assets/flutter_i18n

and put inside them the *json* related to the translation, using the following configuration:

- If you want to specify the country code

    > /assets/flutter_i18n/{languageCode}_{countryCode}.json

- otherwise

    > /assets/flutter_i18n/{languageCode}.json

Of course, you must declare the subtree in your ***pubspec.yaml*** as assets:

```sh
flutter:
  assets:
    - assets/flutter_i18n/
```

The next step consist in the configuration of the *localizationsDelegates*; to use *flutter_i18n*, you should configure as follows:

```sh
localizationsDelegates: [
        FlutterI18nDelegate(useCountryCode),
        GlobalMaterialLocalizations.delegate,
        GlobalWidgetsLocalizations.delegate
],
```

The ***useCountryCode*** parameter depends on the *json* configuration:
- if you used the pattern {languageCode}_{countryCode}, ***useCountryCode*** must be **true**
- if you used the pattern {languageCode}, ***useCountryCode*** must be **false**


## flutter_i18n in action

After the configuration steps, the only thing to do is invoke the following method:

```sh
FlutterI18n.translate(buildContext, "your.key")
```

Where:
- *buildContext* is the *BuildContext* instance of the widget
- *your.key* is the key to translate