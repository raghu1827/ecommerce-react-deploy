# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

# E-Commerce React Application Deployment

This project demonstrates the deployment of a React-based e-commerce application using Vite on an Amazon Linux 2023 (AL2023) EC2 server with NGINX as the web server.

---

## **Features**
- Single Page Application (SPA) built with React and Vite.
- Optimized static file serving using NGINX.
- SPA routing handled by NGINX.
- Hosted on AWS EC2 for scalability and reliability.

---

## **Tools and Technologies**

- **Frontend:** React.js (Vite-based).
- **Server:** Amazon Linux 2023 (AL2023).
- **Web Server:** NGINX.
- **Build Tool:** Vite.
- **Version Control:** GitHub.
- **Cloud Platform:** AWS EC2.

---

## **Deployment Steps**

### **1. Prerequisites**
- Node.js and npm installed on your local machine.
- Access to an AWS EC2 instance running Amazon Linux 2023.
- NGINX installed on the EC2 instance.

### **2. Build the Application**

1. Clone the repository:
  
   git clone <repository_url>
   cd <repository_directory>


2. Install dependencies:

   npm install

3. Build the application:

   npm run build


### **3. Deploy to EC2**

1. Transfer build files to the EC2 instance:
2. 
   scp -r dist/* ec2-user@<ec2-instance-ip>:/usr/share/nginx/html/


3. SSH into the EC2 instance:
  
   ssh ec2-user@<ec2-instance-ip>

### **4. Configure NGINX**

1. Open the NGINX configuration file:
 
   sudo vi /etc/nginx/nginx.conf

2. Replace the content with:
   nginx
   server {
       listen 80;
       server_name <ec2-instance-ip>;

       location / {
           root /usr/share/nginx/html;
           index index.html index.htm;
           try_files $uri /index.html;
       }
   }

3. Test and restart NGINX:
   sudo nginx -t
   sudo systemctl restart nginx
   

### **5. Test the Deployment**

Open your browser and visit:

http://<ec2-instance-ip>

---

## **Future Enhancements**

1. Add HTTPS support using a TLS/SSL certificate.
2. Automate deployment with CI/CD pipelines.
3. Integrate logging and monitoring for the server and application.

---

## **License**

This project is licensed under the MIT License.

