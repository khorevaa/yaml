# `Y`_et_ `A`_in't_ `M`_arup_ `L`_anguage_ для OScript

[![Stars](https://img.shields.io/github/stars/khorevaa/yaml.svg?label=Github%20%E2%98%85&a)](https://github.com/khorevaa/yaml/stargazers)
[![Release](https://img.shields.io/github/tag/khorevaa/yaml.svg?label=Last%20release&a)](https://github.com/khorevaa/yaml/releases)
[![Открытый чат проекта https://gitter.im//oscript-yaml/Lobby](https://badges.gitter.im/khorevaa/yaml.png)](https://gitter.im/oscript-yaml/Lobby?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![Build Status](https://travis-ci.org/khorevaa/yaml.svg?branch=master)](https://travis-ci.org/khorevaa/yaml)
[![Coverage Status](https://coveralls.io/repos/github/khorevaa/yaml/badge.svg?branch=master)](https://coveralls.io/github/khorevaa/yaml?branch=master)

Короткое название библиотеки `yaml`

Данная библиотека для языка OScript, читать файлы на составленные в разметке [yaml](http://yaml.org/) .

> Используется сторонняя библиотека dll [OneScript-YamlDotNet](https://github.com/jdeshin/OneScript-YamlDotNet)

[Документация и описание публичного API](docs/readme.md)

## Быстрый старт

### Пример простого использования

```bsl
#Использовать yaml

```bsl
ПодключитьВнешнююКомпоненту("ПутьКПапкеГдеРасположеныDll\YamlDotNetProcessor.dll");
Процессор = Новый ПарсерYAML;

// Нижеследующий текст будет преобразован в массив строк
СтрокаYaml = "
|--- # Favorite movies
| - Casablanca
| - North by Northwest
| - The Man Who Wasn't There";

ОбъектыМассив = Процессор.ПрочитатьYaml(СтрокаYaml);

Для Каждого ЭлементМассива Из ОбъектыМассив Цикл
	Сообщить(ЭлементМассива);
КонецЦикла;

// Нижеследующий текст будет преобразован в соответствие
СтрокаYaml = "---
|a: 123                     # an integer
|b: ""123""                 # a string, disambiguated by quotes
|c: 123.0                   # a float
|d: !!float 123             # also a float via explicit data type prefixed by (!!)
|e: !!str 123               # a string, disambiguated by explicit type
|f: !!str Yes               # a string via explicit type
|g: True                     # a boolean True (yaml1.1), string ""Yes"" (yaml1.2)
|h: Yes we have No bananas  # a string, ""Yes"" and ""No"" disambiguated by context.
|...";

ОбъектыСоответствие = Процессор.ПрочитатьYaml(СтрокаYaml);

Для Каждого ЭлементСоответствия Из ОбъектыСоответствие Цикл
	Сообщить(ЭлементСоответствия.Ключ + " | " + ЭлементСоответствия.Значение);
КонецЦикла;


```

## Установка

Для установки необходимо: 
- Со страницы релиза проекта
    * Скачать файл yaml*.ospx из раздела [releases](https://github.com/khorevaa/yaml/releases)
    * Воспользоваться командой:

    ```
    $ opm install -f <ПутьКФайлу>
    ```
- Через публичный пакетный менеджер `opm`
    ```
    $ opm install yaml
    ```