# AACP Dongle Mods

Independent research and documentation on wireless Android Auto / CarPlay (AACP) dongles — starting with the CarlinKit CPC200-CCPA.

This repository documents **methods**: how the firmware on these dongles is laid out, how to read it off the flash chip, how to change what is inside it, and how to write it back. It is here so anyone can read and check this work, instead of it being kept private.

---

## ⚠️ Read this before anything else

**This work can permanently kill your dongle.**

You are clipping onto a flash chip and overwriting the firmware on it. A bad write, a bad clip contact, or the wrong file leaves you with a dongle that does nothing at all.

- Everything here is **for learning and research only**.
- You are **solely responsible** for whatever you do to your own hardware.
- This will likely **void your warranty**.
- Nothing here is tested or approved by CarlinKit or by any vehicle manufacturer.
- **No warranty of any kind.** If it breaks, you own both pieces.

**Read the whole chip and keep that dump before you change anything.** That file is the only way back.

If you are not comfortable with a SOIC clip, a CH341A programmer and a Linux shell, this repository is not for you.

---

## Does this apply to your dongle?

Open the case and read the flash chip before you start. Dongles sold under the same model name do not always carry the same chip, and the steps here are written around the one below.

| Dongle | Flash chip | Filesystem | Status |
|---|---|---|---|
| **CarlinKit CPC200-CCPA** | `MX25L12835F` | JFFS2 | Documented |

If your dongle is not on this list, nothing here is known to work on it. Post your model and the marking on the flash chip in [Discussions](../../discussions) — that is how the list grows.

---

## The guides

| Guide | What it covers |
|---|---|
| **[VID/PID Mod via CH341A](docs/vid-pid-mod.md)** | Read the flash chip with a CH341A, unpack the JFFS2 rootfs, change the USB VID and PID inside the firmware, repack it and write it back. Done entirely in Ubuntu WSL. |

---

## Why change the VID and PID

Some head units only start a wireless CarPlay session for a dongle whose USB IDs they already know. Change the IDs the dongle reports and the head unit treats it as a device it recognises. The dongle itself works exactly as before — only the two numbers it announces on the USB bus change.

---

## How this project works

This is a **part-time research project**, run by a few people who have full-time jobs. That shapes what you can expect here.

**There is no personal support.** Private messages are not answered, on any platform. Everything happens in [Discussions](../../discussions), in the open, where the answer stays there for the next person with the same question.

The **Issues** tab is switched off on purpose. It is not a mistake — Discussions is the whole of it.

**Discussions has two halves, and they work differently:**

| Category | Who answers |
|---|---|
| **Research & Findings** | Maintainers join in — this is the part of the project we are actually interested in |
| **Help & Questions** | The community answers each other. We read it, but we do not work through it |

Replies take days, not hours. Sometimes longer, and weekends more often than weekdays. Nothing here is guaranteed a reply.

---

## Scope

**In scope**

- Methods, steps and technical explanation
- Firmware layout, file locations and what each value does
- Tools, commands and workflows
- What works, and what does not, across dongle models and chips

**Out of scope**

- Firmware images, flash dumps or unpacked filesystems that belong to the vendor
- Paid modification services
- Requests to do the work for someone

Brand and model names appear here only to say which hardware a method applies to.

---

## Status

Early. Documentation goes up bit by bit, as it is written and checked.

This repository may be archived or left alone at any point, without notice. The licence lets anyone fork it and carry on.

---

## Contributing

What really helps here:

- Telling us a documented method worked — or did not — on your dongle. **Include the model and the marking on the flash chip.** Without them, a result cannot be matched against anyone else's.
- Reports from dongles or chips that are not covered yet
- Corrections and clearer wording for the documentation
- Findings of your own, even partial ones

Post findings in **Research & Findings**. Open a **Pull Request** for changes to the documentation itself.

Please do not attach vendor firmware or flash dumps to anything you send.

If you worked out something this repository gets wrong, say so directly. Being corrected is the point of publishing.

---

## Credits

This work builds on [ludwig-v/wireless-carplay-dongle-reverse-engineering](https://github.com/ludwig-v/wireless-carplay-dongle-reverse-engineering) and the JFFS2 fork [ludwig-v/jefferson_carlinkit](https://github.com/ludwig-v/jefferson_carlinkit), which is what makes the rootfs on these dongles readable at all.

Special thanks to friends [jamesjoe200](https://github.com/jamesjoe200) and [Warcheif81](https://github.com/Warcheif81) for also providing support in terms of information on the hidden APKs, car firmware files, and hardware advice.

---

## Legal

This is independent interoperability research, on hardware the researchers own. It is not affiliated with, authorised by, or endorsed by CarlinKit, Apple, Google, or any vehicle manufacturer. All trademarks belong to their respective owners.

Documentation licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
