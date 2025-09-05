# Guide til at komme i gang med sqlcmd 

## Installation af sqlcmd 

Sqlcmd bør installeres ude for dit kodemiljø.  

1. Start 

Hvis du bruger WSL2 + ubuntu: 

Åbn powershell og skriv "ubuntu" for at starte WSL2 + Ubuntu. 

Hvis du bruger Linux, så blot åbn en ny terminal.


2. Følg [Microsofts installationsinstrukser](https://learn.microsoft.com/en-us/sql/tools/sqlcmd/sqlcmd-download-install?view=sql-server-ver17&tabs=linux)

Når du har importeret GPG keys, vil du få sådan en meddelelse her:

```bash
cn33760@cn33760-carbon1:~$ curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc [sudo] password for cn33760: % Total % Received % Xferd Average Speed Time Time Time Current Dload Upload Total Spent Left Speed 100 975 100 975 0 0 1375 0 --:--:-- --:--:-- --:--:-- 1375

Sorry, try again. [sudo] password for cn33760: -----BEGIN PGP PUBLIC KEY BLOCK----- Version: BSN Pgp v1.1.0.0 

mQENBFYxWIwBCADAKoZhZlJxGNGWzqV+1OG1xiQeoowKhssGAKvd+buXCGISZJwT LXZqIcIiLP7pqdcZWtE9bSc7yBY2MalDp9Liu0KekywQ6VVX1T72NPf5Ev6x6DLV 7aVWsCzUAF+eb7DC9fPuFLEdxmOEYoPjzrQ7cCnSV4JQxAqhU4T6OjbvRazGl3ag OeizPXmRljMtUUttHQZnRhtlzkmwIrUivbfFPD+fEoHJ1+uIdfOzZX8/oKHKLe2j dfgfdgdfgdfHJKLMKLSNMLBASBJHABVSGHV GHhARXWiP8Q5teL/t5TUH6TZ3B ENboDjwr705jLLPwuEDtPI9jz4kvdT86JwwG6N8gnWM8Ldi56SdJEtXrzwtlB/Fe 6tyfMT1E/PrJfgALUG9MWTJHJKLDNKJNDN++!Q""gVnscbN0PE19KK9 nPsBxyK4wW0AvAhed2qldBPTipgzPhqB2gu0jSryil95bKrSmlYJd1Y1XfNHno5D xfn5JwgySBIdWWvtOI05gw== =zPfd -----END PGP PUBLIC KEY BLOCK----- 
```

Dette er ikke en error, det betyder faktisk, er det er kørt med success. 

 
## Forbind til en database 

For at logge ind på sql-serveren, kør nu: (PS. dette peger mod testdatabasen) 

```bash
sqlcmd -S tcp: ' <server> ',1433 –U ' <db_username> ' -P '<db_password>' -d <db_database_name>
```

OBS, feltet server, username, password og database, kan du finde i .env filerne hvor der står DATABASE_URL 

Når linjen er kørt, skulle der gerne står `1>` i terminalen. 

Du kan nu bruge SQL-kommandoer.

1. Indtast dine kommandoer
2. tryk `ENTER`
3. skriv nu `GO` i terminalen og tryk `ENTER` igen for at eksekvere dine kommandoer. 

PS: du kommer ud af sqlcmd ved at skrive `QUIT`
 

TODO: når https://dev.azure.com/droidsagency/Rodovre-AI/_git/Rodovre-AI/pullrequest/1034 er godkendt og merget, skal der bare henvises til at bruge scriptet start_sqlcmd.py 


## Tjek om du har back up rettigheder 
 
Når du er i sqlcmd, skal skrive følgende SQL-kode.

```sql
SELECT HAS_PERMS_BY_NAME(DB_NAME(), 'DATABASE', 'BACKUP DATABASE');
```

Kør nu kommandoen `GO` for at køre koden. 

 