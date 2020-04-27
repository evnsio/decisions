# This is a test decision

Author: [@chris](slack://user?team=T9U3SEE12&id=U9U5GKCHG)

Category: `just-a-test`

Date: 2020-04-27

## Context

We need to be able to support the request-response model of a handler, however, so we&#39;ve taken the approach of doing some basic multiplexing over the http2 stream, ie we are able to create synchronous &#39;channels&#39; within a single bidirectional stream, where the server can send a message to the client, and block waiting for the right response. Events are tagged with a channel ID which is also set in the response sent back to the server. The server-side streams handler is then able to block until the response comes in for that channel. In doing so, we are designing a wire protocol, which isn&#39;t ideal, but we&#39;ve mostly copied the Go SSH library for the channel implementation.

## Decision

Event processing in multiple environments with isolation — while avoiding the need to deploy lots of services in every environment — is a complex problem with no clear and easy solution, and we have explored a wide range of different options (see below in the Appendix for more details on the alternatives we considered, though not essential reading!).

## Consequences

- This is a thing
- This is another thing