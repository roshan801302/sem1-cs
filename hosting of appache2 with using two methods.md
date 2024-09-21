# Hosting a Website on AWS with Apache2 Using PowerShell
### (These are the steps after launching instance and downloading .pem passkey)<br>
## Step 1: Connect to EC2 Instance Using PowerShell
1. Open **PowerShell** in Windows.
2. Navigate to your PEM file:
First, ensure you’re in the directory where your .pem file is located.
Use cd to change directories:
```bash
cd path\to\your-pem-file
```
4. Use the `ssh` command to connect to your EC2 instance:
   ```bash
   ssh -i "path_to_your_key.pem" ec2-user@your_instance_public_IP
Replace path_to_your_key.pem with the location of your private key.
Replace your_instance_public_IP with the public IP of your EC2 instance.
## Step 2: Update the Package List on Your EC2 Instance
Run the following command after logging in to update your packages:
```bash
sudo apt update
```
## Step 3: Install Apache2
To install the Apache2 web server:
```bash
sudo apt install apache2 -y
```
## Step 4: Delete the Default index.html and Create Your Own
Navigate to the Apache web directory:
```bash
cd /var/www/html
```
1. Delete the default index.html file:
```bash
sudo rm index.html
```
2. Create a new index.html file:
```bash
sudo vi index.html
```
### Add your website's HTML content and save the file.

## YAY! Your link or IP adress of your instance will now work. <br><br><br>
# Hosting a Website on AWS with EC2, Apache2, and PuTTY

## Step 1: Launch a Linux EC2 Instance (Ubuntu)

1. **Login to AWS Console**:
   - Go to [AWS Console](https://aws.amazon.com/console/) and log in.

2. **Launch EC2 Instance**:
   - Navigate to **EC2** and click **Launch Instance**.

3. **Choose an AMI (Amazon Machine Image)**:
   - Select **Ubuntu Server**

4. **Choose Instance Type**:
   - Pick **t2.micro**

5. **Configure Security Group**:
   - Create a security group with the following inbound rules:
     - **SSH** (port 22)
     - **HTTP** (port 80)

6. **Key Pair**:
   - Create a new key pair and download the `.ppk` file.

7. **Launch the Instance**.

---

## Step 2: Connect to EC2 Using PuTTY

1. **Open PuTTY**.

2. **Enter the Public IP of EC2**:
   - In **Host Name (or IP address)**, enter your instance's **public IP**.
   - Example: `eg. (13.45.589.25)`

3. **Load PPK File**:
   - In the left sidebar, navigate to **Connection > SSH > Auth**.
   - Click **Browse** and select the `.ppk` file.

4. **Open the Connection**:
   - Click **Open** and use `ubuntu` as the username when prompted.

---

## Step 3: Install Apache2 on the EC2 Instance

Update the package list and install Apache2:
```bash
sudo apt update
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2
```

## Step 4: Configure Security Group for HTTP Traffic
Go to EC2 Dashboard > Security Group.

Edit Inbound Rules:

Add a new rule for HTTP on port 80 with Source: Anywhere (0.0.0.0/0).

## Step 5: Delete Default index.html and Create a New One
1. Navigate to the Apache directory:
   cd /var/www/html
2. Delete the default index.html:
   sudo rm index.html
3. Create a new HTML file:
   sudo vi index.html
4. Add your HTML code:
   - Example:
   ```
     <html>
       Hlo, I am XYZ.
     </html>
   ```
5. Save and exit:
   Press Ctrl + C, then press Y, and hit Enter to save the file.

## Step 6: Access Your Website
1. Open a Browser.

2. Visit Your Website:

   Enter your EC2 Public IP in the browser:
   eg. (13.45.589.25)
3. You should see your custom HTML page!

