Installing AWS Systems Manager Agent (SSM Agent)

Line # 31 of .yml file needs to be edited with your 'CODE' 'ID' 'REGION'

These are the steps:

# Create a temporary directory on the on-premise-instance.
mkdir /tmp/ssm

# Change to the temporary directory.
cd /tmp/ssm

# Download SSM installer.
curl https://s3.amazonaws.com/ec2-downloads-windows/SSMAgent/latest/linux_amd64/amazon-ssm-agent.rpm -o /tmp/ssm/amazon-ssm-agent.rpm

# Then run the SSM installer.
yum install -y /tmp/ssm/amazon-ssm-agent.rpm

# Stop the agent before registration
service amazon-ssm-agent stop

# Register the instance using the CODE and REGION generated by the Activation
amazon-ssm-agent -register -code "CODE" -id "id" -region "REGION"

# Start the agent
service amazon-ssm-agent start
