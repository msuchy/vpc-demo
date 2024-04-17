1. Create VPC
   - vpc-meg-test 10.0.0.0/16
2. Create Subnets
   - sb-public 10.0.0.0/24
   - sb-pvt-app 10.0.12.0/22
   - sb-pvt-resources 10.0.4.0/23
3. Create Internet Gateway
4. Attach igw-meg-test to vpc-meg-test
5. Create Route Table
   - rt-public
6. Add route to rt-public
   - 0.0.0.0/0 -> igw-meg-test
7. Attach rt-public to sb-public
8. Create Route Table
   - rt-private
9. Attach rt-private to sb-pvt-app
10. Attach rt-private to sb-pvt-resources
11. Create nat-gateway on sb-public
   - nat-meg-test
   - public connectivity
12. Add route to rt-private
   - 0.0.0.0/0 -> nat-meg-test
13. Add security group
   - meg-test
   - IN
      - TCP 23
      - ICMP all
   - OUT
      - HTTP
      - HTTPS
14. Launch EC2 jump box on sb-public
    - sg -> meg-test
    - Auto assign public ip

    - telnet is not installed by default on AMI

    - connect throught ssh

      - ssh -i "meg.pem" ec2-user@3.91.198.190

      - sudo yum install telnet-server
      - sudo systemctl start telnet.socket
      - sudo systemctl enable telnet.socket
      - sudo systemctl status telnet.socket

15. Launch EC2 on sb-pvt-app
    - sg -> boti-test
    - private ip




    -- enable password
    https://comtechies.com/password-authentication-aws-ec2.html
