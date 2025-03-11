# Домашнее задание к занятию «Инструменты Git». Щербаков А.А

------

## Задание

В клонированном репозитории:

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.

- полный хеш коммита aefead2207ef7e2aa5dc81a34aedf0cad4c32545
- комментарий "Update CHANGELOG.md"

```git
git show aefea
```

2. Ответьте на вопросы.

- Какому тегу соответствует коммит `85024d3`?

Ответ:
v0.12.23

- Сколько родителей у коммита `b8d720`? Напишите их хеши.

Ответ:
parent 56cd7859e05c36c06b56d013b55a252d0bb7e158
parent 9ea88f22fc6269854151c571162c5bcf958bee2b

```git
git cat-file -p b8d720
git show --pretty=raw b8d720
```

- Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами  v0.12.23 и v0.12.24.

```output
git log v0.12.23..v0.12.24 --oneline 
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release
```

- Найдите коммит, в котором была создана функция `func providerSource`, её определение в коде выглядит так: `func providerSource(...)` (вместо троеточия перечислены аргументы).

Ответ:

```output
git log -S'func providerSource' --oneline
find -type f -name 'rovider_source.go'
git blame ./provider_source.go | grep 'func providerSource'
```

5af1e6234ab6da412fb8637393c5a17a1b293663 main: Honor explicit provider_installation CLI config when present

- Найдите все коммиты, в которых была изменена функция `globalPluginDirs`.

Ответ:

```output
git grep --show-function "GlobalPluginDirs"
git log -L :GlobalPluginDirs:internal/command/cliconfig/plugins.go 
7c4aeac5f30aed09c5ef3198141b033eea9912be

```

- Кто автор функции `synchronizedWriters`?

Ответ:

Первый коммит: 5ac311e2a9  
Автор: Martin Atkins

```git
git log -S"func synchronizedWriters(" --pretty=format:'%h %an %ad %s'
```
