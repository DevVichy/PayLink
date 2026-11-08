# PayLink

> A personal Open Payments wallet address for every Nigerian university student.

## The Problem

Sending money to a Nigerian university student should be simple. It is not.

Parents send transfers that arrive hours late or fail entirely. Students get
embarrassed in public when a payment they were expecting has not cleared.
Group contributions — splitting a bill, pooling for a project, collecting
hostel fees — collapse into chaos because everyone transfers to one person
who then becomes a bottleneck, a debtor, and a WhatsApp dispute waiting to happen.

The root cause is not that people lack money or intent. It is that Nigeria's
payment infrastructure is a collection of siloed networks that do not talk to
each other reliably. GTBank does not know Opay. Opay does not know Palmpay.
Every transfer requires knowing the recipient's exact bank name and account
number, and even then it might fail.

## The Solution

PayLink gives every student a wallet address — a permanent, shareable URL like
`paylink.app/victor` — that anyone can use to send them money instantly,
from any bank or mobile wallet, without knowing their account number.

No app download required on the sender's side.
No account details shared.
No failed transfers because of bank incompatibility.

For group contributions, PayLink lets students create a payment pool with a
single link. Every contributor pays their share directly into the pool. The
organiser never holds anyone else's money in transit. Everyone sees the
running total in real time.

## How It Works

PayLink is built on the [Open Payments](https://openpayments.dev) protocol
and [Rafiki](https://rafiki.dev), the open-source Interledger implementation.

When a student signs up:
1. A wallet address is provisioned via the Open Payments wallet address API
2. The student receives a shareable URL and QR code
3. Any sender visits the link and initiates a payment from their Open
   Payments-compatible wallet
4. PayLink creates an incoming payment resource on the recipient's wallet
5. The student sees funds confirmed in real time via webhook notification

Group payment pools use GNAP-based delegated access — a scoped, time-limited
grant that lets contributors pay directly into the pool without the organiser
ever holding funds in custody.

## Tech Stack

- **Frontend:** React, Tailwind CSS, deployed on Vercel
- **Backend:** Node.js, Express, deployed on Railway
- **Database:** PostgreSQL (Supabase)
- **Protocol:** Open Payments API, Rafiki
- **Auth:** University email verification, JWT sessions

## Status

**Stage: design and planning.** This repository currently holds the project
plan and roadmap; implementation starts with the Rafiki sandbox (first item
in the roadmap below). Applying to the
[Interledger Foundation Open Payments Accelerator 2026](https://interledger.org).

User research conducted in-person with students at the University of Lagos
(UNILAG) prior to development. Problem validated across 15 one-on-one
interviews.

## Roadmap

- [ ] Rafiki sandbox environment setup
- [ ] Wallet address creation and resolution (Open Payments API)
- [ ] Incoming payments endpoint integration
- [ ] Student signup and wallet address assignment flow
- [ ] Sender payment page (no login, browser-native)
- [ ] Real-time webhook notifications
- [ ] Student dashboard with QR code and payment history
- [ ] Group payment pool feature
- [ ] Live wallet provider integration (Fynbos or equivalent)
- [ ] UNILAG pilot launch

## Contact

**Nwaokobia Victor**
onyekavictor07@gmail.com
