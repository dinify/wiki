# Aspects
- accessibility
- localization
- internationalization
- RTL layout support
- multi browser support

# Translations
In the database, the data provided by users will need to be translated and served in multiple languages.
There is a lot if different ways to design a database to accomodate translated fields.  
See [solutions/translations](./translations.md)

# Standards
Our solution is aligned with: [ECMAScript Internationalization API](http://www.ecma-international.org/ecma-402/1.0/) (ECMA-402), [Unicode CLDR](http://cldr.unicode.org/), and [ICU Message syntax](http://userguide.icu-project.org/formatparse/messages).

# Form structure
Sometimes, a form will need to be structured in a different way for different locales. 

### Address input
See data:  
[artifacts/i18n/supplemental/address-components](https://gitlab.com/dinify/artifacts/blob/master/i18n/supplemental/address-components.json)  
[artifacts/i18n/supplemental/address-format](https://gitlab.com/dinify/artifacts/blob/master/i18n/supplemental/address-format.json)

### Name input
Two fields for name: first and last is not true for all locales. Some locales only have one character as last name, or they use their father’s name as their last name, so it’s better to include a single field for name which they can fill out however they want. (It allows for more flexibility).

# Existing solutions
https://github.com/unicode-org/cldr
https://github.com/unicode-org/icu
https://rtlcss.com/index.html
