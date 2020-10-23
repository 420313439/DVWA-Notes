# DVWA Notes

## Command Injection
防御方法：用白名单仔细检查每一个输入的字符，例如输入的是IPv4地址，确保每一个字符都是整型。  

## CSRF
防御方法：加上CSRF_TOKEN；若有改密码，要求输入原密码。   

## File Inclusion  
防御方法：  
1、关闭php.ini中的allow_url_include和allow_url_fopen；  
2、使用include()、include_once()、require()、require_once()等函数时，用硬编码来包含，不允许输入，或用白名单过滤输入。  

## SQL Injection
防御方法：参数化查询  
```php
if(is_numeric( $id )) { 
    $data = $db->prepare('SELECT first_name, last_name FROM users WHERE user_id = (:id) LIMIT 1;');
    $data->bindParam(':id', $id, PDO::PARAM_INT);
    $data->execute()
}
```

## Weak Session IDs
防御方法：cookie随机生成，时间限制，域限制，HttpOnly
```php
$cookie_value = sha1(mt_rand() . time() . "Impossible");
setcookie("dvwaSession", $cookie_value, time()+3600, "/vulnerabilities/weak_id/", $_SERVER['HTTP_HOST'], true, true);
```

## XSS
防御方法：
```php
htmlspecialchars(string);
```
