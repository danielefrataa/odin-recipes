# GIT, HTML & CSS

First fundamental I learn at Odin Project

## 1. Git & GitHub Setup
- Set up Git basic + 2FA security on GitHub.
- Git needs to know WHO we are → `git config user.name` & `user.email`.
  → This is the COMMIT AUTHOR LABEL, not authentication.
  → Email must match the one on GitHub for commits to be "verified".
- Authentication to GitHub itself is done by SSH key, NOT by email.

## 2. SSH Key — Check & Generate
- Check existing key:  ls ~/.ssh/id_ed25519.pub
- Generate:            ssh-keygen -t ed25519 -C "email@kamu.com"

## 3. Why ed25519?
- Cryptographic algorithm to create SSH key pairs.
- Compared to RSA (older):
  - Ed25519 = 256-bit, equals RSA 3072-bit security.
  - Key size MUCH smaller, faster signing/verification.
- Modern default for OpenSSH & GitHub.

## 4. Key Pair Concept
- Private key (id_ed25519)      → SECRET, never leaves laptop.
- Public key  (id_ed25519.pub)  → shared to GitHub, safe.
- Passphrase                    → optional lock for private key (recommended).

## 5. Workflow
1. Set git identity (name + email)         → commit author label
2. Generate SSH key (ed25519)              → creates private + public pair
3. Upload PUBLIC key to GitHub             → GitHub verifies signatures
4. Test: ssh -T git@github.com             → should say "successfully authenticated"
5. Clone/push using SSH URL (git@github.com:user/repo.git)

## Windows Note
- ssh-agent is a Windows SERVICE, not `eval`:
  Set-Service ssh-agent -StartupType Automatic
  Start-Service ssh-agent
  ssh-add $env:USERPROFILE\.ssh\id_ed25519