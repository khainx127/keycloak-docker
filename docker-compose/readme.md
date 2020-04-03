# Keycloak

## Setup on localhost
Run command `docker-compose -f .\keycloak.yml up -d`

## Login Keycloak admininistration
Open url: http://localhost:8081/

Username: admin

Passwrod: P@ssw0rd 

## Default users
Username: usera

Passwrod: 12345678@A 

---

Username: userb

Passwrod: 12345678@A

## Authentication endpoints
Login Url: http://localhost:8081/auth/realms/rga/protocol/openid-connect/token

Authority: http://localhost:8081/auth/realms/rga

Audience: `account`

Client Id: `account`

Client Secret: `f50df734-7350-4acb-be7f-45c0e872127b`

## Form login
POST http://localhost:8081/auth/realms/rga/protocol/openid-connect/token

Headers:
`Content-Type: application/x-www-form-urlencoded`

Form Data
```
username: userb
password: 12345678@A
grant_type: password
client_secret: f50df734-7350-4acb-be7f-45c0e872127b
client_id: account
```

## Jwt 
This is a sample of Jwt after logging in
```
{
  "exp": 1585110293,
  "iat": 1585109993,
  "jti": "e44ccd9b-f2d3-4d92-95c3-6c3df2728adb",
  "iss": "http://localhost:8081/auth/realms/mycompany",
  "sub": "2c239e89-1ef8-4649-9d65-110c46a4170b",
  "typ": "Bearer",
  "azp": "account",
  "session_state": "662e6155-32a6-4cb6-a8dc-21be5d039689",
  "acr": "1",
  "allowed-origins": [
    "*"
  ],
  "realm_access": {
    "roles": [
      "Claims"
    ]
  },
  "resource_access": {
    "account": {
      "roles": [
        "manage-account",
        "manage-account-links",
        "view-profile"
      ]
    }
  },
  "scope": "email profile",
  "email_verified": false,
  "preferred_username": "userb"
}
```
User roles is `realm_access.roles`