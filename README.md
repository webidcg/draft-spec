### Web Identity and Discovery (WebID) Specification

**Author**: Nathan Rixham

#### Abstract

WebID defines a standard means by which user agents and servers interact to establish a user's identity, ensuring a structured, decentralized approach for identity and discovery on the web. This specification delineates a URI that dereferences to an RDF response, asserting a `webid:Agent` to qualify as a WebID. This spec encompasses an open-ended list of sub-specifications, each addressing a valid RDF response type.

#### Table of Contents

1. [Introduction](#introduction)
2. [Terminology](#terminology)
3. [WebID Definition](#webid-definition)
4. [WebID Sub-Specifications](#webid-sub-specifications)
5. [Implementation](#implementation)
6. [Security Considerations](#security-considerations)
7. [Acknowledgments](#acknowledgments)

#### 1. Introduction

The WebID protocol enables secure and decentralized identity verification on the web, allowing users and services to establish verifiable identities.

#### 2. Terminology

- **WebID**: A URI which, when dereferenced, leads to an RDF document that asserts the URI is related to a `webid:Agent`.
- **webid:Agent**: An entity that can be authenticated and identified via a WebID.
- **RDF**: Resource Description Framework, a language for representing information about resources on the web.

#### 3. WebID Definition

A **WebID** is a URI which, when dereferenced, should result in an RDF document. This document should assert the URI to be an entity of type `webid:Agent`. The dereference must adhere to the HTTP/1.1 status code 303 (See Other) to ensure the URI is not ambiguous and that the RDF document is a description of the identified URI.

```plaintext
<uri> rdf:type webid:Agent.
```

#### 4. WebID Sub-Specifications

WebID introduces an extensible list of sub-specifications for each valid RDF response type. Denoted as `webid-{type}`, each sub-specification is constrained to require only that specific RDF type.

##### Examples:

- **WebID-Turtle**: Requires Turtle RDF response type.
- **WebID-JSON-LD**: Requires JSON-LD RDF response type.

Additional sub-specifications can be defined in an analogous manner, promoting a flexible, inclusive framework for varied RDF types.

#### 5. Implementation

Implementing WebID involves creating a URI which, upon dereferencing, results in an RDF response that asserts the URI identifies a `webid:Agent`. Sub-specifications enforce the type of RDF used in the response.

##### Example:
```turtle
@prefix : <#>.
@prefix webid: <http://webid.example.org/>.

:me rdf:type webid:Agent.
```
Where `:me` is a URI identifying an agent, and the document is available in Turtle format at a dereferenceable URI.

#### 6. Security Considerations

- **Dereferencing URIs**: Ensure secure, private, and integral URI dereferencing.
- **Verification**: Verification of assertions in the RDF document must be secure to prevent spoofing and injection attacks.
- **Privacy**: Protect the privacy of users and consider data minimalism to avoid exposure of sensitive or unnecessary information.
  
#### 7. Acknowledgments

The author acknowledges the contributions and discussions from the WebID community and related working groups.

#### Notes

This spec acts as a succinct, adaptable framework, allowing the community to define and utilize a variety of RDF types within the WebID protocol. It achieves universality and potentially infinite applicability without necessitating further modifications to the primary specification.
