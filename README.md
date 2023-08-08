# sas-9.4
Uzitecne prikazy k SAS 9.4 administraci

# zapnutí nebo vypnutí služeb

/sas/sasconfig/Lev1/sas.servers start/stop /status

# zapnutí metadata serveru

/sas/sasconfig/Lev1/SASMeta/MetadataServer/MetadataServer.sh start

# vypíše produkty co je na serveru nainstalovany

/sas/sashome/InstallMisc/InstallLogs/DeploymentRegistry.txt+ - 

# Vygeneruje nové DeploymentRegistry.txt 

cd /sas/sashome/deploymntreg/
java -jar sas.tools.viewregistry.jar


# Zkopírování dat z jednoho serveru na druhý
scp sas-security-update-2023-03-M7.zip sas@sas01prod.id.prod:/sas/sashome/InstallMisc/HotFixes/SecurityUpdates/

# Jak spouštět SAS 9.4 služby ve správném pořadí

Začít na 01 serveru meta data

1: 
/sas/sasconfig/Lev1/sas.servers.pre start / status / stop

2:
Zapnout SAS Metadata Server
a pak 
/sas/sasconfig/Lev1/sas.servers.mid start

teď se dají zapnout 02 a 03 servery a pak už 

3:
/sas/sasconfig/Lev1/sas.servers.mid start

# V případě že neprojde Redeploy web app, tak zkusit pročistit cache a logy - udělat pak redeploy znovu
použít Viktor_Cistic.sh

# po Redeployi pokud nejede server zkontrolovat logy /logs/SASServer1_1/ atd (další servery/appky) 
catalina.out a server.log
less /logs/SASServer1_1/server.log

# Diagnostika RTDM
rtdm04prod.in.prod:8343/RTDM/Diagnostics.jsp
