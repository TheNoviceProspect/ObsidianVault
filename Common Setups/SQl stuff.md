login into a mysql server from linux:
```bash
sudo mysql -u root -p
```
enter the password of the user.

## Changing a users password:
(from: [MySQL Change a User Password Command Tutorial - nixCraft (cyberciti.biz)](https://www.cyberciti.biz/faq/mysql-change-user-password/))
```sql
SET PASSWORD FOR 'user'@'host' = PASSWORD('foobar');
```
(if you enter `%` as a host its a wildcard.)