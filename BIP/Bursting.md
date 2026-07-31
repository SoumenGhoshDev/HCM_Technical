

Bursting Query:

``` SQL

SELECT
trx_number KEY,                                   -- Split by
'Bursting_Layout' TEMPLATE,                       -- Catalog
:xdo_user_report_locale LOCALE,                   -- English (es)
'PDF'                 OUTPUT_FORMAT,              -- PDF,HTML,CSV,RTF,EXCEL
'EMAIL'               DEL_CHANNEL,                -- EMAIL/FAX/FTP/FILE/SFTP/PRINT/WEBDAV
'AR INVOICE_'||trx_number OUTPUT_NAME,            -- Output Name
'apps.soumen@gmail.com'          parameter1, -- To
'apps.soumen@gmail.com'          parameter2, -- CC
'apps.soumen@gmail.com'          parameter3, -- From
'Bursting Program testing'        parameter4, -- Subject
'Dear Customer PFA Attachment'    parameter5, -- Body
'true'                            parameter6, -- Attachment
'Reply-To'                        parameter7, -- Reply to
'apps.soumen@gmail.com'          parameter8  -- Bcc
FROM (
select distinct b.trx_number
from ra_customer_trx_lines_all a,
     ra_customer_trx_all b
where a.customer_trx_id= b.customer_trx_id
and   a.customer_trx_id in (1002,1))

```

Parameter according to Delivery Type:

| Delivery Channel (DELIVERY_CHANNEL) | PARAMETER1                                     | PARAMETER2                                  | PARAMETER3                        | PARAMETER4                          | PARAMETER5                           | PARAMETER6                          | PARAMETER7              |
|-------------------------------------|------------------------------------------------|---------------------------------------------|-----------------------------------|-------------------------------------|--------------------------------------|-------------------------------------|-------------------------|
| EMAIL                               | To: Email Address (e.g., employee@company.com) | CC: Email Address (or comma-separated list) | BCC: Email Address                | Subject Line of the email           | Body Text / HTML Content             | Attachment Name (e.g., Payslip.pdf) | Reply-To: Email Address |
| SFTP / FTP                          | Server Name / Host IP address                  | Username                                    | Password (or Security Token name) | Remote Directory path on the server | Target File Name to create on server | Transfer Mode (ASCII or BINARY)     | Not Used (Leave NULL)   |
| PRINTER                             | Printer Name (as registered in BIP Console)    | Print Tray name (e.g., Tray1)               | Number of Copies (e.g., 1)        | Orientation (PORTRAIT or LANDSCAPE) | Duplex Mode (TRUE or FALSE)          | Page Range (Optional)               | Not Used (Leave NULL)   |
| FAX                                 | Fax Server name / number                       | Telephone Number                            | Recipient Name                    | Cover Page template name            | Not Used (Leave NULL)                | Not Used (Leave NULL)               | Not Used (Leave NULL)   |
| WCC / UCM (WebCenter Content)       | Security Group (e.g., FAEnterprise)            | Account Name (e.g., hcm/dataloader)         | Author / User                     | Document Title                      | File Name inside UCM                 | Not Used (Leave NULL)               | Not Used (Leave NULL)   |



https://docs.oracle.com/cd/E24001_01/bi.1111/e18862/T527073T555155.htm
