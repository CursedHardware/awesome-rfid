# Read UID of R.P.C China Identity Card

- Reader require Need support **ISO14443 Type B** protocol
  <br>e.g: PN53x, PN5180

## Read UID Logic

| Action           | Data                                  |
| ---------------- | ------------------------------------- |
| Send `REQB`      | `05 00 00`                            |
| Receive `ATQB`   | `50 00 00 00 00 D1 03 86 0C 00 80 80` |
| Send `ATTRIB`    | `1D 00 00 00 00 00 08 01 08`          |
| Receive `ATTRIB` | `08`                                  |
| Send UID Command | `00 36 00 00 08`                      |
| Receive `UID`    | `** ** ** ** ** ** ** ** 90 00`       |

## PN532 Registry

```c
pn53x_write_register(pnd, PN53X_REG_CIU_Mode, 0xff, 0xff);
pn53x_write_register(pnd, PN53X_REG_CIU_TxAuto, 0xff, 0x00);
pn53x_write_register(pnd, PN53X_REG_CIU_TxMode, 0xff, 0x03);
pn53x_write_register(pnd, PN53X_REG_CIU_RxMode, 0xff, 0x03);
pn53x_write_register(pnd, PN53X_REG_CIU_TypeB, 0xff, 0x03);
pn53x_write_register(pnd, PN53X_REG_CIU_Demod, 0xff, 0x4d);
pn53x_write_register(pnd, PN53X_REG_CIU_GsNOn, 0xff, 0xff);
pn53x_write_register(pnd, PN53X_REG_CIU_CWGsP, 0xff, 0x3f);
pn53x_write_register(pnd, PN53X_REG_CIU_ModGsP, 0xff, 0x18);
pn53x_write_register(pnd, PN53X_REG_CIU_RxThreshold, 0xff, 0x4d);
pn53x_write_register(pnd, PN53X_REG_CIU_ModWidth, 0xff, 0x68);
pn53x_write_register(pnd, PN53X_REG_CIU_ManualRCV, 0xff, 0x10);
```

## PN532 Reading code

```c
uint8_t PUPI[4];

uint8_t REQB[5] = { 0x05, 0x00, 0x00 };
iso14443b_crc_append(REQB, 3);
transmit_bytes(REQB, 5);    // Send REQB
memcpy(PUPI, abtRx + 1, 4); // Copy PUIP in ATQB

printf("PUPI: ");
print_hex(PUPI, 4);

uint8_t Attrib[11] = { 0x1d, 0x00, 0x00, 0x00, 0x00, 0x00, 0x08, 0x01, 0x01 };
memcpy(Attrib + 1, PUPI, 4);
iso14443b_crc_append(Attrib, 9);
transmit_bytes(Attrib, 11);  // Send ATTRIB

uint8_t ReadGUID[7] = {0x00, 0x36, 0x00, 0x00, 0x08};
iso14443b_crc_append(ReadGUID, 5);
transmit_bytes(ReadGUID, 7); // Send Read UID Command

nfc_close(pnd);
nfc_exit(context);
exit(EXIT_SUCCESS);
```

## References

- [RPC-Identify-UID-Archived.md](RPC-Identify-UID-Archived.md)
- <https://archive.is/18eP5>
- <https://archive.is/4dyRt>
- <https://archive.is/ecX6q>
- <https://archive.is/FCTsO>
- <https://www.nxp.com/docs/en/user-guide/141520.pdf>
