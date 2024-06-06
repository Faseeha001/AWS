# Hands-On : Using Amazon LightSail Launch a website with Load Balancer

Setting up two web servers, connecting them to a load balancer on Amazon Lightsail, and pointing them to a domain involves several steps. Here's a detailed guide to help you through the process:

## 1. Set Up Two Web Servers on Amazon Lightsail
**Step 1**: Create Two Lightsail Instances

1.Log in to your AWS Management Console.

2.Navigate to Lightsail.

3.Create an instance:

* Choose the region where you want your instance to be located.
![image](https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/c8573d0c-b71f-4cf2-b315-4f043e79aa53)

*Select a blueprint (OS or application). For a web server, you can choose Linux/Unix and then select the appropriate app or stack (Here Wordpress is used ).
![image](https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/77c1da52-b8ec-4348-9f97-4b295e226713)

*Choose an instance plan based on your needs.
<img width="609" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/a4eba3ad-a773-4c74-b493-62beb515b5bc">

*Name your instance (e.g., webserver-1).
<img width="673" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/18951b3b-d108-431b-b445-5e6a3417a61c">

Repeat the process to create Webserver2.

## 2. Set Up a Load Balancer on Lightsail
**Create a Load Balancer**

In the Lightsail console, go to the Networking tab.

1. Create a load balancer:

Name your load balancer (e.g., my-load-balancer).
<img width="760" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/a5905901-38ba-46ba-a327-68c17eccd625">

2. Choose the region where your instances are located.
<img width="719" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/d475e2df-3338-4166-9f50-6e0cad01406c">

Create the load balancer.
![image](https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/b85626b1-1871-49da-b7fa-9a5d5ca100e9)
**Attach Instances to the Load Balancer**

1. After the load balancer is created, go to its management page.
Attach your instances (webserver-1 and webserver-2) to the load balancer.

<img width="626" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/29b3b963-0aa4-467a-8e93-234706c4c528">

## 3.Configure SSL/TLS Certificate for the Load Balancer
**Step 1 :Request an SSL/TLS Certificate**

1.  In the Lightsail console, navigate to your load balancer's management page.
 Click on the "Certificates" tab.
 Request a new certificate:
 Enter your domain name.
 Add any additional domain names if needed (e.g., www.yourdomain.com)
<img width="565" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/29598bdd-a74d-4431-b6e6-56b2cc2435e4">
<img width="613" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/c02e63c0-e359-43ec-b49c-e7df3a2859fe">

 **Step2 : Validate the Domain**

Follow the instructions to validate your domain. This typically involves adding a CNAME record to your domain's DNS settings.
1. Log in to your domain registrar's account and navigate to the DNS settings.
2. Add the CNAME record provided by Lightsail to your DNS settings.
3. Wait for the validation to complete. This may take some time depending on your DNS provider.
**Step 3: Attach the Certificate to the Load Balancer**

Once the certificate is issued, return to the load balancer's management page.
In the "Certificates" tab, select the issued certificate and attach it to the load balance
<img width="522" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/762ff44e-0586-4e6c-ab11-2ba429a80b98">
<img width="477" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/4f2ff336-1f13-42eb-b5f7-299bbf9b7527">

## Point Your Domain to the Load Balancer

**Step 1: Get the DNS Name of the Load Balancer**
1.In the Lightsail console, navigate to your load balancer's management page.
2.Copy the DNS name of the load balancer.

**Step 2: Update Your Domain's DNS Settings Using Amazon Lightsail's Domains and DNS Service**

1.Navigate to the Networking tab in the Lightsail console.
2.Click on "Create DNS zone".
Enter your domain name and click "Create DNS zone".
<img width="764" alt="image" src="https://github.com/Faseeha001/Static-web-Host-using-S3/assets/169563689/33b2168e-35cc-4966-a827-bf3c6bae1ffe">

