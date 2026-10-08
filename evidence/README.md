# Evidence descriptions

## [00-vm-connectivity.png](00-vm-connectivity.png)

Records the VM connectivity checks used before the HTTPS and proxy tests.

## [01-valid-origin-tls.png](01-valid-origin-tls.png)

Documents the direct curl test of the HTTPS origin and its certificate validation before introducing the interception proxy.

## [02-direct-tls-wireshark.png](02-direct-tls-wireshark.png)

Records the direct HTTPS exchange in Wireshark, showing TLS handshake metadata while HTTP request content remains encrypted.

## [03-untrusted-proxy-rejected.png](03-untrusted-proxy-rejected.png)

Documents certificate verification rejection when the Ubuntu client uses the proxy without trusting its lab certificate authority.

## [04-trusted-proxy-flow.png](04-trusted-proxy-flow.png)

Documents the fictional request inspected in mitmproxy after the client explicitly trusts the lab CA for a single curl invocation.

## [05-proxy-wire-capture.png](05-proxy-wire-capture.png)

Records the client-to-proxy connection in Wireshark, distinguishing the HTTP CONNECT tunnel setup from the encrypted TLS traffic that follows.
