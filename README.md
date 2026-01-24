# ☁️ 1€ Self-Hosted Cloud  

![image](storageproblem.png)


### Replacing Phone & Laptop Storage with Nextcloud

Your phone tells you **“Storage almost full”**.  
Your laptop starts slowing down.  
Photos, videos, documents — everything competes for space.

You look at cloud storage plans:

- €2 here  
- €5 there  
- suddenly it’s another monthly subscription  

I didn’t want that.

What I *did* have was:

- an unused laptop  
- a large hard drive  
- basic Linux knowledge  

So instead of buying more cloud storage, I built my own personal cloud — for about **€1 per month**.

This repository documents that setup.

Not as a perfect solution.  
Not as an enterprise system.  
Just something practical that works.

---

## The idea (in one sentence)

Use hardware you already own to move storage pressure away from phones and laptops — and keep control of your data.

---

## What this is (and what it isn’t)

### ✅ What this setup is
- A personal cloud running at home  
- Built with **Nextcloud**  
- Uses a local disk (internal or external)  
- Fast on your home network  
- Optional public access from anywhere  

### ❌ What this setup is not
- A NAS appliance replacement  
- A zero-maintenance system  
- A cloud service for teams  
- A “plug-and-play” product  

This is for people who are okay with:
- reading logs  
- running commands  
- understanding trade-offs  

---

## The problem this solves

Most people hit storage limits in this order:

1. Phone storage fills up (photos & videos)  
2. Laptop storage fills up  
3. Cloud subscriptions start stacking up  

The devices still work fine — it’s just storage that’s the problem.

This setup changes that flow:

- Phones upload photos → storage freed  
- Laptops sync files → disk pressure reduced  
- Data lives on a larger, cheaper disk at home  

---

## High-level architecture

            Internet
                |
      (optional public access)
                |
          ┌─────────────┐
          │   Small VPS │  (~€1/month)
          │  (Gateway)  │
          └──────┬──────┘
                 │  VPN (WireGuard)
                 │
      ┌──────────▼──────────┐
      │  Home Ubuntu Server │
      │  (unused laptop)   │
      │                    │
      │  Nextcloud (Docker)│
      │                    │
      │  Data stored on:   │
      │  - internal disk  │
      │  - OR external HDD│
      └──────────┬─────────┘
                 │
          Local Network (LAN)
                 │
      Phones • Laptops • Tablets

**Important:**  
The VPS never stores your data.  
It only provides secure access to your home server.

If you don’t need public access, the VPS is optional.

---

## Hardware requirements (minimal)

You don’t need anything fancy.

- Any old laptop or PC that can run Ubuntu  
- Either:
  - a large internal disk, or  
  - an external USB hard drive  

If you already own these, the cost is effectively **zero**.

---

## Local cloud first (LAN-only)

At the core of this setup is **Nextcloud running on Ubuntu**.

Why local-first matters:
- much faster than internet cloud services  
- works even if your internet is down  
- no exposure to the public internet by default  
- ideal for home photo backups  

For many people, LAN-only access is already enough.

---

## Optional: public access from anywhere

Public access is not mandatory.

If you want:
- access while traveling  
- file sharing links  
- HTTPS with a proper domain  

You can add:
- a very small VPS (~€1/month)  
- a VPN tunnel to your home server  
- optional domain + TLS  

This keeps:
- your home network hidden  
- your data stored only at home  

---

## Data migration methods (your choice)

Moving existing data into your cloud is usually a one-time task.  
Different users will prefer different methods.

### Common options

#### **Nextcloud desktop client**
- simple  
- good for small datasets  

#### **scp**
- predictable  
- good for one-off transfers  
- no resume on failure  

#### **rsync** *(recommended for large data)*
- resumable  
- efficient  
- scriptable  
- reliable for unstable connections  

---

## Daily usage (what this feels like)

Once set up, this behaves like a normal cloud:

- phones upload photos automatically  
- laptops sync selected folders  
- files can be shared via links  
- storage pressure disappears from devices  

A common workflow:

1. Photos upload to the cloud  
2. You confirm they’re safely stored  
3. Photos are deleted from the phone  
4. Phone storage is free again  

---

## Backup strategy (important)

This setup is **not a backup by default**.

Recommended:

- a second external hard drive  
- periodic backups of the Nextcloud data directory  
- keep backups offline when not in use  

A rule worth repeating:

> **One copy is not a backup.**  
> **Two copies is the minimum.**

---

## Costs

Typical ongoing costs:

| Item | Cost |
|------|------|
| Old laptop / PC | €0 |
| External hard drive | One-time |
| VPS (optional) | ~€1 / month |
| Domain (optional) | ~€1 / month |
| Cloud storage subscription | €0 |

After setup, the monthly cost is often less than a coffee.

---

## Who this setup is for

✔️ People running out of phone or laptop storage  
✔️ People with unused hardware  
✔️ People comfortable with basic Linux  

---

## Final thoughts

This setup won’t impress anyone with complexity — and that’s the point.

It’s:

- simple  
- affordable  
- understandable  
- under your control  

If you already own unused hardware, this is one of the cheapest ways to stop worrying about storage limits — without handing your data to yet another subscription service.
