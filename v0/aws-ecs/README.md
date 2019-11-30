# Install Docker container in an AWS-ECS ecs_cluster

## Pre-Reqs

An EC2 User with high level admin rights.

Set environment Variables:

```
export AWS_ACCESS_KEY_ID={KEY_ID}
export AWS_SECRET_ACCESS_KEY={SECRET}
```

### AWS VPC & cluster

Run the 'infra' playbook and `ecs-ecr` role in the project [ansible.ec2.solveapuzzle](https://github.com/npiper/ansible.ec2.solveapuzzle) to create a VPC and ECS Cluster.

## Running a deploy

```
ansible-playbook -vvv -i ./DEV/allvars ecs-restreference.yml
```
