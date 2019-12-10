Kyball Project

This project sets up a Django web application that allows users to query a database for baseball players.
The query should return nice visuals showing relevant stats of the player. The main triumph of this project,
however, is that all of the infrastructure is IaC: 'Infrastructure as Code'. 

What all happens?

Good question.

First, Terraform spins up an RHEL EC2 instance (with user data script), an AWS RDS MySQL instance, and appropriate security groups to only let the EC2 instance access the MySQL database.

Second, the user data performs a Git pull from this repo to gain the csv files for the baseball data as well as some installations like Python, pip, etc.. The script ends with a call to a python module 'write_to_sql_from_ec2.py' with options dynamically populated from Terraform. This module performs all of the write operations on the MySQL database.

Requirements:
	-AWS account with CLI setup
	-Terraform properly installed