# Malicious
```sql
SELECT 
    name, 
    type, 
    CASE 
        WHEN description = 'security holding package' THEN NULL
        ELSE description 
    END as description
FROM package
INNER JOIN malicious_packages mp ON mp.package_id = package.id
ORDER BY type, name;
```

# Deprecated
```sql
SELECT 
    name, 
    type, 
    CASE 
        WHEN description = 'security holding package' THEN NULL
        ELSE description 
    END as description
FROM package WHERE is_deprecated
ORDER BY type, name;
```

# Archived
```sql
SELECT 
    package.name, 
    type, 
    CASE 
        WHEN package.description = 'security holding package' THEN NULL
        ELSE package.description 
    END as description
FROM package INNER JOIN repository ON package.repository_id=repository.id AND repository.archived=TRUE
ORDER BY type, name;
```