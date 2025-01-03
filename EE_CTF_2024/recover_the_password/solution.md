# Recover the password
**_Reverse Engineering_** \
Difficulty: Easy

### 1. Initial code
```python
from base64 import b64decode

exec(b64decode(b"ZnJvbSBjcnlwdG9ncmFwaHkuZmVybmV0IGltcG9ydCBGZXJuZXQ="))
exec(b64decode(b"ZmVybmV0a2V5ID0gYidaZmdZX01yRW1nN0dTTzRWZWZMM29YWTdsRVFwQjJJWWlSTm1ZVTRwM0pFPSc="))
exec(b64decode(b"ZiA9IEZlcm5ldChmZXJuZXRrZXkp"))
exec(b64decode(b"ZXhlYyhmLmRlY3J5cHQoYidnQUFBQUFCbWpybFlqZkxWRG5leWdwS1NYWTFNaF8tYUt6cC05YlNMdFR1V3U4UHFXdDQ5enQ3T3RHNVpjZjVwY0huS0lQWEZyRi1RNnktTjFaWUVJY05HdDlTbC15cGFHejhDTUx4RXlQVEtmR3ZpaWhKNmR0OFExQVJzRDh5NmEybkFnblpXM0g1dldPU29fa3Q3UXE1Mi1SQTNvYXNLazZXNXBPTFpVcDFuTVp5Znl1bTVDM0lybzNYZjhZYjhWdmwyWl9kVXNmOGd3VDBrdzZvNTNjaHdGXzNaOUUtbzRheUpablVjRUVjZUJ1WmtLVDZuMUotNlg4TzBmQVRFLUNBVzUzbkktV0szYzBjTVJvN0hHX1d6NGtQWFQ5OVJuZkFURGcyVFRzZE5Wdy1ISVNFUFBKSnBSWTJYNnZFakh6REdMZjh0Z3V1eXNDSWFXVXBrX2NkZ1JSR1ZDSzdHbHhPRU9Hc0MwM2NONnU5dWlBczZoZlhWUHBvRkpuR3c0TVZEaF9fSGNZb3RCaWZYbFozRzl3QjdTOExpZ09zVGNBUXJ1ZDdaQlZKT29pb0xzY3NxVG1HbzdXVHViNnJ2eDl3dWlTTGNxZ2FZeGViWUVielJIS2xLNWhzMnVJTGZKUXhwcFZoUm9FLUs5QVFkbkFNbkVxdjR4TmdBOTkzaHJBWlIxTWZjSC1uTENvOWJDOHVoNDZxOGpKR25BdU5ucGxmdUgzVmlrajMtOXBWOHlrZDU3b1J3M29TQW40MWlBRm5hZVBMemYyQUNXa3c2Z0E5dlBqZ1kxSENERnFtODA4dnpMOS12d2tVOTZvbmNKcGFLb3g3aWoydjlDMnB3N01wcl8ydDdzdm91azI5eXZ6MTh6SVBIVlJIN2NIX3oxQjVHWGhfenA3MzVpR0JOVnZVcS11V1BiNVRfazdpMmIxMnF3bENNSlhaSlFwZjN0OXotM2JkV2xkR1ZoMHNfQTF1RF82em9WUUpFT3pwejRlR29OX0UyUVJyQjU3X2JyN1hUM3hYb09qQXVtc055cHMyU0h5WEtBdlZaV1d3cjM4U25XdHJETzlnak1CNGdZRFVUR2kxOVk3VjZyTlZKSVRKMHZQOEN0Q0MxQ0x3TWZRYVlVY2JBeGhPUHlMaGQzU0xDbUJzSXJOek40enFYcXlnSGczRHVjVlR6b05lNjkwU3htZFhZY2twcG16Z0hjVnYzeE9yY2ZpbDJMQTFYbTBmR01YYWZkWmI0LWlWUGkyemNnT3lfWEFVLVVHSXExQjZXbldZY0xhOTJweGpzSXlMSUhaS2xxUHZGdU1oLXAxVm5MOTZLalZMN29NUVJ0XzVOcFFrUHY1Rk9LX1l0T0VLNG0xRm12RUR0RGVJT2xXOW54Y0hLUG8wbk1TOEU0dW9YRnVzVjRpamNUYTBtb2VIRzk3THA0Zk5hd1VuZ3dZcnRpb3kyNVRQQlNYNFRmQmFhWUs5U1d6QmF3N0U2RVphWHl2cVdXNVY3Sm5vNW9sT3BfRWc3a09YckdwNTMxdWhucVdPZTA3ZjFtczd5aEdCV0FzWERsaHg1Mm9VTTZnPT0nKSkK"))
```

### 2. First base64 decode
```python
from cryptography.fernet import Fernet

fernetkey = b'ZfgY_MrEmg7GSO4VefL3oXY7lEQpB2IYiRNmYU4p3JE='
f = Fernet(fernetkey)
exec(f.decrypt(b'gAAAAABmjrlYjfLVDneygpKSXY1Mh_-aKzp-9bSLtTuWu8PqWt49zt7OtG5Zcf5pcHnKIPXFrF-Q6y-N1ZYEIcNGt9Sl-ypaGz8CMLxEyPTKfGviihJ6dt8Q1ARsD8y6a2nAgnZW3H5vWOSo_kt7Qq52-RA3oasKk6W5pOLZUp1nMZyfyum5C3Iro3Xf8Yb8Vvl2Z_dUsf8gwT0kw6o53chwF_3Z9E-o4ayJZnUcEEceBuZkKT6n1J-6X8O0fATE-CAW53nI-WK3c0cMRo7HG_Wz4kPXT99RnfATDg2TTsdNVw-HISEPPJJpRY2X6vEjHzDGLf8tguuysCIaWUpk_cdgRRGVCK7GlxOEOGsC03cN6u9uiAs6hfXVPpoFJnGw4MVDh__HcYotBifXlZ3G9wB7S8LigOsTcAQrud7ZBVJOoioLscsqTmGo7WTub6rvx9wuiSLcqgaYxebYEbzRHKlK5hs2uILfJQxppVhRoE-K9AQdnAMnEqv4xNgA993hrAZR1MfcH-nLCo9bC8uh46q8jJGnAuNnplfuH3Vikj3-9pV8ykd57oRw3oSAn41iAFnaePLzf2ACWkw6gA9vPjgY1HCDFqm808vzL9-vwkU96oncJpaKox7ij2v9C2pw7Mpr_2t7svouk29yvz18zIPHVRH7cH_z1B5GXh_zp735iGBNVvUq-uWPb5T_k7i2b12qwlCMJXZJQpf3t9z-3bdWldGVh0s_A1uD_6zoVQJEOzpz4eGoN_E2QRrB57_br7XT3xXoOjAumsNyps2SHyXKAvVZWWwr38SnWtrDO9gjMB4gYDUTGi19Y7V6rNVJITJ0vP8CtCC1CLwMfQaYUcbAxhOPyLhd3SLCmBsIrNzN4zqXqygHg3DucVTzoNe690SxmdXYckppmzgHcVv3xOrcfil2LA1Xm0fGMXafdZb4-iVPi2zcgOy_XAU-UGIq1B6WnWYcLa92pxjsIyLIHZKlqPvFuMh-p1VnL96KjVL7oMQRt_5NpQkPv5FOK_YtOEK4m1FmvEDtDeIOlW9nxcHKPo0nMS8E4uoXFusV4ijcTa0moeHG97Lp4fNawUngwYrtioy25TPBSX4TfBaaYK9SWzBaw7E6EZaXyvqWW5V7Jno5olOp_Eg7kOXrGp531uhnqWOe07f1ms7yhGBWAsXDlhx52oUM6g=='))
```

### 3. Result of decryption
```python
a = ''.join(map(chr, map(int, '112 97 115 115 119 111 114 100 32 61 32 105 110 112 117 116 40 34 80 111 100 97 106 32 104 97 115 108 111 58 32 34 41 46 115 116 114 105 112 40 41 10 10 105 102 32 112 97 115 115 119 111 114 100 32 61 61 32 34 75 97 98 101 108 107 105 84 111 83 109 105 101 114 99 52 51 50 53 52 50 51 34 58 10 32 32 32 32 112 114 105 110 116 40 34 83 65 77 65 32 80 82 65 87 68 65 33 34 41 10 32 32 32 32 112 114 105 110 116 40 34 79 116 111 32 116 119 111 106 97 32 102 108 97 103 97 58 32 34 41 10 32 32 32 32 112 114 105 110 116 40 34 69 69 95 67 84 70 123 82 51 118 51 82 53 51 95 116 72 51 95 83 78 52 107 51 95 65 97 50 102 49 95 52 51 106 50 102 125 34 41 10 101 108 115 101 58 10 32 32 32 32 112 114 105 110 116 40 34 66 108 101 100 110 101 32 104 97 115 108 111 33 34 41'.split(' '))))
exec(a)
```

### 4. Actual code
```python
password = input("Podaj haslo: ").strip()

if password == "KabelkiToSmierc4325423":
    print("SAMA PRAWDA!")
    print("Oto twoja flaga: ")
    print("EE_CTF{R3v3R53_tH3_SN4k3_Aa2f1_43j2f}")
else:
    print("Bledne haslo!")
```

### 5. Result
Password: `KabelkiToSmierc4325423` \
Flag: `EE_CTF{R3v3R53_tH3_SN4k3_Aa2f1_43j2f}`