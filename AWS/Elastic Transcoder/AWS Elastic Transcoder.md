---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/course/aws-certified-solutions-architect-associate-saa-c01/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/aws/elastic-transcoder, review]
sr-due: 2022-11-24
sr-interval: 1
sr-ease: 130
---

# AWS Elastic Transcoder

- [[Convert]] [[media files]] ([[video]] + [[music]]) stored in [[AWS S3]] into various formats for tablets, PC, Smartphone, TV etc
- Features: [[bit rate optimisation]], [[thumbnail]], [[watermarks]], [[captions]], [[DRM]], [[progressive download]], [[encryption]]
- 4 components:
    - [[Jobs]]: what does the work of the transcoder
    - [[Pipeline]]: [[Queue]] that manages the transcoding job
    - [[Presets]]: Template for converting media from on format to another
    - [[Notifications]]: [[AWS SNS]] for example
- Pay for what you use, scales automatically, [[fully managed]]