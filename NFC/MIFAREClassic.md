# MIFARE Classic Manual

## Card Kind

- Standard MIFARE Classic Card, **0 block** is UNWRITABLE. \
  UID is randomly by the manufacturer. \
  Product page: <https://www.mifare.net/en/products/chip-card-ics/mifare-classic/> \
  Product page: <https://nxp.com/pages/:NTAG-TAGS-AND-LABELS> \
  Product page: <https://nxp.com/pages/:MF1S50YYX_V1> \
  Product page: <https://nxp.com/pages/:MF1S70YYX_V1>

- **UID Card**, all blocks writeable with magic command. \
  magic commands can bypass authentication. \
  see <https://stackoverflow.com/a/42299452>

- **CUID Card**, The **UID Card** magic command is not processed. \
  based standard commands write **0 block**.

- **FUID Card**, The **UID Card** magic command is not processed. \
  based standard commands write **0 block** with write once.

- **UFUID Card** based on **UID Card**. \
  after the locked card, the behavior is consistent with Standard MIFARE Classic Card. \
  the lock card is a magic command. \
  see <https://web.archive.org/web/20200922151434/http://www.proxmark.org/forum/viewtopic.php?pid=32307>

- **SUID Card** based on **CUID Card**. \
  after the locked card, the behavior is consistent with Standard MIFARE Classic Card. \
  the lock card is a magic command.

- **KUID Card**, The **UID Card** magic command is not processed. \
  based non-standard commands write card.

## Cracker Tools

- [Mifare Classic Offline Cracker](https://github.com/nfc-tools/mfoc)
- [MIFARE Classic Universal toolkit](https://github.com/nfc-tools/mfcuk)
- [Mifare Offline Cracking GUI for Windows](https://www.huuf.info/OV/)
- [Proxmark 3](https://github.com/Proxmark/proxmark3)
- [Chameleon Mini](https://github.com/emsec/ChameleonMini)
