### **Deployment Instructions**

1. **Save the file** as `ubuntu-vm.yaml`
2. **Create the stack using AWS CLI:**
   ```sh
   aws cloudformation create-stack --stack-name UbuntuStack --template-body file://ubuntu-vm.yaml --capabilities CAPABILITY_NAMED_IAM
   ```
3. **Check stack status:**
   ```sh
   aws cloudformation describe-stacks --stack-name UbuntuStack
   ```
4. **Find the public IP:**
   ```sh
   aws cloudformation describe-stacks --stack-name UbuntuStack --query "Stacks[0].Outputs[?OutputKey=='InstancePublicIp'].OutputValue" --output text
   ```
5. **SSH into the instance:**
   ```sh
   ssh -i jv.pem ubuntu@<PUBLIC_IP>
   ```
