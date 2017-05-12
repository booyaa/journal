# Miscellany

I always forget how to get AD logon details from Oracle. This is the first time I've used Oracle virtual columns, in my case I've used it to compute the length of a proposed column name (to avoided 30 character length limit in Oracle less than 12c). Finally the `<details>` is too handy to keep forgetting, it can be used very effectively in GitHub to reduce the noise of log files and command output.

## Get AD logon in Oracle

```sql
SELECT
    sys_context('userenv','os_user')
FROM
    dual;
```

## Virtual columns

To quote [ORACLEBASE](https://oracle-base.com/articles/11g/virtual-columns-11gr1):

> When queried, virtual columns appear to be normal table columns, but their values are derived rather than being stored on disc.

Syntax

```sql
column_name [datatype] [GENERATED ALWAYS] AS (expression) [VIRTUAL]
```

## Collapsible sections in SQL

### Demo

<details>
  <summary>Works great in GitHub!</summary>
  <p>Dipshit with a nine-toed woman. Dolor sit amet, consectetur adipiscing elit praesent ac magna. You don’t go out and make a living dressed like that in the middle of a weekday. Justo pellentesque ac lectus quis. Yeah. Roadie for Metallica. Speed of Sound Tour. Elit blandit fringilla a ut turpis praesent felis. Keep your ugly fucking goldbricking ass out of my beach community! Ligula, malesuada suscipit malesuada non, ultrices non urna sed orci ipsum, placerat id.</p>
</details> 

### Code 

```html
<details>
  <summary>Click to expand...</summary>
  <p>Imagine this is the entire text of War and Peace.</p>
</details> 
```

## Toggling hidden files in Finder (OSX)

If you search for how to do this, you get a lot of nonsense involving messing with `defaults write` and horrific applescript bodges.

`CMD` + `SHIFT` + `.`

That's command key, shift and full stop (period) pressed at the same time.