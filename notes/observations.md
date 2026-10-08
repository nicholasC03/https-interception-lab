# Observations

## Record scope

This summary uses the lab information reported during the project. Screenshots should accompany the repository. Packet numbers, exact certificate issuer/validity fields, and software versions are not transcribed here because the available text does not establish them. No values are inferred from the planned configuration.

## Date and environment

Evidence collection occurred during October 2026; project documentation was prepared October 8, 2026 (America/New_York). The client is an Ubuntu VM, the proxy is a Kali VM, and the endpoint is an owned AWS EC2 HTTPS server. Local VMs have NAT and host-only adapters. Kali's host-only address is `192.168.56.102`. The hostname used is `hypnos-https-lab.duckdns.org`. The current cloud public address and Ubuntu host-only address are not asserted here.

## Origin validation

The project includes `01-valid-origin-tls.png` for direct curl certificate validation. The endpoint was configured for Let's Encrypt HTTPS. Exact certificate subject/SAN, issuer, dates, and negotiated parameters should be read from the evidence rather than copied from setup expectations.

## Direct capture

`02-direct-tls-wireshark.png` documents the direct TLS capture. A TLS 1.3 Client Hello with the lab hostname in SNI was reported. That hostname is handshake metadata; it is not the encrypted HTTP query marker.

A Find Packet search returned “no packet contained that string in its converted data,” as reported by the operator. The conversation referred to the search phrase as “demo only 123”; the request marker is `DEMO_ONLY_123`. Without confirmation of the literal search text and Packet bytes setting, this summary does not treat that wording alone as proof that the exact marker was absent. Use the original search-result screenshot to confirm the settings before making a stronger claim.

Capture interface, actual capture filter, and frame numbers are not transcribed in this record.

## Untrusted proxy

`03-untrusted-proxy-rejected.png` is the evidence for certificate rejection without trusting the proxy CA. The exact curl error text and numeric exit code are not transcribed here. Certificate validation failure should be distinguished from connectivity failure in the screenshot.

## Trusted proxy

The operator explicitly reported matching CA fingerprints and HTTP 200 after the public proxy CA certificate was transferred. The intended trust scope is curl's `--cacert` option for one invocation, rather than installing a system-wide CA. `04-trusted-proxy-flow.png` documents the inspected proxy flow. The fictional test marker used by the project is `DEMO_ONLY_123`.

## Proxy capture

`05-proxy-wire-capture.png` documents the proxy connection. In this topology an HTTP CONNECT tunnel precedes client-to-proxy TLS. Decoded application requests are inspected in mitmproxy. Ordinary Wireshark wire payloads remain encrypted after TLS negotiation. Exact CONNECT/TLS frame numbers and capture settings are not transcribed here.

## Interpretation

The client deliberately chose an explicit proxy and trusted its lab CA. The proxy terminates client TLS and establishes separate upstream TLS to the origin. Passive packet observation alone does not grant that trust or reveal the HTTPS request.

## Limits and cleanup

The results apply to owned lab systems and fictional data. No claim is made about breaking TLS, attacking public users, or capturing a separate upstream leg. Raw packet captures and proxy flow dumps remain private by default. Resource cleanup and final GitHub image-link validation are pending until performed by the operator.
