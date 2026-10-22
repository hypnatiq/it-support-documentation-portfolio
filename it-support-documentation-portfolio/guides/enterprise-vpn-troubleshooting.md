# Enterprise VPN Troubleshooting

## Purpose

Use this runbook to separate endpoint, local-network, authentication, client, gateway, policy, and application-access failures. It is vendor-neutral and assumes the VPN profile is managed by an organization.

## Safety and authority

- Never ask a user to disclose a password, one-time code, recovery code, or MFA approval.
- Do not weaken TLS, firewall, endpoint protection, certificate validation, or conditional-access controls to make a connection succeed.
- Do not edit the managed gateway, certificate, route, DNS, or tunnel mode without authorization.
- Export logs only to an approved location and review them for usernames, addresses, tokens, and internal hostnames before sharing.
- Use an approved break-glass or recovery process for identity issues.

## 1. Define the failure stage

Capture:

- Exact client name and version
- Exact error text, timestamp, and connection profile
- Whether the failure occurs before credential entry, during authentication, during MFA, while establishing the tunnel, or after connection
- Whether the user can reach the internet without the VPN
- Whether one user, one endpoint, one network, one location, or many users are affected
- Whether the VPN reports connected while the required application remains unavailable

Do not treat a client progress percentage as a universal root-cause map. Percentages and error codes vary by version, gateway, configuration, and authentication flow.

## 2. Check service status and scope

1. Review the organization’s approved status page and current incident channel.
2. Test with a known-good account or endpoint only if policy allows.
3. Determine whether the gateway, identity provider, MFA service, certificate authority, DNS, or target application has a known incident.

If multiple users fail at the same stage, escalate as a service incident before changing endpoints individually.

## 3. Establish a local connectivity baseline

- Confirm the endpoint has a valid address, default route, DNS resolution, and working internet access.
- Confirm system time and time zone are correct because certificate and authentication checks depend on time.
- Move from an untrusted or captive portal to an approved network.
- Test a second known-good network, such as an approved mobile hotspot, only if policy permits.
- Record whether the result changes. A successful second-network test points toward the first network path, not automatically toward the endpoint.

Do not disable the local firewall or endpoint protection as a routine test.

## 4. Verify the managed profile and client health

1. Confirm the selected profile, gateway name, and connection type match the approved configuration.
2. Confirm the client is compatible with the managed gateway version.
3. Confirm required background services are running.
4. Confirm the endpoint has the expected management or telemetry connection if the organization requires one.
5. Compare the installed client version with the supported version list.

Repair or reinstall only through the approved software channel. Export the current profile and logs first when policy allows. Do not manually recreate a managed profile from memory.

## 5. Separate identity, MFA, and certificate failure

- Confirm the account is active and not locked through the approved identity tool.
- Confirm password status without asking the user to reveal it.
- Ask the user to complete MFA privately on the registered method.
- Check for sign-in risk, conditional-access, location, device-compliance, or certificate errors through authorized logs.
- For certificate-based VPN, verify certificate presence, validity dates, intended purpose, trust chain, and private-key access.

MFA method changes and re-registration are identity-security actions. Follow the organization’s verification and recovery process rather than editing user contact data as a troubleshooting shortcut.

## 6. Confirm tunnel establishment and post-connect function

If the client reports connected, test the required workflow in layers:

1. Assigned address and route
2. DNS resolution for the approved internal name
3. Reachability to the required service and port
4. Application authentication
5. Original user task

A connected icon proves only that the client believes a tunnel exists. It does not prove DNS, routes, policy, or the destination application is working.

## 7. Collect evidence for escalation

Collect only what policy allows:

- Client and operating-system version
- Gateway profile name, sanitized outside the organization
- Error code and timestamp with time zone
- Failure stage
- Network comparison result
- Identity, MFA, certificate, and compliance state from approved consoles
- Client logs at the minimum useful verbosity
- Route, DNS, and destination-port test results
- Recent changes and rollback attempt

For FortiClient environments, Fortinet documents checking version compatibility, gateway reachability, tunnel settings, and exported debug logs. Treat Fortinet error codes and progress behavior as version-specific evidence rather than a universal diagnosis.

## Change, rollback, and validation

- Make one approved change at a time.
- Record the previous client version, profile, certificate state, and network result.
- If a reinstall or profile update fails, restore the approved prior state or escalate.
- Validate connection, DNS, route, target application, and the user’s original task.
- Confirm the tunnel disconnects cleanly and normal non-VPN access behaves as policy expects.

## Authoritative references

- [Fortinet: Troubleshooting common SSL VPN issues](https://docs.fortinet.com/document/fortigate/7.0.3/administration-guide/993282/troubleshooting-common-issues)
- [Fortinet: Configuring an SSL VPN connection](https://docs.fortinet.com/document/forticlient/7.4.3/administration-guide/205286)
- [Fortinet: Verifying and troubleshooting](https://docs.fortinet.com/document/forticlient/7.4.7/administration-guide/893881/verifying-and-troubleshooting)
- [Microsoft: Fix Wi-Fi connection issues in Windows](https://support.microsoft.com/en-us/windows/fix-wi-fi-connection-issues-in-windows)
