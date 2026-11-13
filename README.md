# PRESENCE
A data analyst project that focuses on CCTV footage. The system will use  convolutional neural networks (CNN) machine learning model  to capture attendance, monitor student actions and generate insight. 


Proposal
This proposal outlines a data science project that makes use of convolutional neural networks (CNNs) to analyse existing CCTV footage in order to automate classroom attendance from which insights can be derived.
The system is designed to reduce teacher administrative workload and improve the accuracy of attendance records.
The system would record who is present in each lesson and turn those records into patterns such as punctuality, subject-level absenteeism, and early signs of truancy, so staff can act sooner and teachers spend less time on roll calls.
Problem statement 
Manual roll calls consume instructional time, often 5 to 10 minutes per lesson. This eats up on valuable time that could be spent in passing knowledge.
Attendance records are also prone to errors, proxy attendance, and delayed reporting to parents. Meanwhile, staff cannot continuously watch camera feeds, so incidents are usually reviewed only after the fact.
Research Questions
The business questions the system should answer:
Which classes, periods, or days have the highest absence and lateness?
Which students show an emerging pattern that needs a welfare check?
How much teaching time is recovered by removing manual roll calls?



Objectives
Automate attendance capture in classrooms.
Reduce teacher time spent on administrative attendance tasks.
Capture student behaviour.
Demonstrate that the system can operate fairly, transparently, and in compliance with data protection law.
Dataset links 
GitHub - Whiffe/SCB-dataset: Student Classroom Behavior dataset
WIDER FACE: A Face Detection Benchmark
Proposed Technical Approach
System Overview
The pipeline has five stages: video capture, pre-processing, CNN-based analysis, decision and logging, and staff review.
Video capture: Existing CCTV streams are ingested at 5 to 10 frames per second, which is sufficient for attendance and event detection while limiting compute and storage.
Pre-processing: Frames are resized, normalised, and enhanced for low light. Regions outside the monitored area are masked.
CNN analysis: Separate models handle detection, identification, and behaviour.
Decision and logging: Outputs are converted into attendance entries or alerts with confidence scores. Low-confidence results are routed to a human.
Staff review: Teachers and designated staff confirm, correct, or dismiss results through a dashboard.
Attendance Module
Person detection: A CNN detector using YOLO-family or Faster R-CNN model locates people in each frame.
Face detection and embedding: A face detector using RetinaFace which crops faces, and a CNN embedding model (such as ArcFace-style networks built on ResNet backbones) converts each face into a numeric vector.
Matching: Embeddings are compared against a consent-based enrolment database. A student is marked present when a match exceeds a confidence threshold across several frames, which reduces false positives.
Fallback: Students without consent, or whose faces are not matched, are recorded through manual or alternative methods (for example ID card scan) so that no one is penalised.










