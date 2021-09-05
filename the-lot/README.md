BASIC VPC AND NETWORKING ASG HTTPS LISTENERS AND COMPUTE INSTANCES THE LOT FINE TUNE AS NEEDED

assumptions for using this quick big VPC with networking and hosting infra stack:

There is manual work involved with anything involving certs and secret management/ params so ->

- I have set up the appropriate values in param store (*the ones that the scripts are calling*)

- have a domain or access to an aws:
- hosted zone
- validated ssl cert (with a CNAME record ALREADY EXISTING in the hosted zone associated with the domain in use)


this dir includes

VPC

2 public and 2 private subnets across respective AZs (TODO add 3rd)

NAT gateways -> private subnet nats route 0.0.0.0/0 to public subnet NATs

public NATs -> 0.0.0.0/0 to VPC internet gateway.

there are restrictive NACLs and VPC endpoints which are causing me grief and I am dumping this in this repo bc I will emove them for the current use case.

I am trying to engineer this so that no traffic comes IN to my private subnets directly, but am stuck because when the compute instances initialise they need to call AWS services (I have tried setting up s3, 2 respective ecr and SSM and autoscaling endpoints but am struggling with the tuning)

probably for the SSM agent I should bake that into the image

SGs for: ASG, also one for the VPC endpoints.

AUTOSCALING GROUP

TARGET GROUP

ALB

Listeners -> http -> https  -> target group

SCALING RULES (that will need to be tuned to use case)

architecture approximates:

< put image here >