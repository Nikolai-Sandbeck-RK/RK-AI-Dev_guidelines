# SqlPackage - Guidelines 

## Installér SqlPackage 

OBS: tjek gerne Microsofts egen side for opdaterede links der skal bruges med curl. 


1) Prereqs
```bash
sudo apt-get update
sudo apt-get install -y unzip libunwind8
```

2) Download the latest Linux build (evergreen link from Microsoft) 

```bash
mkdir -p ~/sqlpackage && cd ~/sqlpackage
```
```bash
curl -L https://aka.ms/sqlpackage-linux -o sqlpackage-linux.zip
```bash

3) Unzip and make it runnable

```bash
unzip -o sqlpackage-linux.zip
```
```bash
chmod +x ./sqlpackage
```

4) Put it on your PATH

```bash
echo 'export PATH="$HOME/sqlpackage:$PATH"' >> ~/.bashrc
```
```bash
source ~/.bashrc
```

5) Verify 
```bash
which sqlpackage
```
```bash
sqlpackage /?
```

## Tag backup af databasen 

Tag backup af databasen, og gem den lokalt. Dette backup kan puttes ind i en Docker instance som du kan pege prisma imod. På den måde kan du bruge dit lokale kopi af databasen, og du behøver ikke bekymrer dig om at ødelægge noget. 


I bash terminalen skal du køre følgende: 
 
OBS: skift placeholders ud med rigtige credentials 

```bash
sqlpackage /a:Export \
  /ssn:"tcp:rodovre-ai-db.database.windows.net,1433" \
  /sdn:"<db_name>" \
  /su:"<db_username>" \
  /sp:"<db_password>" \
  /tf:"<Din sti til backup>/Database_copy_$(date +%F).bacpac"
```

/a:Export = export action

/ssn = server name

/sdn = source database name

/tf = output file path (on your WSL / Linux filesystem)


Du skulle gerne nu se noget i dur med

```bash
Connecting to database 'DB_NAME' on server '<your-server>.database.windows.net,1433>'.
Extracting schema
Extracting schema from database
Resolving references in schema model
Validating schema model
Validating schema model for data package
Validating schema
Processing tables for data extraction
Exporting data from database
Exporting data
Processing Export.
Processing Table '[dbo].[Agent]'.
Processing Table '[dbo].[Message]'.
Processing Table '[dbo].[_RoleToUser]'.
Processing Table '[dbo].[Chat]'.
Processing Table '[dbo].[VerificationToken]'.
Processing Table '[dbo].[Role]'.
Processing Table '[dbo].[DriveFile]'.
Processing Table '[dbo].[Account]'.
Processing Table '[dbo].[User]'.
Processing Table '[dbo].[Document]'.
Processing Table '[dbo].[Session]'.
Processing Table '[dbo].[_prisma_migrations]'.
Processing Table '[dbo].[ExternalApplication]'.
Successfully exported database and saved it to file '<Din sti til backup>/Database_copy_2025-09-04.bacpac'.
```

 

 

 