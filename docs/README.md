# Defacto2 Data Exports

![Website](https://img.shields.io/website/https/defacto2.net/sql?label=daily%20data%20dumps&style=flat-square)
![MySQL](https://img.shields.io/badge/mysql-5.7-blue?style=flat-square)

### Daily MySQL dumps:

Defacto2 has daily dumps of the MySQL 5.7 database for download.

### Insert

Daily dump that includes `DROP` `TABLE`, `CREATE TABLE` and `INSERT` statements, to replace all existing tables + data.

[d2-sql-insert.sql](https://defacto2.net/sql/d2-sql-insert.sql) <small>([sha1](https://defacto2.net/sql/d2-sql-insert.sql.sha1))</small>

### Update

Daily dump that uses `REPLACE INTO` statements to update any existing data.

[d2-sql-update.sql](https://defacto2.net/sql/d2-sql-update.sql) <small>([sha1](https://defacto2.net/sql/d2-sql-update.sql.sha1))</small>

### Backups

Backup SQL data dumps are also available for download: https://defacto2.net/sql/

---

### Licence

The data and these exports are under a [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/) licence.

---

### How to use the SQL

You need a preconfigured and running database server that can handle MySQL 5.7 syntax. Any of these database applications are suitable.

- [MySQL Community Server](https://dev.mysql.com/downloads/mysql/5.7.html) 5.7
- [Percona Server](https://www.percona.com/doc/percona-server/5.7/index.html) 5.7 *
- [MariaDB](https://mariadb.com) 10.2+ *

<small>* Is a drop in replacement for MySQL 5.7</small>

##### In a terminal use the MySQL client to import the data:

```bash
# download the database
wget https://defacto2.net/sql/d2-sql-insert.sql

# import the data to the mysql database using the database root account.
mysql -u root < d2-sql-insert.sql
```

I recommend using [Adminer](https://www.adminer.org) for data browsing and management, though [DBeaver Community](https://dbeaver.io) also works fine.

---

### Datasets

The data is broken down into three tables, `files`, `groups` and `netresources`

- `files` form the core of the site and compose of nearly 18,000 rows of hosted data.
- `groups` comprise of only initialisms and acronyms for scene groups.
- `netresources` are online links to other scene resources, usually websites.

#### files

| Column | Description | Example |
| --- | --- | --- |
| id | Primary key | 8968 |
| uuid | Unique identifier used as the stored file and images name | b826e39b-66c6-4929-8e5a-f59b07ffaa00 |
| list_relations | List of associated Defacto2 records | Alternative;a84626 |
| web_id_github | Github repository Id | |
| web_id_youtube | YouTube video Id | |
| web_id_pouet | Pouët record Id | |
| web_id_demozoo | Demozoo record Id | 158448 |
| group_brand_for | Group or brand authorship | The Dream Team |
| group_brand_by | Group or brand authorship | |
| record_title | Production title or magazine issue | Midwinter II |
| date_issued_year | Published year | 1992 |
| date_issued_month | Published month | 3 |
| date_issued_day | Published day | 26 |
| credit_text | Writing credits | |
| credit_program | Programming credits | |
| credit_illustration | Artist credits | |
| credit_audio | Composer credits | |
| filename | Filename of the download | MID2TDT1.ZIP |
| filesize | Size of the download | 30923 |
| list_links | List of associated URLs | |
| file_security_alert_url | A URL to the results of a virus scan | |
| file_zip_content | List of files and directories contained in the download archive | DREAM.NFO INTRO.EXE MUSIC TEXT |
| file_magic_type | File type metadata | Zip archive data, at least v1.0 to extract |
| preview_image | The name of a file within the archive that was used as a screenshot | |
| file_integrity_strong | SHA386 hash value of the download | 22370b5e81... |
| file_integrity_weak | MD5 hash value of the download |c00fccc640... |
| file_last_modified | Last modified date value of the download | 2017-03-19 05:49:14 |
| platform | Computer platform tag | dOS |
| section | Category tag | releaseadvert |
| comment | Description of the download | |
| deletedat | When this record was disabled | |
| deletedby | The id of the account which disabled this record | |
| createdat | When this record was created | 2014-10-13 12:08:52 |
| dosee_run_program | Program filename to run in DOSee, the MS-DOS emulator | |
| retrotxt_readme | The filename of a text file to display in the browser | DREAM.NFO |
| retrotxt_no_readme | Toggle to disable retrotxt_readme | |
| dosee_hardware_cpu | DOSee CPU emulation selection | 486 |
| dosee_hardware_graphic | DOSee graphic card selection | vga |
| dosee_hardware_audio | DOSee audio card selection | covox |
| dosee_no_aspect_ratio_fix | DOSee aspect-ratio toggle | |
| dosee_incompatible | Flag this record as incompatible with DOSee | |
| dosee_no_ems | DOSee Expanded memory toggle | 1 |
| dosee_no_xms | DOSee Extended memory toggle | 1 |
| dosee_no_umb | DOSee Upper memory toggle | 1 |
| dosee_load_utilities | Load DOSee utilities | |
| updatedby | The id of the account which updated this record | ADB7C2BF-7221-467B-B813-3636FE4AE16B |
| updatedat | When this record was last updated | 2017-03-19 05:57:12 |

##### groups

| Column | Description | Example |
| --- | --- | --- |
| id | Primary key | 9 |
| pubname | Unique group id | Razor 1911 |
| initialisms | Acronym or initialism value | RZR |

##### netresources

| Column | Description | Example |
| --- | --- | --- |
| id | Primary key | 675 |
| uuid | Unique identifier | 6c43b299-d7da-4670-a687-70c642b3a33e |
| legacyid | Callback to the original database used by Defacto2 | |
| httpstatuscode | HTTP code results from a ping | 200 |
| httpstatustext | HTTP text results from a ping | OK |
| httplocation | Unused | |
| httpetag | HTTP etag result that's used for cache | |
| httplastmodified | HTTP lastmodified result that's used for cache | |
| metatitle | Title metatag | Demozoo |
| metadescription | Description metatag | |
| metaauthors | Authors metatag | |
| metakeywords | Keywords metatag | |
| uriref | Web address | http://demozoo.org |
| title | Name of the site | Demozoo |
| date_issued_year | Publication year | |
| date_issued_year | Publication month | |
| date_issued_year | Publication day | |
| comment | About this web resource | The world's largest database of scene productions. |
| categorykey | Category tag | cracktro |
| categorysort | Subcategory tag | gallery |
| deletedat | When this record was disabled | |
| deletedatcomment | The reason this record was disabled | |
| createdat | When this record was created | 2016-05-07 20:43:36 |
| updatedat | When this record was last updated | 2017-01-27 22:11:23 |
