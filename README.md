# regex-snippets

### Find spaces outside double quotes

**Regex expression**
```
\s+(?=(?:[^"]*"[^"]*")*[^"]*$)
```

#### Usage example: convert search string to full-text query for PostgreSQL 

```
select replace(regexp_replace('some search terms "and terms inside double quotes" and few additional "double quoted words" examples', '\s+(?=(?:[^"]*"[^"]*")*[^"]*$)', ' & ', 'g'), '"', '''');
```

...converts input parameter 
`some search terms "and terms inside double quotes" and few additional "double quoted words" examples`
to string that can be directly used for `to_tsquery` function:
`some & search & terms & 'and terms inside double quotes' & and & few & additional & 'double quoted words' & examples`.
