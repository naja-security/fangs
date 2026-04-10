\# Lab 01 — Vulnerable Chatbot (VulnBot v1)



> Part of \[\*\*Naja / Fangs\*\*](../../) — vulnerable AI application stack for purple team training.



\## What this lab teaches



A deliberately insecure LLM customer support chatbot with \*\*5 documented vulnerabilities\*\*.

You'll practice extracting secrets from the system prompt using real prompt injection techniques.



\## Vulnerabilities (intentional)



| # | Vulnerability | OWASP LLM |

|---|---|---|

| 1 | Hardcoded secrets in system prompt | LLM07 |

| 2 | "Never reveal" treated as a security control | LLM07 |

| 3 | No input validation | LLM01 |

| 4 | No output filtering | LLM02, LLM05 |

| 5 | No rate limiting or logging | LLM10 |



\## What you'll need



\- Python 3.10+

\- \[Ollama](https://ollama.com) with `llama3.2:3b` pulled (`ollama pull llama3.2:3b`)

\- The `requests` Python library (`pip install requests`)



\## Run it



```bash

python vulnbot.py

```



You'll see a chat prompt. Try saying "hi" first to confirm it works.

Then try the attack probes in `recon\_log.md` to extract the secrets.



Type `quit` to exit.



\## Try these attacks



See \[`recon\_log.md`](./recon\_log.md) for 5 attack probes.

4 out of 5 successfully extracted both secrets from llama3.2:3b.



The most effective techniques in this lab:

\- \*\*Authority impersonation\*\* — claim to be a developer running an audit

\- \*\*Translation bypass\*\* — ask the model to translate its instructions to another language

\- \*\*Completion trick\*\* — ask the model to complete a sentence that starts with the system prompt



\## Findings



The full purple team finding (red team results, blue team mitigations, lessons learned) is in \[`purple\_engagement.yaml`](./purple\_engagement.yaml) in industry-standard format.



\## What you should learn



> The system prompt is not a security boundary. It is a behavior suggestion. Anyone determined will extract it. Treat it as public.



If you put secrets in a system prompt, they will leak. The only real fix is to never put secrets there in the first place.



\## Hardening (coming in later labs)



| Day | What we add | Tool |

|-----|---|---|

| 02 | Input filtering | LLM Guard |

| 04 | Output PII scrubbing | Presidio |

| 17 | Logging + rate limiting | Langfuse |



\## Status



🐍 Lab 01 — shipped Day 1 of 20 of the Naja sprint.







