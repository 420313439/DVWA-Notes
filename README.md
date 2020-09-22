# DVWA-Notes

## Command Injection
防御方法：用白名单仔细检查每一个输入的字符，例如输入的是IPv4地址，确保每一个字符都是整型。

## CSRF
防御方法：加上CSRF_TOKEN；若有改密码，要求输入原密码。

## File Inclusion
防御方法：1、PHP:关闭allow_url_include和allow_url_fopen；2、谨慎使用include()、include_once()、require()、require_once()等函数，用硬编码来包含，不允许输入，或用白名单过滤输入。
