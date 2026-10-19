# Silicon Workshop Agent

Identity card for the automated agent operating **https://subsilicon.cn**.

This repository exists so platforms, search engines and API providers can verify a claim:
*"this request comes from the Silicon Workshop agent"* — cryptographically, not by user-agent string.

## Identity

| Field | Value |
|---|---|
| Agent name | `silicon-agent` |
| Operator | 剑阁县下寺镇硅基之下信息技术咨询服务店（个体工商户） |
| Homepage | https://subsilicon.cn/agent/ |
| Public key directory | https://subsilicon.cn/.well-known/http-message-signatures-directory |
| Algorithm | Ed25519 (RFC 8037) |
| keyid | `96aIOgmi6My2zYCQPLBHYZVGJgJPwWMGDUSJZxdcroY` |

## How requests are signed

Requests carry `Signature` and `Signature-Input` headers per
[RFC 9421 HTTP Message Signatures](https://www.rfc-editor.org/rfc/rfc9421), following the
[Web Bot Auth](https://developers.cloudflare.com/bots/reference/bot-verification/web-bot-auth/) profile:

```
Signature-Input: sig1=("@method" "@authority" "@path");created=..;expires=..;keyid="..";alg="ed25519";tag="web-bot-auth"
Signature: sig1=:..:
Signature-Agent: "https://subsilicon.cn/agent/"
```

Covered components: `@method`, `@authority`, `@path`. Signatures expire in 5 minutes.
The verifying key is published as a JWKS at the directory URL above.

## What this agent does

- Maintains the tool site (content, fixes, deployment) and its automation.
- Handles work explicitly delegated by the operator.
- Signs its outbound requests so operators can distinguish it from unlabelled crawlers.

## What it does not do

- Impersonate a human, or bypass real-name / CAPTCHA / KYC checks.
- Submit someone else's identity documents.
- Scrape content that requires authentication.
- Operate a payment account in its own name — payments run through the operator's registered entity.

## Responsibility

The agent has no separate legal personality. All acts, obligations and liabilities
rest with the operator named above. Report abuse through the contact on the homepage.
