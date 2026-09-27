# Consent Mail

Consent records and campaign audience previews.

An email address alone is not permission to send a campaign. This prototype tracks a separate consent lifecycle for each purpose and checks eligibility when a campaign audience is previewed.

**Status:** local prototype, under development. Java 17+, Spring Boot 4.1.1, PostgreSQL and Flyway.

## Implemented

- Pending, confirmed and withdrawn consent states.
- Single-use confirmation tokens with a 24-hour expiry.
- Encrypted email storage, hashed tokens and consent events.
- Campaign drafts and audience counts that exclude pending or withdrawn contacts.

## Run locally

Requires Java 17+ and Maven 3.6.3+.

```sh
mvn verify
mvn spring-boot:run -Dspring-boot.run.profiles=demo
```

Open <http://localhost:8082>. Sign in with `operator` / `operator-local`.
The separate review account is `reviewer` / `reviewer-local`; administration uses `admin` / `admin-local`.
These public credentials are only for the localhost demo, which resets its H2 database on restart.

With the application running, exercise the complete example:

```sh
python3 scripts/demo.py
```

## Project notes

- [Design and business rules](docs/design.md)
- [API and configuration](docs/api.md)
- [Next steps](docs/roadmap.md)

The automated suite uses H2 in PostgreSQL mode. PostgreSQL setup is included; it is a separate integration check.
