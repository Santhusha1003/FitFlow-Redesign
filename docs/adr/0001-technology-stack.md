# ADR 0001: Technology Stack for FitFlow Redesign

## Status

Accepted

## Context

FitFlow requires a rebuilt mobile experience spanning iOS, Android, and a lightweight web presence, with AI-powered personalization, computer-vision nutrition logging, and real-time social features.

The startup has a small-to-mid-sized engineering team, needs to move quickly to market, and must keep infrastructure costs predictable while meeting GDPR/CCPA data obligations identified during user research.

## Decision

The following technology stack has been selected for the FitFlow redesign:

- **Frontend:** React Native, for near-total code reuse across iOS/Android and JavaScript/TypeScript alignment with the backend team.
- **Backend:** Node.js with Express, exposing REST endpoints and WebSocket channels for real-time social and notification features.
- **Database:** Firebase Firestore for real-time social/community data and PostgreSQL for structured, compliance-sensitive user and health records.
- **Authentication:** Firebase Authentication, for fast integration with the chosen data layer and built-in OAuth/social login support.
- **AI/ML:** TensorFlow Lite for on-device workout personalization and ML Kit for camera-based nutrition logging. Cloud-side model training supports the on-device models.
- **Caching:** Redis for session state and frequently accessed analytics queries.

## Consequences

### Positive

- Provides a realistic path to a cross-platform Minimum Lovable Product.
- A single JavaScript/TypeScript team reduces hiring and onboarding friction.
- On-device AI reduces data transmission and supports the privacy-by-design goal.

### Trade-offs

- Using both Firestore and PostgreSQL adds integration complexity compared with using a single database.
- The two-database approach is used because PostgreSQL provides a stronger fit for compliance-sensitive health data.
- React Native's JavaScript bridge can become a bottleneck for extremely complex animations.

### Mitigation

Heavy animation work can be moved into native modules where profiling shows that it is required.

## Revisit Trigger

If the user base scale or model complexity outgrows Firebase or on-device TensorFlow Lite, the technology stack should be re-evaluated.

Potential future options include a dedicated Go-based real-time service and self-hosted vector/ML infrastructure.
