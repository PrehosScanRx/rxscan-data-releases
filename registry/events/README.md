# Append-only release events

This directory is intentionally empty of lifecycle events.

Future records use `registry/events/<timestamp>-<state>-<releaseId>.json`. Candidate, approved, stable, rollback, and withdrawn transitions are append-only audit events. Existing events must never be changed or deleted.
