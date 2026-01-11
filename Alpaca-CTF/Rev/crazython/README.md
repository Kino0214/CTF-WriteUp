# crazython

## 問題
**crazython.py**
```python
#coding:L1
import zlib,hashlib
b=bytes("""x<9c>ÝXÍn^[7^P¾û)¶¾D^B^R<83>ä<90>CÒ@^N}<8e>Ä(æ×^RêÈ<86>ì´E<83>¼{gm^CÉ½{0²^Wír9Ão¾ùÕ^^\¿<Ü<9f><9f><96>^C=^^î<8e>|ñúx¶<8b>ÃòqùôÎ<80>ç ª^D<99>réZY\r­B^BpD¦Ò«^P'ãn<9c>¥'<93><9a>k*ìX:¨<8e>wï<97>wD4c\r±z¦<9a>½Æv<96>VdÎ Æ<88>d^L<88><98>ÊlÃÕ<89>Ê\0îÙ°*ç^B«^Nµ®<99>{    ^T<96>^P
wñTM½%(2LÜiú¤4ê,¹^U<9e>^Eã´FÝ:6í«<8e>T<81>z^^= ·^X^G<95>FÊ^A<9c>]´I*- ä,¡-t ø,M<93><85>6#^_ó^YG±Bê=÷Î<9d>^F¹*K.<9a>^Qªx^A£^\g¤<92>^\)C^Z©'ÊXSrÆ°ÍV^][p
Þ'sç
<8d>S<83><92>±e%s<85>^PVÁ<91>U^R^F<95>Ø,<96>^L^F@ç1<84>RE5Zu<94>à´H^B<9a>-u²^R[Å^[7h8F£^F0<81>JxEKÍ0ë<9c>=ö<84><81>A<9b>¹àf¾Ý<80>Ó_)>^R»MhÖ<93><84>c¥^K^A¹ô&<96>4   ^U<9f><83>[-ÅR^ZÌ<90>%%Aí<9e>=nIq+[¶<88>±<HÀ:Tð<94>qÌ$-§°ÎÃÀ<82>9ãÔià\r[^E¬e^NHN<9e>&T¯>¬nÅiiÅs<92>^A^XÇ³<84>DjS^R<93><8d>Ò<9a>ñÊjc«<9a>µ³8<8d>©½ÔA£èô<9c>óª^C<9b><84>á¹^Q^N^Lj<99><91>Ùç^Z×uÖÈ^G^^)áHP<83><90>I<93>´FÊdNCbKÑ²ê¨ag<9d>^VÞóÔÊìyf#Í`%+(·^R. 6<8f><9b><80>U'V^^Å¹äà(²1oÅ<87>h<8a>Ì^]\rsí<8c>Ò¸ºGÒ¨<9b>5<8d>¤'<82> ^FÒ<9c>æ<99>Ã¢JbZ\0d<92>[<99>[ñAB2P<92>a<9a>B3ÂiMÞdEID8 E<8d><8a>^E,Ù<83>^[6±¨3#"2b^H=måÛ-êGæ<8c><9c>C^D^FGa×5©º)óhBÔSKZQr^]^Y"Ò<93>^G²<91>|^TÀÀ®<·òË&ñA³<8f><9c>K°É¬BNR 3L* ^R½«^O4÷^Q0¥ZT<98>^Yjzt<8d>\0Z£*mÕçÞJ¿Ý¢ÏmQO^?¥ÜßBÇ^V¶lQ<83>Þ<8a>o·<98>é¶ðË^V}ÿ­púVòåÍôÊ7^R§[Ôä-ú^\^V<89>³:5ÕudÏ^UÃÅ1D^HÔj\râ¼h9-Â½<87>ð¨^UÄ&^V^Fb<8d>MíeN®CmÆC§^ZäOk(:cB§Öjt¢>j'ç´<86>^CZ.Ne<92>tU^O^K<82><85>­f<98>Mr^?<83>9h<8b>ÿ/oå»ÃÿöíÍ<85>ßÑíòq9<9e>^^¾>í.íôdçe]»^.÷W<8f>OçãÃn^?qôåt¿~»¹ò¯ww_èI^N»óåïw^OQ8>^?ûD^_þýãæ^[â÷Ïß/ß?Kï¯<97><87>óñ^T^Z<8f>§¿èî¨<8b>ß<9f>Cn¹Þ]î/ìîÑ®/<96>¸^O_^?>õë^Oùæeõþ¼^\^CÒr¦Ó­í^P÷/»×+ ¼~Qºz<<84>ëp÷,|¼¹²<93>Ü«íöû«<83>ý£Ç[{|Úí<97>ß>.<87>xûCÁz½bûû|^?º}<81>ôó[>^[ýù¼ò^CèORr^?><9b><ý^VRÿ^A^Ob&o""",'L1')
assert hashlib.md5(b).hexdigest()=='c0c42cbe7318e7e7d9c58ca4800e9681','corrupted, you may have broke it during re-saving'
exec(zlib.decompress(b))
```

## 解法
```python zlib.decompress(b)```をdumpする.
```bash
$sed -i 's/^exec(zlib.decompress(b))$/dump=zlib.decompress(b)\nopen("dump.bin","wb").write(dump)/' crazython.py

$cp dump.bin dump.py
```
**dump.py**
```python
import hashlib
import re
h = ['e3b98a4da31a127d4bde6e43033f66ba274cab0eb7eb1c70ec41402bf6273dd8', 'aaa9402664f1a41f40ebbc52c9993eb66aeb366602958fdfaa283b71e64db123',
                                ...                               ,
 '148de9c5a7a44d19e56cd9ae1a554bf67847afb0c58f6e12fa29ac7ddfca9940']
flag = input("enter flag: ").strip()
if not re.fullmatch(r"Alpaca\{[a-z_]{66}\}", flag): print("invalid format :(")
else:
    flag = flag[7:-1]
    for i in range(66):
        if hashlib.sha256(flag[i].encode()).hexdigest() != h[i]:
            print("wrong :(")
            break
    else:
        print("correct!")

```

Alpaca{ ... }の66文字をSHA256で照合しているだけのようです. flagで使用されているのはa-zと"_"の27通りしかないので, 27通りのハッシュを事前計算しておいて逆引きすればできそうです.

**solve.py**
```python
import hashlib

h = ['e3b98a4da31a127d4bde6e43033f66ba274cab0eb7eb1c70ec41402bf6273dd8', ... ]
alphabet = "abcdefghijklmnopqrstuvwxyz_"
rev = {hashlib.sha256(x.encode()).hexdigest(): x for x in alphabet}

inner = "".join(rev[x] for x in h)
print("Alpaca{" + inner + "}")
```
フラグが入手できる
```bash
Alpaca{this_tech_is_used_for_golfing_at_the_google_code_golf_championship}
```