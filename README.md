# FitFlow Redesign

**IT306 Human Computer Interaction | Lab Exercise 05 | Semester 2, 2026**

FitFlow is a proposed redesign of a fitness tracking app. The case study identifies problems with generic workout plans, limited social motivation, and nutrition logging. This repository contains the technology comparison and architecture proposed for the redesign.

This is an academic documentation repository. The application and AI models have not yet been implemented.

## Proposed Technology Stack

| Layer | Technology | Purpose |
|---|---|---|
| Mobile | React Native and TypeScript | iOS and Android app |
| Web | React | Browser experience with shared TypeScript logic where suitable |
| Backend | Node.js, Express, TypeScript | Workout, nutrition, social, and notification APIs |
| AI service | Python and FastAPI | Heavier recommendations and model training |
| Private data | PostgreSQL | User, workout, and confirmed nutrition records |
| Social data | Firebase Firestore | Real-time circles and challenges |
| Authentication | Firebase Authentication | User sign-in |
| On-device AI | TensorFlow Lite and custom ML Kit models | Suitable offline suggestions and food image labels |
| Cache | Redis, if needed | Short-lived derived data |

## Main Features

- Personalized workout suggestions that users can review and edit.
- Private social circles and community challenges.
- Food image suggestions with user confirmation of food, portions, and nutrients.
- Progress tracking across supported devices.

## Repository Structure

```text
fitflow-redesign/
├── frontend/
├── backend/
├── ai-service/
├── docs/
│   ├── tech-stack-summary.md
│   ├── comparison-matrix.md
│   ├── architecture-diagram.png
│   └── adr/
│       └── 0001-technology-stack.md
├── .gitignore
└── README.md
