# Stateful Web App: MyWordpress.com

- We are trying to create a fully scalable Wordpress website
- We want that website to access and correctly display picture uploads
- Our user data, an the blog content should be stored in a MySQL database

Use multiple instances with a Load Balancer. For file uploads, use EFS. For database, use Aurora database to have easy Multi-AZ and Read-Replicas.