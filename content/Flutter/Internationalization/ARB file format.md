---
creation date: 2024-02-27 16:29
tags:
  - flutter
  - dart
  - documentation
---
https://localizely.com/flutter-arb/

# ICU format
[ICU formatter](https://localizely.com/icu-message-editor)

### Plural
```json
{hour, plural,
    zero{{min, plural,
        zero{0 minute}
        one{1 minute}
        other{{min} minutes}
    }}
    one{{min, plural,
        zero{1 hour}
        one{1 hour 1 minute}
        other{1 hour {min} minutes}
    }}
    other{{min, plural,
        zero{{hour} hours}
        one{{hour} hours 1 minute}
        other{{hour} hours {min} minutes}
    }}
}
```
