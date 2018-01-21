# Open VPN 

## Server

* Install stall the docker-compose.yml and the rancher-compose.yml on the server.
* Replace the private-ip-of-ranche-server and the public-ip-of-open-ssh-server of the ssh server in the docker-compose.yml

## Client Config
* Run the following on the docker container running on the open ssh server to get your client configuration:
   
   openvpn-get-client-config.sh
   
  Store the results on your client:
  
  /etc/openvpn/config.ovpn
  
  Sample content:
  
  remote 174.129.92.222 1194
  client
  dev tun
  proto tcp
  remote-random
  resolv-retry infinite
  cipher AES-128-CBC
  auth SHA1
  nobind
  link-mtu 1500
  persist-key
  persist-tun
  comp-lzo
  verb 3
  auth-user-pass
  auth-retry interact
  ns-cert-type server
  <ca>
  -----BEGIN CERTIFICATE-----
  MIIEkjCCA3qgAwIBAgIJAJixJkf9XdsOMA0GCSqGSIb3DQEBCwUAMIGMMQswCQYD
  VQQGEwJVUzELMAkGA1UECBMCRkwxDzANBgNVBAcTBlZlbmljZTEMMAoGA1UEChMD
  QlBFMQswCQYDVQQLEwJJVDEPMA0GA1UEAxMGQlBFIENBMRAwDgYDVQQpEwdFYXN5
  UlNBMSEwHwYJKoZIhvcNAQkBFhJwb2xpbmNod0BnbWFpbC5jb20wHhcNMTgwMTIx
  MTcxOTA5WhcNMjgwMTE5MTcxOTA5WjCBjDELMAkGA1UEBhMCVVMxCzAJBgNVBAgT
  AkZMMQ8wDQYDVQQHEwZWZW5pY2UxDDAKBgNVBAoTA0JQRTELMAkGA1UECxMCSVQx
  DzANBgNVBAMTBkJQRSBDQTEQMA4GA1UEKRMHRWFzeVJTQTEhMB8GCSqGSIb3DQEJ
  ARYScG9saW5jaHdAZ21haWwuY29tMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIB
  CgKCAQEAmj4EJ3oBqNijrt+GKiRUU06U9iUD0pl/fmpDfc7TYfCeH5/NtnOZ/sa2
  lL4UtfVrmlBg9S58GCn8QkNOKW6lKZTCYyngJs2LPxd0s3xF39ziefEWmywo7fGy
  +4Y+t773kfH/kxTeZGxBhdQBIzQ8SqWESS3fpzX3t9MwnXHProPfBRJ1eBpQwZOm
  mOWjU7KbSlkDICEXCNSRlZ6Y+gt5NRNdBSZS2Q/IrSWlhr8Ru0aTb+PStFUx+ypB
  KrR5Pyc9vchEPqpE/e36GbIQuTJ2uABynmf254YBMyFuJ47xOPEHIK+JgG+hV4zm
  to+6B0ifpJhPWsb4+M1tv8p6EXAXgwIDAQABo4H0MIHxMB0GA1UdDgQWBBR6drVp
  suc34SOddWlSdO0MeoTjETCBwQYDVR0jBIG5MIG2gBR6drVpsuc34SOddWlSdO0M
  eoTjEaGBkqSBjzCBjDELMAkGA1UEBhMCVVMxCzAJBgNVBAgTAkZMMQ8wDQYDVQQH
  EwZWZW5pY2UxDDAKBgNVBAoTA0JQRTELMAkGA1UECxMCSVQxDzANBgNVBAMTBkJQ
  RSBDQTEQMA4GA1UEKRMHRWFzeVJTQTEhMB8GCSqGSIb3DQEJARYScG9saW5jaHdA
  Z21haWwuY29tggkAmLEmR/1d2w4wDAYDVR0TBAUwAwEB/zANBgkqhkiG9w0BAQsF
  AAOCAQEAVCVgbN67HSlgL+KSGZBUTLQiRM9i/u6Ar+qGRuiNyPHVNpJy3R1e+8sI
  i358FcrNpB5LbALl+OfIOH0Rz5ybxFeF8HmJaTA7dcF2mwIK3tNcX12w+2JL6L56
  sq29FNX/IfFbsvY/8TBNGacfUA8DZRtI6Y97+8hWcGzSmd/1CBD72WFrnKaWp2LB
  GS7dUr0iL9jFga0B+VgfuGSKb51PY6lYqEQqZvK5gIrYnT0c0A7bR4CqqHS75poV
  becxL6jrwb9d3drNU6Hml+BuBXY4ypsUgiuhcIuXqMLrJRCeGwqpvI8bLcjLjDEI
  TJccTjtsmdO/+PPFnYYhhz3c7Jc13w==
  -----END CERTIFICATE-----
  </ca>

   
## Connect from the Client
   
* Connect from Linux by setting up a new VPN connection in your network admin page pointing to the /etc/openvpn/config.ovpn file.