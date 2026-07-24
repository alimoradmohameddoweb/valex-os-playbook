<p align="center">
  <img src="Images/playbook.png" width="128" alt="Valex OS Logo"/>
</p>

<h1 align="center">Valex OS</h1>

<p align="center">
  <strong>The most comprehensive performance, privacy, and stability playbook for Windows 10 & 11</strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#options">Options</a> •
  <a href="#compatibility">Compatibility</a> •
  <a href="#faq">FAQ</a> •
  <a href="#credits">Credits</a>
</p>

---

## What is Valex OS?

Valex OS is an [AME Wizard](https://ameliorated.io) playbook that transforms a stock Windows installation into the fastest, most private, and most stable operating system possible — without reinstalling Windows or breaking core functionality.

This is not a simple debloater. Valex OS is a **complete system re-engineering** with over **820 precisely targeted actions** across 11 phases:

- Every telemetry endpoint is severed
- Every unnecessary service is eliminated
- Every timer and scheduler is tuned for maximum FPS
- Every network stack parameter is optimized
- Every bloatware package is surgically removed
- Every AI/Copilot/Recall component is eliminated
- Windows Defender is toggleable — disable for max FPS or keep enabled for security

> ⚠️ **WARNING**: This playbook makes deep, irreversible changes. Use only on a **fresh Windows installation**. Always create a system image backup before applying.

---

## Features

### 🔒 Privacy & Telemetry Elimination
- **Zero telemetry** — all data collection, diagnostics, and feedback disabled
- **185+ registry values** blocking every known telemetry vector

- **DiagTrack service deleted** with firewall rules blocking outbound
- **WMI autologger sessions** disabled (DiagTrack, SQM, CloudExperience)
- **IFEO process blocking** — CompatTelRunner, DeviceCensus, AggregatorHost killed on launch
- **CLI telemetry opt-out** — PowerShell, .NET CLI, .NET Upgrade Assistant

- **NVIDIA telemetry** disabled at machine and user level

### 🤖 AI / Copilot / Recall Elimination
- Windows Copilot completely disabled (policy + runtime + shell)
- Windows Recall (AI screenshot surveillance) blocked at every level
- AI in Paint, Notepad, and Edge disabled
- Copilot protocol handlers removed (`ms-copilot`, `ms-clicktodo`, `ms-office-ai`)
- Generative AI capability access denied
- BingChat/BGAUpsell/BCILauncher processes blocked via IFEO

### ⚡ Maximum Performance
- **CPU**: Win32PrioritySeparation=38, core parking disabled, CSRSS elevated priority
- **GPU**: Hardware-accelerated scheduling, preemption disabled, DWM frame limiting off
- **MMCSS**: SystemResponsiveness=0, Games profile at max priority, latency-sensitive
- **Memory**: Paging executive disabled, page combining off, Prefetcher=3 (boot+app), Superfetch disabled (SSD-optimized)
- **Disk I/O**: Last access timestamp off, 8.3 names off, NTFS compression off
- **Timer**: High-resolution timer enabled, dynamic tick disabled, TSC Enhanced sync
- **Power**: Ultimate Performance plan, core parking off, power throttling disabled
- **Boot**: 3s timeout, legacy boot menu, first logon animation off, hibernate off
- **Visual**: Best performance mode, instant menus (0ms delay), ClearType preserved

### 🌐 Network Optimization
- TCP auto-tuning with Cubic congestion provider
- Nagle's algorithm disabled globally (TcpNoDelay + TcpAckFrequency)
- DNS over HTTPS (DoH) enabled with reduced cache TTL
- IPv4 preferred over IPv6 (dual-stack preserved), NetBIOS disabled, LMHOSTS disabled
- RSS enabled, DCA enabled, interrupt moderation disabled
- QoS reserved bandwidth set to 0%
- Network adapter power management disabled
- Telemetry IP firewall blocking (defense-in-depth)

### 🛡️ Security Hardening
- **TLS**: SSL 2.0/3.0 and TLS 1.0/1.1 disabled; TLS 1.2/1.3 enforced; insecure renegotiation blocked
- **Ciphers**: RC4, DES, 3DES, RC2, NULL disabled; 2048-bit minimum DH
- **SMB**: v1 disabled, signing required, encryption enabled, guest access blocked
- **NTLM**: NTLMv2 enforced, LM hash storage disabled, NTLM traffic audited
- **.NET**: Strong cryptography enforced across v2.0 and v4.0 (32/64-bit)
- **UAC**: Enabled with consent prompt, installer detection on, no secure desktop, unsigned apps allowed
- **Credentials**: WDigest plaintext caching off, domain logon caching off
- **DEP**: Always on via bcdedit
- **SEHOP**: Exception chain validation enabled
- **DLL**: Safe search order + CWD illegal in DLL search
- **Spectre/Meltdown**: Mitigations disabled (5-30% CPU performance gain; Defender unaffected)
- **VBS/HVCI**: Disabled (5-25% performance gain)
- **Vulnerable Driver Blocklist**: Enabled
- **Autorun/AutoPlay**: Disabled on all drives (USB malware prevention)
- **Windows Script Host**: Disabled when Defender is off (blocks .vbs/.js malware; left enabled when Defender is on since it scans scripts)
- **LLMNR/WPAD**: Disabled (prevents name-resolution poisoning)
- **Remote**: Remote Assistance off, WinRM off
- **Office**: VBA macros, DDE, ActiveX, OLE packages blocked across Office 2007-365
- **Adobe Reader**: JavaScript off, protected mode/view enforced (DC + XI)
- **PowerShell**: Script block logging enabled, RemoteSigned execution policy
- **Certificates**: Authenticode padding check enabled
- **Windows 11 bypass**: TPM, Secure Boot, CPU, RAM, storage checks bypassed

### 🧹 Bloatware Removal
- **40+ AppX packages** removed (including Cortana, Teams, Xbox, Copilot, Widgets)
- **OneDrive** fully uninstalled with folder cleanup and reinstall prevention
- **Edge** update services deleted, AI features disabled, telemetry blocked
- **Windows capabilities** removed (IE mode, Quick Assist, Hello Face, Steps Recorder, WordPad, PowerShell ISE, Math Recognizer)
- **Dynamic deprovisioning** — automatically prevents removed packages from returning after Windows Update
- **30+ third-party bloat** removed (Spotify, Disney+, TikTok, Netflix, CandyCrush, etc.)

### 🎨 Clean Interface
- Classic context menu (Win10 style on Win11)
- Useful "New" file types added (Batch, PowerShell, Registry)
- Dark mode enabled (apps + system + Explorer)
- Taskbar: left-aligned, no search/widgets/chat/copilot/cortana buttons
- Explorer: This PC default, file extensions shown, hidden files visible, compact mode
- Toast notifications and balloon tips disabled (notification center preserved for usability)
- Sticky keys, toggle keys, filter keys popups disabled
- Mouse acceleration disabled for gaming accuracy
- Shortcut arrow overlay removed, "- Shortcut" suffix removed

### 🔄 Windows Update Control
Three user-selectable policies:
1. **Security Updates Only** (recommended) — quality patches only, feature updates deferred 365 days, pinned to current release
2. **Disable All Updates** — complete update lockdown with service/task removal
3. **Keep Default** — leave Windows Update as-is

### 📦 Software Installation
- **Browser choice**: Firefox, Brave, or Chrome (with privacy policies pre-configured)
- **NanaZip**: Modern file archiver based on 7-Zip (optional toggle)
- **VCREDISTs**: Full Visual C++ Runtime stack 2005-2022 with high-reliability MSI extraction (optional toggle)
- **DirectX**: Legacy DirectX June 2010 runtimes (optional toggle)
- **DirectPlay**: Legacy game support for older titles (optional toggle)
- File associations auto-configured for installed software


---

## Installation

### Requirements
- Fresh Windows 10 21H2/22H2 or Windows 11 22H2/23H2/24H2/25H2 installation
- Internet connection
- No pending Windows Updates
- Windows Defender disabled (AME Wizard will guide you to temporarily disable it)
- No third-party antivirus
- Plugged into power (laptops)

### Steps

1. **Download** [AME Wizard](https://ameliorated.io) (latest version)
2. **Download** the latest `valex-os.apbx` from [Releases](https://github.com/alimoradmohameddoweb/valex-os-playbook/releases)
3. **Open** AME Wizard and drag the `.apbx` file into it
4. **Select** your preferred options (browser, features, update policy)
6. **Click** "Run" and wait ~35 minutes for completion
7. **Reboot** when prompted

### Supported Windows Builds
| Build | Version | OS |
|-------|---------|-----|
| 19044 | 21H2 | Windows 10 |
| 19045 | 22H2 | Windows 10 |
| 22621 | 22H2 | Windows 11 |
| 22631 | 23H2 | Windows 11 |
| 26100 | 24H2 | Windows 11 |
| 26120 | 24H2 | Windows 11 |
| 26200 | 25H2 | Windows 11 |

---

## Options

### Windows Defender (RadioPage)
| Option | Description |
|--------|-------------|
| **Disable Defender** | Fully disables Windows Defender via Group Policy, services, drivers, and scheduled tasks for maximum performance |
| **Keep Defender Enabled** (default) | Leave Windows Defender active — recommended if you don't use a third-party antivirus |

### Browser Selection (RadioImagePage)
| Option | Description |
|--------|-------------|
| **Firefox** (default) | Privacy-focused, with telemetry/Pocket/studies disabled via policy |
| **Brave** | Chromium-based with built-in ad blocking; rewards/VPN/wallet/AI disabled |
| **Chrome** | Google Chrome Enterprise with telemetry disabled via policy |
| **None** | Skip browser installation |

### Core System Features (CheckboxPage 1)
| Option | Default | Description |
|--------|---------|-------------|
| Surgical Bloatware Removal | ✅ | Remove 40+ AppX packages + OneDrive + capabilities |
| Absolute Privacy | ✅ | Eliminate all data collection, diagnostics, feedback |
| Ultimate Performance Tuning | ✅ | CPU/GPU/memory/timer/boot/visual optimizations |
| Advanced Network Stack Optimization | ✅ | TCP/IP stack, DNS, Nagle, adapter tuning |

### Additional Customization (CheckboxPage 2)
| Option | Default | Description |
|--------|---------|-------------|
| Streamlined User Interface | ✅ | Taskbar, Explorer, context menu, dark mode, notifications |
| Apply Valex OS UI | ✅ | Set Valex OS branded desktop wallpaper & lock screen |
| Enable Legacy Game Support | ✅ | Enable DirectPlay for older games compatibility |
| Install NanaZip | ✅ | Modern file archiver based on 7-Zip |
| Install Visual C++ Runtimes | ✅ | Full VC++ stack 2005-2022 for app/game compatibility |
| Install Legacy DirectX | ✅ | DirectX June 2010 runtimes for older game support |


> **Note:** Privacy, security hardening, and service optimization are always applied — they are not optional toggles.

### Windows Update Policy (RadioPage)
| Option | Description |
|--------|-------------|
| **Security Only** (default) | Quality patches only, feature updates blocked |
| Disable All | Completely disable Windows Update |
| Keep Default | Leave update behavior unchanged |

---

## Architecture

```
valex-os-playbook/
├── playbook.conf              # AME Wizard configuration (XML)
├── Images/                    # OOBE software icons
│   ├── playbook.png
│   ├── firefox.png
│   ├── brave.png
│   ├── chrome.png
│   └── nanazip.png
├── Configuration/
│   ├── main.yml               # Entry point — 11 phases
│   └── Tasks/
│       ├── privacy.yml        # ~237 actions — telemetry elimination
│       ├── debloat.yml        # ~115 actions — AppX/capability removal
│       ├── services.yml       # ~81 actions — service optimization
│       ├── performance.yml    # ~120 actions — CPU/GPU/memory/timer tuning
│       ├── network.yml        # ~41 actions — TCP/IP/DNS optimization
│       ├── security.yml       # ~145 actions — TLS/SMB/cipher hardening
│       ├── updates.yml        # ~48 actions — Windows Update policy
│       ├── interface.yml      # ~195 actions — shell/taskbar/explorer cleanup
│       ├── cleanup.yml        # ~62 actions — scheduled tasks/file cleanup
│       ├── software.yml       # ~66 actions — browser/tools installation
│       └── finalize.yml       # ~50 actions — cleanup, branding, wallpaper, final tuning
└── Executables/
    └── Media/
        ├── Valex-background.jpg    # Valex OS desktop wallpaper
        └── Valex-lockscreen.jpg    # Valex OS lock screen image
```

### Execution Order
1. **Privacy & Telemetry** → Sever all data collection first
2. **Bloatware Removal** → Remove packages while no telemetry reports it
3. **Service Optimization** → Reduce running services baseline
4. **Performance** → CPU/GPU/memory/timer/boot tuning
5. **Network** → TCP/IP stack and adapter optimization
6. **Security** → TLS/SMB/cipher/credential hardening
7. **Windows Update** → Apply user-selected update policy
8. **Interface** → Shell, taskbar, explorer, dark mode cleanup
9. **Cleanup** → Delete 70+ scheduled tasks and caches
10. **Software** → Install browser, NanaZip, VCREDIST, DirectX
11. **Finalize** → Wallpaper, branding, GPU cache clear, advanced cleanup

---

## FAQ

**Q: Can I undo this?**
A: System Restore is kept enabled with a minimal 3% disk allocation, so restore points are created when drivers or apps are installed. For full rollback, always create a system image backup before applying.

**Q: Will my games still work?**
A: Yes. Game Mode is enabled, Xbox gaming services are disabled but not deleted (re-enable for Game Pass if needed), and GPU/CPU/timer optimizations specifically target gaming performance. Automated VCREDIST and DirectX installation ensures maximum compatibility.

**Q: Will Windows Update still work?**
A: Depends on your selection. "Security Only" keeps critical patches flowing. "Disable All" completely stops updates. "Keep Default" leaves it unchanged.

**Q: Can I re-enable Bluetooth/printing/etc.?**
A: Bluetooth, Print Spooler, and scanner services are set to Manual (start on demand) so they work automatically when you use them. No manual re-enabling needed.

**Q: Is this safe for daily use?**
A: Yes, when installed on a fresh Windows. The playbook disables unnecessary components but preserves all core OS functionality, networking, and driver support.

**Q: Does it work on Windows 10?**
A: Yes. Valex OS supports Windows 10 21H2 (build 19044) and 22H2 (build 19045). Win11-only features (like classic context menu, snap layouts) are automatically skipped on Win10.

---

## Cross-Reference Sources

Valex OS was built by analyzing and cross-referencing the best practices from:

- [Atlas OS](https://atlasos.net) — Service optimization, component removal, cleanmgr engine
- [ReviOS](https://revi.cc) — Performance tuning, timer optimization
- [RapidOS](https://github.com/rapid-community/RapidOS) — NTLM hardening, LSA protection, .NET crypto
- [EudynOS](https://github.com/KarmaDevelopment/EudynOS) — Accessibility cleanup, boot optimization
- [AtmosphereOS](https://github.com/AtmosphereTeam/AtmosphereOS) — Office macro hardening, Adobe security, software resilient downloads
- [ArkanoidOS Lite](https://github.com/jointhearkanoid/playbook) — OOBE cleanup, internet restrictions
- [Privacy+ AME-11](https://github.com/Ameliorated-LLC/privacy_plus) — Copilot elimination, voice activation
- [AME-10-0.8](https://github.com/Ameliorated-LLC/AME-10) — Win10 legacy tweaks, NVIDIA tuning
- [Windows10Debloater](https://github.com/Sycnex/Windows10Debloater) — AppX removal, context menu cleanup
- [winutil](https://github.com/ChrisTitusTech/winutil) — Edge policies, crash display, notification control

Every entry was validated against the [official AME Wizard documentation](https://docs.amelabs.net).

---

## Building from Source

```powershell
git clone https://github.com/alimoradmohameddoweb/valex-os-playbook.git
cd valex-os-playbook
```

---

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).

---

<p align="center">
  <strong>Valex OS 1.0</strong> — Zero telemetry. Maximum FPS. Total control.
</p>




