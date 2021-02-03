# Simple Kubernetes lab

This lab consist of 3 virtual machines:

- Control-plane: Running all administrative tasks and apis
- 2 Workers: Running pods

I provisioned this lab using Ansible in a simples way, without much work on the roles definitions or preparations for multiple OS distros, at the moment it will only works on Debian 10 (Buster). 
