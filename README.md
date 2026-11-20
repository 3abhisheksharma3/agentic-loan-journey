# SuperAgent: an agentic, voice-first personal loan journey

A working prototype of how a personal loan could feel if an AI agent did the paperwork. The customer talks, the agent fetches and checks everything in the background, and the customer only confirms the steps that matter.

**▶ Live demo:** `https://<your-username>.github.io/agentic-loan-journey/`

![Five screens from the journey: start, consent, offer, video KYC and submitted](docs/preview.png)

> Concept prototype with synthetic data. It is not affiliated with any lender, bank, credit bureau or government service, and nothing you say or type leaves your browser.

## Try it

| Button | What happens |
|---|---|
| **Start with voice** | Talk to the assistant. Works best in Chrome or Edge (allow the microphone). |
| **Start with text** | Type, or tap the suggestion chips. |
| **Watch an auto-play demo** | The full journey plays hands-free in about 70 seconds. |

On a laptop, the **Behind the screen** panel on the right shows every background job as it runs. Press **D** to hide it.

## The journey

| # | What the customer does | What the agent does in the background |
|---|---|---|
| 1 | Says "I want a personal loan" | |
| 2 | Shares a mobile number, confirms the autofilled OTP | Verifies the OTP |
| 3 | Says how much they need | Pre-fills name, PAN, date of birth, gender and PIN code from a credit bureau |
| 4 | Chooses **SuperAgent** over filling the form manually | |
| 5 | Ticks one consent for Account Aggregator + bank | Finds linked bank accounts |
| 6 | Picks a bank and confirms the bank's OTP | Reads 6 months of statements: salary, average balance, last balance; verifies PAN |
| 7 | Allows a credit report check | Pulls the credit score and runs eligibility |
| 8 | Confirms the offer (can change tenure by voice) | Prices the loan |
| 9 | Reads and accepts the Key Facts Statement | Generates the KFS with APR |
| 10 | Allows file access and shares Aadhaar + salary slip | Reads the documents, extracts the address, cross-checks salary |
| 11 | Confirms the address | |
| 12 | Joins a short video KYC call and shows Aadhaar and PAN | Face and document match |
| 13 | Answers 4 work questions out loud | Verifies the employer |
| 14 | Approves UPI AutoPay | Sets up the mandate |
| 15 | Waits | Submits the application; money arrives within 24 hours |

## Design choices

- **One conversation, one card at a time.** No forms, dashboards or progress bars.
- **Transparent background work.** Each fetch shows as a single live line, then folds into a ✓ chip. Every fetch has a **View records** link showing the source, the reason, what allowed it and the exact fields returned.
- **Voice-first, tap to commit.** Anything can be said out loud, but consents, KFS acceptance, device access and the auto-pay approval need a deliberate tap.
- **Trust cues on every OTP.** Who sent the code, what it is for, and that only that one code is read.
- **Built for Indian speech.** Understands "dedh lakh", "two lakh rupees", phone numbers said digit by digit ("double seven"), and replies in an Indian-English female voice when the device has one.

## How it's built

One self-contained `index.html`: plain HTML, CSS and JavaScript with no build step and no backend.

- Speech in and out uses the browser's Web Speech API, so voice quality depends on the device. Edge on Windows (voice "Neerja") sounds the most natural.
- All services (bureau, Account Aggregator, bank, PAN check, KYC, payments) are deterministic mocks.

To run it locally, download `index.html` and open it in Chrome or Edge. The microphone needs a secure page, so live voice works on the GitHub Pages link or on `localhost`, not from a file opened directly.
