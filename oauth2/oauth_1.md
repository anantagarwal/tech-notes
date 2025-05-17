# Oauth 2.0 - Nuts & Bolts

## A. Introduction

### 1. Brief History

- **2006**: OAuth originated from the need for a secure, open protocol for API authorization—engineers from Twitter and
  Ma.gnolia (a bookmarking service) began discussing better alternatives to password sharing.
- **2007**: The OAuth Core 1.0 protocol was formalized by a group of open web developers and published under the OAuth
  community project.
- **December 2007**: OAuth 1.0 was officially released, providing a token-based authorization method with strong
  cryptographic signatures.
- **2009**: Work began on OAuth 2.0 to simplify the protocol, improve usability for developers, and support a wider
  range of use cases, such as mobile and enterprise apps.
- **October 2012**: OAuth 2.0 was published as RFC 6749 by the IETF, marking a significant shift away from the more
  complex signature-based flow of OAuth 1.0.
- **Post-2012**: OAuth 2.0 gained widespread adoption by major tech companies (e.g., Google, Facebook, Microsoft),
  becoming the standard for delegated authorization.
- **Recent years**: Extensions and profiles like OAuth 2.1 (draft), PKCE, and OpenID Connect emerged to address security
  issues and expand capabilities for identity and mobile scenarios.

| **Aspect**               | **OAuth 1.0**                                        | **OAuth 2.0**                                                                     |
|--------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------|
| **Release Year**         | 2007                                                 | 2012                                                                              |
| **Specification**        | RFC 5849                                             | RFC 6749 (core), RFC 6750 (Bearer Tokens), and extensions                         |
| **Security Mechanism**   | Uses **HMAC-SHA1** signatures for request validation | Relies on **HTTPS (TLS)** for transport-layer security                            |
| **Token Type**           | Uses **signed tokens** (with signature verification) | Uses **Bearer tokens** (easier to use, but less secure if not protected by HTTPS) |
| **Complexity**           | More complex (signing every request)                 | Simpler for developers, more flexible flows                                       |
| **Mobile & Web Support** | Limited support for mobile                           | Strong support for mobile apps and SPAs                                           |
| **Client Types**         | Primarily for confidential clients                   | Supports public and confidential clients                                          |
| **Extension Support**    | Limited                                              | Highly extensible (PKCE, JWT, OpenID Connect, etc.)                               |
| **Revocation & Scopes**  | Limited                                              | Improved support for **scopes**, **token revocation**, and **refresh tokens**     |
| **Use Today**            | Largely deprecated                                   | Industry standard for authorization                                               |

### 2. How it improves Application Security

#### 2.1 Eliminates password sharing

- Users grand limited access using `tokens`, not credentials.
- Prevents apps from storing or mishandling user passwords.

#### 2.2 Scoped Access

- OAuth 2.0 allows tokens to be granted with specific `scopes`, meaning:
    - Limited permissions (e.g. read-only access)
    - Reduced impact if a token is compromised

#### 2.3 Short-Lived and Refresh Tokens

- **Access tokens** are short-lived, limiting the window of abuse.
- **Refresh tokens** allow secure re-authentication with:out user involvement

#### 2.4 Supports Strong Client Authentication

- Users `client credentials` and `redirect URI's` to validate legitimate apps.
- Prevents unauthorized apps from impersonating others.

#### 2.5 Enforces Use of HTTPS

- OAuth 2.0 assumes TLS/HTTPS for all token transmissions.
- Protects tokens from eavesdropping or interception.

#### 2.6 Token Revocation and Rotation

- OAuth 2.0 supports revoking tokens on logout or compromise
- Token rotation reduces risk from leaked refresh tokens.

#### 2.7 Minimized Attack Surface

- Applications don't need to handle or store user crendentials
- Reduces risk of database leaks or password theft

### 3. OAuth vs OpenID Connect

#### Real work analogy

- e.g. Hotel card, the room door need not know who you are. You can use this card to access room, gym etc.
- Front desk is checking id, credit card and handing over the card (access token), the rooms, gym etc are the resource
  servers.
- The key card does not have any user details, it only knows how to open the door.
- The key card has the list of doors it can open and an expiration date
- OAuth does not hold any user information.
- Using OpenID Connect, we add user details
- OAuth issues access tokens to the app
- OpenID issues id tokens to the app

  | Feature        | **OAuth 2.0**                      | **OpenID Connect (OIDC)**                         |
      | -------------- | ---------------------------------- | ------------------------------------------------- |
  | Purpose        | **Authorization** (access control) | **Authentication + Authorization**                |
  | User Identity? | ❌ No                               | ✅ Yes (provides user info like name, email, etc.) |
  | Built On       | Standalone protocol                | Built on top of OAuth 2.0                         |
  | Analogy        | Hotel key for amenities            | Hotel key + your ID badge                         |

## B. API Security Concepts

## Resources

- [OAuth](https://oauth.net/)
- [OAuth Specs](https://oauth.net/specs/)