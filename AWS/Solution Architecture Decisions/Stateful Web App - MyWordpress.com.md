---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/architecture, review]
sr-due: 2022-11-10
sr-interval: 3
sr-ease: 250
---

# Stateful Web App: MyWordpress.com

- We are trying to create a fully scalable Wordpress website
- We want that website to access and correctly display picture uploads
- Our user data, an the blog content should be stored in a [[MySQL]] database

Use multiple instances with a [[Load Balancer]]. For file uploads, use [[EFS - Elastic File System]]. For database, use [[AWS Aurora]] database to have easy [[Multi-AZ]] and [[Read Replica]]s.