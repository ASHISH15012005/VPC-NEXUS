# AWS Custom VPC Setup Guide

## Logging in as an IAM User or Root User
1. Go to [AWS Console](https://aws.amazon.com/).
2. Click on the **Sign in to the console** button at the top right.
3. If you have used an AWS account before, you will see the IAM user login page by default.
4. Enter your credentials and log in.

---

## Creating a Custom VPC
1. Select the region where you want to run your VPC (VPCs are region-based).
2. For this demonstration, we select **Mumbai (ap-south-1)**.
3. Navigate to **VPC Dashboard** > Click on **Create VPC**.
4. Select **VPC only** under the "Resource to create" section.
5. Give the name **"My Custom VPC"**.
6. Leave the **IPv4 CIDR manual input** as default.
7. To choose your own CIDR range, use a CIDR calculator.
8. Under **Networking Address**, leave it as is.
9. For **Mask Bits**, enter **22** and click **Update**.
10. Note down the assigned IPs.
11. Enter the CIDR range and click **Update**.
12. Your interface should now match the preview before clicking **Create VPC**.
13. Click **Create VPC**.

---

## Creating Subnets
1. Navigate to **Subnets** under "Your VPCs".
2. Click on **Create Subnets**.
3. Select the **VPC ID** that we created earlier.
4. Under **Subnet Settings**:
   - Enter **Subnet Name** as **Public Subnet 1A**.
   - Set **Availability Zone** to **ap-south-1a**.
   - Provide the **IPv4 Subnet CIDR block** as per the noted IPs.
5. Click **Add new Subnet** and repeat for three additional subnets:
   - **Two private subnets**
   - **One additional public subnet**
6. Click **Create Subnets**.

---

## Assigning an Internet Gateway
1. Navigate to **Internet Gateways** under the VPC dashboard.
2. Click on **Create Internet Gateway**.
3. Provide the name **"Custom Gateway 1"**.
4. Click **Create Internet Gateway**.
5. After creation, click on **Actions** > **Attach to VPC**.
6. Select the **Custom VPC** we created earlier.

---

## Assigning Subnets and Internet Gateway in Route Tables
1. Navigate to **Route Tables**.
2. Click on **Create Route Table**.
3. Provide the name **"Private Subnet"** and select the VPC.
4. Click **Create Route Table**.
5. Go to **Subnet Associations** and select the private subnets.
6. Repeat the same steps for public subnets, naming the route table **"Public Subnet"**.
7. Open the **Public Subnet** route table.
8. Under **Routes**, click **Edit Routes**.
9. Click **Add Route**:
   - **Destination**: `0.0.0.0/0` (allows all outbound traffic).
   - **Target**: Select the **Internet Gateway** created earlier.
10. Click **Save Changes**.

---

## Clearing All Resources
1. Navigate to **VPCs**.
2. Select the VPC created earlier.
3. Under **Actions**, select **Delete**.
4. Type **delete** to confirm and permanently remove all resources.

---

## Output
- We have successfully created a **Custom VPC** with **two subnets**.
- These subnets can now be used for launching **EC2 instances**.
- The **Public Subnet** (in the route table) is connected to the **Internet Gateway**.
- The **Private Subnet** (in the route table) has no internet access.

---

## Why Did We Attach an Internet Gateway to the Public Subnet?
A common question for new VPC users and cloud enthusiasts:
- By attaching an **Internet Gateway** to a **VPC** and associating it with a **Route Table**, instances in the **Public Subnet** can communicate with the internet.
- This is essential for applications needing internet access (e.g., web servers).
- The **Internet Gateway** enables outbound and inbound traffic to and from the internet.

---

## Need Help?
If you have any doubts, feel free to connect with me:
- **LinkedIn**: [Ashish Kodumuru](https://www.linkedin.com/in/ashishk169/)
- **Email**: kodumuruashish15012005@gmail.com
---

# Documentation
For detailed step by step live demonstration you can refer [here](https://aws-x-vpc-custom-vpc.hashnode.dev/aws-networking-module)
