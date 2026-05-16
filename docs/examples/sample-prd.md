# Sample PRD: Account Email Change

## Background

Users need a secure way to change their account email address while preserving account ownership and auditability.

## Goal

Allow authenticated users to request an email change, verify the new email address, and complete the change only after verification.

## Users

- Authenticated account owner.
- System notification service.
- Support operator who may inspect audit records.

## Requirements

- User can submit a new email address.
- System sends a verification message to the new email address.
- Email address changes only after verification succeeds.
- Expired verification requests cannot be used.
- All email change attempts are auditable.

## Non-Functional Requirements

- Verification tokens must expire.
- The flow must avoid account takeover risk.
- The system must record audit events.
