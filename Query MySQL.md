## Cek Duplicate
```
select txtOkp, txtLotnumber, count(*) as cnt
FROM db_qfg.mstg_pending_lot mpl 
GROUP BY txtOkp, txtLotnumber
HAVING COUNT(*) > 1
ORDER BY cnt DESC
```
## Delete Duplicate
```
DELETE t1
FROM name_table t1
JOIN name_table t2
  ON t1.txtOkp = t2.txtOkp
 AND t1.txtLotnumber = t2.txtLotnumber
 AND t1.id > t2.id;
```
