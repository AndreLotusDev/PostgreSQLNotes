---
aliases: 
tags: 
date created: Sunday, February 9th 2025, 4:20:21 pm
date modified: Sunday, February 9th 2025, 4:20:40 pm
---
```sql
DO $$
DECLARE
    affected_rows INTEGER;
BEGIN
    -- Run the UPDATE statement.
    UPDATE your_table
    SET some_column = 'new_value'
    WHERE some_condition;

    -- Get the number of rows updated.
    GET DIAGNOSTICS affected_rows = ROW_COUNT;
    
    -- If more than one row is affected, raise an exception.
    IF affected_rows > 1 THEN
        RAISE EXCEPTION 'Update affected % rows, which is more than the allowed single row', affected_rows;
    END IF;
    -- If exactly one row was updated (or zero, if that’s acceptable), the transaction will complete normally.
END $$;
```