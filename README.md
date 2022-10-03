# Универсальная английская и русская раскладка для Linux

## Установка

Замените файлы `/usr/share/X11/symbols/us`, `/usr/share/X11/symbols/ru` и `/usr/share/X11/rules/evdev.xml` файлами из этого репозитория.


## Альтернативная установка

Если не хотите слепо заменять файлы, внесите изменения вручную:

1.  В файл `/usr/share/X11/xkb/symbols/us` допишите:

    ```
    partial alphanumeric_keys
    xkb_symbols "unieng" {
      
        include "us(basic)"
        name[Group1]= "English Universal";

        key <TLDE> { [ apostrophe, quotedbl, grave ] };
        key <AE01> { [ exclam, 1, onesuperior, exclamdown ] };
        key <AE02> { [ at, 2, twosuperior, onehalf ] };
        key <AE03> { [ numbersign, 3, threesuperior, onethird ] };
        key <AE04> { [ dollar, 4 ] };
        key <AE05> { [ percent, 5, permille ] };
        key <AE06> { [ asciicircum, 6 ] };
        key <AE07> { [ question, 7, questiondown ] };
        key <AE08> { [ asterisk, 8, infinity, doublelowquotemark ] };
        key <AE09> { [ parenleft, 9, leftdoublequotemark, leftsinglequotemark ] };
        key <AE10> { [ parenright, 0, rightdoublequotemark, rightsinglequotemark ] };
        key <AE11> { [ minus, underscore, endash, emdash ] };
        key <AE12> { [ equal, plus, notequal, plusminus ] };

        key <BKSL> { [ slash, bar, backslash] };

        key <AD03> { [ e, E, EuroSign ] };
        key <AD11> { [ bracketleft, braceleft, bracketleft, braceleft ] };
        key <AD12> { [ bracketright, braceright, bracketright, braceright ] };

        key <AC02> { [ s, S, section, U0301 ] };
        key <AC06> { [ h, H, U20BD ] };
        key <AC10> { [ semicolon, colon, guillemotleft, leftarrow ] };
        key <AC11> { [ asciitilde, asciitilde, guillemotright, rightarrow ] };

        key <AB02> { [ x, X, multiply ] };
        key <AB08> { [ comma, semicolon, less, lessthanequal ] };
        key <AB09> { [ period, colon, greater, greaterthanequal ] };
        key <AB10> { [ ampersand, ampersand, ampersand,  ellipsis ] };

        include "level3(ralt_switch)"
    };
    ```

2.  В файл `/usr/share/X11/xkb/symbols/ru` допишите:

    ```
    partial alphanumeric_keys
    xkb_symbols "unirus" {
        
        include "ru(common)"
        name[Group1]= "Russian Universal";

        key <TLDE> { [ apostrophe, quotedbl, grave ] };
        key <AE01> { [ exclam, 1, onesuperior, exclamdown ] };
        key <AE02> { [ at, 2, twosuperior, onehalf ] };
        key <AE03> { [ numbersign, 3, threesuperior, onethird ] };
        key <AE04> { [ dollar, 4 ] };
        key <AE05> { [ percent, 5, permille ] };
        key <AE06> { [ asciicircum, 6 ] };
        key <AE07> { [ question, 7, questiondown ] };
        key <AE08> { [ asterisk, 8, infinity, doublelowquotemark ] };
        key <AE09> { [ parenleft, 9, leftdoublequotemark, leftsinglequotemark ] };
        key <AE10> { [ parenright, 0, rightdoublequotemark, rightsinglequotemark ] };
        key <AE11> { [ minus, underscore, endash, emdash ] };
        key <AE12> { [ equal, plus, notequal, plusminus ] };

        key <BKSL> { [ slash, bar, backslash] };

        key <AD03> { [ Cyrillic_u, Cyrillic_U, EuroSign ] };
        key <AD05> { [ Cyrillic_ie, Cyrillic_IE, Cyrillic_io, Cyrillic_IO ] };
        key <AD11> { [ Cyrillic_ha, Cyrillic_HA, bracketleft, braceleft ] };
        key <AD12> { [ Cyrillic_be, Cyrillic_BE, bracketright, braceright ] };

        key <AC06> { [ Cyrillic_er, Cyrillic_ER, U20BD ] };
        key <AC10> { [ Cyrillic_zhe, Cyrillic_ZHE, guillemotleft, leftarrow]};
        key <AC11> { [ Cyrillic_e, Cyrillic_E, guillemotright, rightarrow ] };

        key <AB02> { [ Cyrillic_che, Cyrillic_CHE, multiply ] };
        key <AB07> { [ Cyrillic_softsign, Cyrillic_SOFTSIGN, Cyrillic_hardsign, Cyrillic_HARDSIGN ] };
        key <AB08> { [ comma, semicolon, less, lessthanequal ] };
        key <AB09> { [ period, colon, greater, greaterthanequal ] };
        key <AB10> { [ Cyrillic_yu, Cyrillic_YU, ampersand,  ellipsis ] };

        include "level3(ralt_switch)"
    };
    ```

3.  В файле `/usr/share/X11/xkb/rules/evdev.xml` найдите место:

    ```
          <configItem>
            <name>us</name>
            <!-- Keyboard indicator for English layouts -->
            <shortDescription>en</shortDescription>
            <description>English (US)</description>
            <countryList>
              <iso3166Id>US</iso3166Id>
            </countryList>
            <languageList>
              <iso639Id>eng</iso639Id>
            </languageList>
          </configItem>
    ```

    Под ним начинается раздел `<variantList>`. Добавьте в него новый вариант:

    ```
            <variant>
              <configItem>
                <name>unieng</name>
                <description>English Universal</description>
              </configItem>
            </variant>
    ```

4.  Аналогично добавьте вариант в русскую раскладку.

    Найдите:

    ```
          <configItem>
            <name>ru</name>
            <!-- Keyboard indicator for Russian layouts -->
            <shortDescription>ru</shortDescription>
            <description>Russian</description>
            <countryList>
              <iso3166Id>RU</iso3166Id>
            </countryList>
            <languageList>
              <iso639Id>rus</iso639Id>
            </languageList>
          </configItem>
    ```

    Добавьте:

    ```
            <variant>
              <configItem>
                <name>unirus</name>
                <description>Russian Universal</description>
              </configItem>
            </variant>
    ```


## Credits

Сделано на основе [версии Никиты Широкова](https://github.com/braindefender/universal-layout).

Special thanks to [Tonsky](https://tonsky.me/).

