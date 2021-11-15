# 真・語意化版本指南

## 摘要
版本格式：**(修訂號・)(次版號)({的|之})主版號**，版號遞增規則如下：

- 主版號：當你做了不相容的 API 修改，
- 次版號：當你做了向下相容的功能性新增，
- 修訂號：當你做了向下相容的問題修正。

先行版號及版本編譯資訊可以加到主版號、次版號、修訂號的後面，作為延伸，中間以（作分隔。

以下是有效的例子：
- 吟唱
- 輝煌的吟唱
- 真・輝煌的吟唱
- 樸素的吟唱
- 龍之吟唱
- 高風險的木雕
- 極・無奈的蟲（我也很無奈）

## 簡介
在軟體管理的領域裡存在著被稱作「相依性地獄」的死亡之谷，系統規模越大，加入的套件越多，你就越有可能在未來的某一天發現自己已深陷絕望之中。

在相依性高的系統中發佈新版本套件可能很快會成為惡夢。如果相依性關係過高，可能面臨版本控制被鎖死的風險（必須對每一個相依套件改版才能完成某次升級）。而如果相依性關係過於鬆散，又將無法避免版本的混亂（假設相容於未來的多個版本已超出了合理數量）。當你專案的進展因為版本相依被鎖死或版本混亂變得不夠簡便和可靠，就意味著你正處於相依性地獄之中。

作為這個問題的解決方案之一，「語意化的版本控制」（SemVer）就出現了，可是冷冰冰的數字，令人們出現只想要更高更快更強的東西，這完全違背眾生平等的理念。也失去了軟體自身能展露的魅力和生命力。

真語意化版本控制（SSemVer）使用了自然文字獨有的模糊感，不單可以解決依賴問題，也令發行版充滿生命力。

## 真語意化版本控制規範（SSemVer）

以下關鍵詞「MUST」、「MUST NOT」、「REQUIRED」、「SHALL」、「SHALL NOT」、「SHOULD」、「SHOULD NOT」、「RECOMMENDED」、「MAY」、「OPTIONAL」依照 RFC 2119 的敘述解讀。

1. 標準的版號必須（MUST）採用 **(Z)・(Y) ({的|之}) X** 的格式，其中 X、Y 和 Z 為 `A-Za-z0-9` 或任何全型文字（推薦），且禁止（MUST NOT）在 X、Y 和 Z 中使用全型或半型括號。X 是主版號、Y 是次版號、而 Z 為修訂號。每個元素可（MAY）以人類的樸素情感來遞增。例如：初生的貓 -> 幼年的貓 -> 成年的貓。
2. 標記版號的軟體發行後，禁止（MUST NOT）改變該版本軟體的內容。任何修改都必須（MUST）以新版本發行。
3. 修訂號 Z 必須（MUST）在只做了向下相容的修正時才遞增。這裡的修正指的是針對不正確結果而進行的內部修改。
4. 次版號 Y 必須（MUST）在有向下相容的新功能出現時遞增。在任何公共 API 的功能被標記為棄用時也必須（MUST）遞增。也可以（MAY）在內部程式有大量新功能或改進被加入時遞增，其中可以（MAY）包括修訂級別的改變。每當次版號遞增時，修訂號建議（RECOMMENDED）為空（）。
5. 主版本號 X 必須（MUST）在有任何不相容的修改被加入公共 API 時遞增。其中可以（MAY）包括次版號及修訂級別的改變。每當主版號遞增時，次版號和修訂號建議（RECOMMENDED）為空（）。
6. 先行版號可以（MAY）被標注在修訂版之後，先加上一個連接號再加上一連串以句點分隔的標識符號來修飾。標識符號必須（MUST）由 Unicode 碼的字和括號`（）` 組成，且禁止（MUST NOT）留白。先行版的優先級不一定低於相關聯的標準版本。被標上先行版號則表示這個版本並非穩定而且可能無法達到相容的需求。範例：`極・無奈的蟲（我也很無奈）`、`好用的工具（不對`、`我愛黎明（被巴飛`。
7. 版本的優先層級指的是不同版本在排序時如何比較。
    1. 判斷優先層級時，必須（MUST）把版本依序拆分為主版號、次版號、修訂號及先行版號後進行比較。
    2. **由右到左**依序比較每個標識符號，第一個差異值用來決定優先層級：主版號、次版號及修訂號以**個人感覺**比較。（例如： 蟲 < 大的蟲 < 老鼠 < 真・老鼠。
    3. Follow Your Heart (跟隨你的心)



## 常見問題（FAQ）

### 可笑，主版號都是個名詞，我要怎麼判斷哪個比較大？難道「大大的狗」就比「大大的貓」大嗎？

隨心選就可以了，嚴格上來說，主版本號的修改意味著互不相容，不相容的兩個物種硬要比較大小才可笑，選一個你喜歡的，或者最新的，這就是一般人的做法。


### 我要怎麼判斷次版號的形容詞？難道堅硬的劍一定比狂龍之劍弱嗎？

你要跟隨你的個人判斷，Follow Your Heart，假設**狂龍**比**堅硬**強，雖然狂龍之劍兼容堅硬之劍的所有API，但也不表示你不能用堅硬之劍吧，很多時候，夠用就好。像蘋果一樣吹噓自己多少百分比的用戶都已經升到最新版本，很多時不過是商業行為而已。你喜歡**堅硬的**多於**狂龍之**，這本來就是一種緣份，相信緣份比起一味的慕強踏實多了。

### 這不會阻礙快速開發和迭代嗎？
不會，相反，可以為版本創作一個帥氣或可愛的名字，有助推動快速開發和迭代。

### “v煌華之舞” 是語意化版本嗎？
是的，不同於弱雞的SemVer，連個v 字都支持不了。SSemVer 容許你加入你想要加的前綴。只要你們都能理解就可以了。

### 有建議用於檢查語意化版本的正規表示式（RegEx）嗎？

有。`^((.+)([的之]))?([^（\n]+)(（.+)?$`

參見：https://regex101.com/r/H1v6S1/1/
