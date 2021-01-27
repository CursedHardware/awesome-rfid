# MIFARE Classic Card kind

- Standard MIFARE Classic Card
  <br>**0 block** is UNWRITABLE.
  <br>UID is randomly by the manufacturer.
  <br>product page: <https://www.mifare.net/en/products/chip-card-ics/mifare-classic/>
  <br>product page: <https://nxp.com/pages/:NTAG-TAGS-AND-LABELS>
  <br>product page: <https://nxp.com/pages/:MF1S50YYX_V1>
  <br>product page: <https://nxp.com/pages/:MF1S70YYX_V1>

- `UID` Card
  <br>all blocks writeable with magic command.
  <br>magic commands can bypass authentication.
  <br>see <https://stackoverflow.com/a/42299452>

- `CUID` Card
  <br>the **UID card** magic command is not processed.
  <br>based standard commands write **0 block**.

- `FUID` Card
  <br>the **UID card** magic command is not processed.
  <br>based standard commands write **0 block** with write once.

- `UFUID` Card
  <br>based on **UID Card**.
  <br>after the locked card, the behavior is consistent with Standard MIFARE Classic Card.
  <br>the lock card is a magic command.
  <br>see <https://web.archive.org/web/20200922151434/http://www.proxmark.org/forum/viewtopic.php?pid=32307>

- `SUID` Card
  <br>based on **CUID Card**.
  <br>after the locked card, the behavior is consistent with Standard MIFARE Classic Card.
  <br>the lock card is a magic command.

- `KUID` Card
  <br>The **UID Card** magic command is not processed.
  <br>based non-standard commands write card.
