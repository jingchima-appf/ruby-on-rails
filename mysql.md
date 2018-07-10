## Start mysql
mysql -u root -p

## Load data into table
- First need to create a table
- Then use 
  ```SQL
    LOAD DATA LOCAL INFILE 'uniq.csv'
    INTO TABLE tblUniq
    FIELDS TERMINATED BY ','
        ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 LINES # ignores header in csv file
  ```
see: https://stackoverflow.com/questions/11077801/import-csv-to-mysql-table
  
## Output table to csv file
```SQL
  SELECT 'ColName1', 'ColName2', 'ColName3' # this is adding headers to csv file
  UNION ALL
  SELECT ColName1, ColName2, ColName3
      FROM YourTable
      INTO OUTFILE '/path/outfile'
      FIELDS TERMINATED BY ','
      ENCLOSED BY '"'
      LINES TERMINATED BY '\n';
```
see: https://stackoverflow.com/questions/5941809/include-headers-when-using-select-into-outfile

## Drop Column
`ALTER TABLE tbl_Country DROP COLUMN IsDeleted;`

see: https://stackoverflow.com/questions/13968494/how-to-delete-a-column-from-a-table-in-mysql
