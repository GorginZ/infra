BASIC VPC AND NETWORKING

this dir includes

VPC

2 public and 2 private subnets across respective AZs (TODO add 3rd)

NAT gateways -> private subnet nats route 0.0.0.0/0 to public subnet NATs

public NATs -> 0.0.0.0/0 to VPC internet gateway.

there are restrictive NACLs and VPC endpoints which are causing me grief and I am dumping this in this repo bc I will emove them for the current use case.

I am trying to engineer this so that no traffic comes IN to my private subnets directly, but am stuck because when the compute instances initialise they need to call AWS services (I have tried setting up s3, 2 respective ecr and SSM and autoscaling endpoints but am struggling with the tuning)

probably for the SSM agent I should bake that into the image

AUTOSCALING GROUP

TARGET GROUP

SCALING RULES (that will need to be tuned to use case)

architecture approximates:

< put image here >