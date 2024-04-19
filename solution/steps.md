# Steps

Manual steps to create the proposed solution in AWS.

1. Create VPC
   - vpc-meg-test 10.0.0.0/16
1. Create Subnets
   - sb-public 10.0.0.0/24
   - sb-pvt-app 10.0.12.0/22
   - sb-pvt-resources 10.0.4.0/23
1. Create Internet Gateway - igw-meg-test
1. Attach igw-meg-test to vpc-meg-test
1. Create Route Table
   - rt-public
1. Add route to rt-public
   - 0.0.0.0/0 -> igw-meg-test
1. Attach rt-public to sb-public
1. Create nat-gateway on sb-public
   - nat-meg-test
   - public connectivity
1. Create Route Table
   - rt-private
1. Add route to rt-private
   - 0.0.0.0/0 -> nat-meg-test
1. Attach rt-private to sb-pvt-app
1. Attach rt-private to sb-pvt-resources
1. Create Security Groups
   - public-sg
   - app-sg
   - resources-sg
1. Launch EC2 `jump box` on sb-public
   - sg -> public-sg
   - Auto assign public ip
   - connect throught ssh
      - `ssh -i "my-pem.pem" ec2-user@3.91.198.190`
1. Launch EC2 `app` on sb-pvt-app
   - sg -> spp-sg
   - private ip
1. Launch RDS `meg-db` on sb-pvt-resources
   - sg -> resources-sg
   - private ip
1. Test connectivity
   - Access `jump box` through ssh
   - From `jump box`, access `app` on sb-pvt-app through ssh
      - install postgres client
         - `sudo dnf install postgresql15`
      - connect to postgres
         - `psql --host=meg-db.c9s6gyei0l8h.us-east-1.rds.amazonaws.com --port=5432 --username=postgres --password --dbname=test`
      - create table
         - `create table test (id int, name varchar(20));`
      - list tables
         - `\d`