## Tomcat
docker run -it --rm -p 8080:8080 tomcat:8.0

## Oracle
docker run -d -it --name myoracle store/oracle/database-enterprise:12.2.0.1
docker exec -it myoracle bash
sqlplus sys/Oradoc_db1@ORCLCDB as sysdba