sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql.service
sudo systemctl status postgresql.service
sudo -i -u postgres
psql
createuser --interactive
sudo -u postgres createuser --interactive
createdb tryton
sudo -u postgres createdb tryton

/etc/postgresql/<version>/main/postgresql.conf
listen_addresses = '*'

/etc/postgresql/<version>/main/pg_hba.conf
# TYPE  DATABASE        USER            ADDRESS                 METHOD
host    all             all             <client_ip_address>     <authentication_method>
host    all             all             0.0.0.0/0               md5

CREATE DATABASE trytondb;
CREATE USER trytonuser WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE trytondb TO trytonuser;


db_uri = postgresql://trytonuser:your_password@localhost:5432/trytondb
trytond-admin -c /path/to/trytond.conf --all
trytond -c /path/to/trytond.conf

Open a web browser and enter the Tryton server URL. By default, it is http://localhost:8000.



