To find unused ENIs for Glue  - 

aws ec2 describe-network-interfaces --region us-west-2 | jq -r '.NetworkInterfaces[] | select(.Description | startswith("Attached to Glue using")) | .NetworkInterfaceId'


Here is an easy CLI command that I have formed which will lists all the private addresses in a subnet. 

aws ec2 describe-network-interfaces --region <region> --output text --query 'NetworkInterfaces[?SubnetId==`<subnet-id>`].PrivateIpAddresses[*].PrivateIpAddress'

Replace <region> and <subnet-id> with your region and subnet-id.
