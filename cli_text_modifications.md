# sed command sage


```shell
sed -r -n -e '/232476/p' 2022-08-23_admin_mysql_test_update.log > logs.log
```

- output to file 
- search and keep all lines with string rest ignored


# ex command usage

```shell
ex -sc '%s/\(\Nayak\).*/\1/ | x' sql_logs_copy.log
```

- crop all line contents till end from given string
