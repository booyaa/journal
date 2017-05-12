# Crap I've been holding onto in my SO favs

## Windows command stdout and stderr redirection

```dos
dir > a.txt 2>&1
```

This is identical to Linux/OSX redirection.

## List active/open connections in Oracle

```sqlpl
SET LINESIZE 200
COL pid FORMAT a9
COL sid FORMAT a5
COL ser# FORMAT a5
COL box FORMAT a6
COL username FORMAT a10
COL os_user FORMAT a8
COL program FORMAT a30
COL terminal FORMAT a30

SELECT
    substr(a.spid,1,9) pid,
    substr(b.sid,1,5) sid,
    substr(b.serial#,1,5) ser#,
    substr(b.machine,1,6) box,
    substr(b.username,1,10) username,
    substr(b.osuser,1,8) os_user,
    substr(b.program,1,30) program,
    b.terminal
FROM
    v$session b,
    v$process a
WHERE
    b.paddr = a.addr
AND
    type = 'USER'
ORDER BY spid;
```

## XML node() vs. text()

There are all kinds of [node tests][1]:

- `node()` matches *any* node (the least specific node test of them all)
- `text()` matches *text* nodes only
- `comment()` matches *comment* nodes
- `*` matches any *element* node
- `foo` matches any element node named `"foo"`
- `processing-instruction()` matches PI nodes (they look like `<?name value?>`).
- *Side note:* The `*` also matches attribute nodes, but only along the `attribute` axis. `@*` is a shorthand for `attribute::*`. Attributes are not part of the `child` axis, that's why a normal `*` does not select them.

  
  [1]: http://www.w3.org/TR/xpath/#node-tests

Source: http://stackoverflow.com/a/11744783/105282

## Searching a list in Lua

```lua
local items = { "apple", "orange", "pear", "banana" }

for _,v in pairs(items) do
  if v == "orange" then
    -- do something
    break
  end
end
```

## Rounding to midnight

```sql
SELECT getdate() AS now
	,cast(getdate() - 6 AS DATE) AS sql2008
	,dateadd(day, datediff(Day, 0, getdate() - 6), 0) AS sql2005
```
