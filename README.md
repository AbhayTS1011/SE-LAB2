# Telemedicine Slot Booking & Prescription Portal

This repository contains the software engineering lab material for **Problem Statement #11: Telemedicine Slot Booking & Prescription Portal**. The proposed system lets patients find physicians, book and pay for video consultations, receive secure meeting details, and access signed prescriptions.

## Project scope

The documents describe these core capabilities:

- Patients browse physicians by specialty, review profiles and availability, and select a consultation slot.
- Patients pay through a payment gateway. A successful payment confirms the appointment; repeated payment failure cancels the booking and releases the slot.
- The portal generates a secure video-room link and sends appointment information to the patient and physician.
- Physicians create and digitally sign structured prescriptions, which patients can later download as PDF records.
- Patients can review previous consultations and access their own prescription records.

## Requirements at a glance

| ID | Requirement |
| --- | --- |
| FR-001 | Physicians author and digitally sign prescriptions that are compiled into downloadable PDFs. |
| FR-002 | Patients browse and filter physicians by specialty and view profiles and availability. |
| FR-003 | Patients select available consultation slots and securely pay the consultation fee. |
| FR-004 | After booking, the system generates encrypted video-room links and transmits them to patient and physician. |
| FR-005 | Patients view consultation history and download digitally signed prescriptions. |
| NFR-001 | Protect video-session metadata and clinical notes with TLS 1.3 in transit and AES-256 at rest. |
| NFR-002 | Return doctor search results and available slots within a 2-second target. |

## Booking flow

The main use case is **UC-02: Book Video Consultation Slot**. A logged-in patient chooses a specialty, doctor, and time slot, reviews the fee, and confirms a payment method. When the payment gateway authorizes the transaction, the portal records the appointment, updates the schedule, creates the video-room link, and sends confirmation and a receipt. If payment is declined, the patient can retry; after two failed attempts, the reservation is released and the process is cancelled.

## Architecture

The architecture note compares layered, microservices, and client-server approaches and selects a **hybrid layered-microservices architecture**. The layered structure separates presentation, business logic, and data concerns. Services for booking, payment, telehealth, and prescriptions can be developed, maintained, and scaled independently. The document also proposes an API Gateway for controlled access, TLS 1.3 for communications, AES-256 for applicable data at rest, and asynchronous processing for resource-intensive work.

## Files in this folder

| File | Contents |
| --- | --- |
| `Requirements.pdf` | Functional and non-functional requirements, priorities, acceptance criteria, and rationale. |
| `UseCaseFlow.pdf` | Actors, preconditions, postconditions, main success scenario, and declined-payment alternate flow for UC-02. |
| `Architecture_Comparison_and_Justification.pdf` | Architecture comparison, selected design, and security and performance rationale. |
| `Lab assignment1 - Usecase diagrams - Classroom.pdf` | Google Classroom export referring to `use-case-diagram.png`. |
| `Lab - Assignment2- Create component diagram - Classroom.pdf` | Google Classroom export referring to `TELEMEDICINE_COMPONENT_DIAGRAM.png`. |

The two Classroom export PDFs contain links and image names rather than the diagram artwork. The referenced PNG files are not included in this folder.

## Note

This folder contains planning and modelling documents; it does not include application source code or a running implementation.
