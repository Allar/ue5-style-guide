# [Gamemakin](https://gamemak.in) UE4 Style Guide() {

*A mostly reasonable approach to Unreal Engine 4*

Heavily inspired by the [Airbnb Javascript Style Guide](https://github.com/airbnb/javascript).

[![Analytics](https://ga-beacon.appspot.com/UA-80567399-1/repo?useReferrer)](#)

## Repo Notice

This repo is now located at https://github.com/Allar/ue5-style-guide. The default branch of this repository has been renamed `main`.



## Table of contents
- [Các thuật ngữ quan trọng](#important-terminology)
  - [Levels/Maps - Bản đồ](#terms-level-map)
  - [Identifiers - Định danh / Tên gọi](#terms-identifiers)
  - [Cases - Quy chuẩn chữ cái](#terms-cases)
  - [Variables / Properties - Biến / Thuộc tính](#terms-var-prop)
    - [Property - Thuộc tính](#terms-property)
    - [Variable - Biến](#terms-variable)
- [0. Principles - Nguyên tắc cơ bản](#0)
  - [0.1 Nếu project đã có quy chuẩn thì bám theo quy chuẩn của project](#0.1)
  - [0.2 Tất cả cấu trúc, assets và mã nguồn trong một dự án UE phải thống nhất một theo một thể không cần biết có bao nhiêu người cùng tham gia dự án](#0.2)
  - [0.3 Nhắc nhở phạm quy và cùng khắc phục](#0.3)
  - [0.4 Một team mà không có guide line thì không phải là một team](#0.4)
  - [0.5 Đừng phá luật](#0.5)
- [00. Yêu cầu chung](#00)
  - [00.1 Những ký tự bị cấm](#00.1)
    - [Identifiers - Định danh](#identifiers)
- [1. Quy tắc đặt tên cho Asset](#anc)
  - [1.1 Tên Asset - `Prefix_BaseAssetName_Variant_Suffix` - `TiềnTố_TênCơSở_BiếnThể_HậuTố`](#base-asset-name)
    - [1.1 Ví dụ](#1.1-examples)
  - [1.2 Phần bổ nghĩa cho tên Asset](#asset-name-modifiers)
    - [1.2.1 Phổ biến nhất](#anc-common)
    - [1.2.2 Animations](#anc-animations)
  - [1.2.3 Artificial Intelligence](#anc-ai)
  - [1.2.4 Blueprints](#anc-bp)
  - [1.2.5 Materials](#anc-materials)
  - [1.2.6 Textures](#anc-textures)
    - [1.2.6.1 Texture Packing](#anc-textures-packing)
  - [1.2.7 Miscellaneous - Khác](#anc-misc)
  - [1.2.8 Paper 2D](#anc-paper2d)
  - [1.2.9 Physics](#anc-physics)
  - [1.2.10 Sounds](#anc-sounds)
  - [1.2.11 User Interface](#anc-ui)
  - [1.2.12 Effects](#anc-effects)
- [2. Cấu trúc thư mục](#structure)
  - [2e1 Ví dụ về cấu trúc thư mục](#2e1)
  - [2.1 Tên thư mục](#structure-folder-names)
    - [2.1.1 Luôn dùng PascalCase](#2.1.1)
    - [2.1.2 Không bao giờ dùng dấu cách](#2.1.2)
    - [2.1.3 Không dùng các ký tự Unicode, vd: chữ có dấu](#2.1.3)
  - [2.2 Sử dụng thư mục cấp cao nhất cho dự án](#structure-top-level)
    - [2.2.1 Không dùng Assets toàn cục / No Global Assets](#2.2.1)
    - [2.2.2 Giảm rủi ro xung đột Migration](#2.2.2)
      - [2.2.2e1 Ví dụ vật liệu chủ / Master Material Example](#2.2.2e1)
    - [2.2.3 Samples, Templates, và nội dung Marketplace Content Are Risk-Free](#2.2.3)
    - [2.2.4 DLC, Sub-Projects, and Patches dễ duy trì](#2.2.4)
  - [2.3 Sử dụng thư mục developer cho thử nghiệm](#structure-developers)
  - [2.4 Tất cả file map<sup>*</sup> đều phải để trong thư mục Maps](#structure-maps)
  - [2.5 Sử dụng thư mục `Core` cho những Blueprint và Assets cốt lõi](#structure-core)
  - [2.6 Không tạo thư mục tên `Assets` hoặc `AssetTypes`](#structure-assettypes)
    - [2.6.1 Tạo thư mục `Assets` là dư thừa](#2.6.1)
    - [2.6.2 Tạo thư mục tên `Meshes`, `Textures`, hoặc `Materials` là dư thừa](#2.6.2)
  - [2.7 Asset đồ sộ cần layout thư mục riêng của nó](#structure-large-sets)
  - [2.8 `MaterialLibrary`](#structure-material-library)
  - [2.9 Không thư mục trống](#structure-no-empty-folders)
- [3. Blueprints](#bp)
  - [3.1 Biên dịch ](#bp-compiling)
  - [3.2 Biến](#bp-vars)
    - [3.2.1 Đặt tên](#bp-var-naming)
      - [3.2.1.1 Danh từ](#bp-var-naming-nouns)
      - [3.2.1.2 PascalCase](#bp-var-naming-case)
        - [3.2.1.2e Ví dụ](#3.2.1.2e)
      - [3.2.1.3 Tiền tố Boolean `b`](#bp-var-bool-prefix)
      - [3.2.1.4 Tên Boolean ](#bp-var-bool-names)
        - [3.2.1.4.1 Thông tin chung và độc lập](#3.2.1.4.1)
        - [3.2.1.4.2 Trạng thái phức hợp](#3.2.1.4.2)
      - [3.2.1.5 Xem xét ngữ cảnh](#bp-vars-naming-context)
        - [3.2.1.5e Ví dụ](#3.2.1.5e)
      - [3.2.1.6 Không thêm kiểu biến đơn giản vào tên](#bp-vars-naming-atomic)
      - [3.2.1.7 Hãy thêm kiểu biến phức hợp vào tên](#bp-vars-naming-complex)
      - [3.2.1.8 Arrays / Mảng](#bp-vars-naming-arrays)
    - [3.2.2 Biến có khả năng chỉnh sửa](#bp-vars-editable)
      - [3.2.2.1 Tooltips](#bp-vars-editable-tooltips)
      - [3.2.2.2 Slider và khoảng giá trị](#bp-vars-editable-ranges)
    - [3.2.3 Danh mục](#bp-vars-categories)
    - [3.2.4 phạm vi truy cập của biến](#bp-vars-access)
      - [3.2.4.1 Biến riêng tư](#bp-vars-access-private)
    - [3.2.5 Hiển thị nâng cao ](#bp-vars-advanced)
    - [3.2.6 Biến tạm thời(Transient)](#bp-vars-transient)
    - [3.2.8 Biến thiết lập](#bp-vars-config)
  - [3.3 Hàm, Sự kiện, Phát sự kiện](#bp-functions)
    - [3.3.1 Đặt tên hàm](#bp-funcs-naming)
    - [3.3.1.1 Tất cả hàm nên là động từ](#bp-funcs-naming-verbs)
    - [3.3.1.2 Trả lời thông báo biến (Property RepNotify Functions) luôn luôn là `OnRep_Variable`](#bp-funcs-naming-onrep)
    - [3.3.1.3 Hàm trả giá trị đúng-sai nên đặt tên dạng câu hỏi đúng sai](#bp-funcs-naming-bool)
    - [3.3.1.4 Xử lý sự kiện(Event Handler) và phát sự kiện(Event Dispatcher) nên bắt đầu bằng `On`](#bp-funcs-naming-eventhandlers)
    - [3.3.1.5 Thủ tục gọi từ xa nên có tiền tố là mục tiêu](#bp-funcs-naming-rpcs)
    - [3.3.2 Tất cả hàm phải có node Return](#bp-funcs-return)
    - [3.3.3 Không hàm nào nên có quá 50 Nodes](#bp-graphs-funcs-node-limit)
    - [3.3.4 Tất cả hàm công khai phải có mô tả](#bp-graphs-funcs-description)
    - [3.3.5 Tất cả hàm của Plugin `BlueprintCallable` phải được phân loại bởi tên plugin ](#bp-graphs-funcs-plugin-category)
  - [3.4 Đồ hình Blueprint](#bp-graphs)
    - [3.4.1 Không để các đường dây rối như mớ bòng bong](#bp-graphs-spaghetti)
    - [3.4.2 Căn theo đường nối, không phải nodes](#bp-graphs-align-wires)
    - [3.4.3 Đường thực thi là ưu tiên số 1](#bp-graphs-exec-first-class)
    - [3.4.4 Đồ hình nên có comment hợp lý](#bp-graphs-block-comments)
    - [3.4.5 Đồ hình nên xử lý ngoại lệ Casting phù hợp](#bp-graphs-cast-error-handling)
    - [3.4.6 Đồ hình không nên có node treo, node không sử dụng](#bp-graphs-dangling-nodes)
- [4. Static Meshes - Lưới tĩnh](#4)
  - [4.1 UV lưới tĩnh (Static Meshes)](#s-uvs)
    - [4.1.1 Tất cả lưới phải có UV](#s-uvs-no-missing)
    - [4.1.2 Tất cả lưới phải có UV cho Lightmaps(UV không chồng đè)](#s-uvs-no-overlapping)
  - [4.2 LODs phải được setup đúng](#s-lods)
  - [4.3 Các asset module phải bắt dính vào lưới](#s-modular-snapping)
  - [4.4 Tất cả lưới phải có Collision](#s-collision)
  - [4.5 Tất cả lưới phải đúng tương quan tỉ lệ đời thực](#s-scaled)
- [5. Niagara](#Niagara)
  - [5.1 Không bao giờ dùng dấu cách](#ng-rules)
- [6. Levels / Maps](#levels)
  - [6.1 Không lỗi, không cảnh báo](#levels-no-errors-or-warnings)
  - [6.2 Ánh sáng phải build](#levels-lighting-should-be-built)
  - [6.3 Không Z Fighting đối với người chơi](#levels-no-visible-z-fighting)
  - [6.4 Luật của Marketplace](#levels-mp-rules)
    - [6.4.1 Bản đồ Tổng quát](#levels-mp-rules-overview)
    - [6.4.2 Bản đồ demo](#levels-mp-rules-demo)
- [7. Textures](#textures)
  - [7.1 Độ phân giải phải là luỹ thừa của 2](#textures-dimensions)
  - [7.2 Mật độ texture nên đồng nhất](#textures-density)
  - [7.3 Texture không nên to hơn 8192](#textures-max-size)
  - [7.4 Texture nên được nhóm đúng](#textures-group)

## Các thuật ngữ quan trọng

<a name="terms-level-map"></a>
##### Levels/Maps
Map hoặc level: 2 từ này có thể dùng tráo đổi cho nhau, cùng chỉ về một không gian người chơi có thể tương tác, tiếp xúc.
(https://en.wikipedia.org/wiki/Level_(video_gaming)).

<a name="terms-identifiers"></a>
##### Identifiers - Định danh
Một `Identifier` là bất cứ gì đóng vai trò "tên gọi". Ví dụ, tên của một asset, or tên của một vật liệu, or a thuộc tính, biến của blueprint property, hay tên của một folder, hoặc tên một hàng trong bảng dữ liệu, v.v...

<a name="terms-cases"></a>
##### Cases - Quy chuẩn đặt tên

Có một vài cách đặt tên thường dùng `CaseWordsWhenNaming`. Dưới đây là một số kiểu phổ biến:

> ###### PascalCase
>
> Viết hoa tất cả các chữ cái đầu tiên của mỗi từ, e.g. `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
>
> ###### camelCase
>
> Chữ cái đầu tiên của từ đầu tiên luôn viết thường, tất cả chữ cái của các từ còn lại viết hoa, e.g. `desertEagle`, `styleGuide`, `aSeriesOfWords`.
>
> ###### Snake_case
>
> Mỗi từ có thể viết hoa hoặc không viết hoa chữ cái đầu tiên nhưng được phân cách bởi dấu gạch dưới e.g. `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

<a name="terms-var-prop"></a>
##### Variables / Properties - Biến / Thuộc tính

Trong hầu hết trường hợp 2 từ 'variable' và 'property' có thể dùng tráo đổi cho nhau. Nếu 2 từ được dùng chung trong cùng một ngữ cảnh:

<a name="terms-property"></a>
###### Property - Thuộc tính
Thường chỉ đến các biến được định nghĩa trong lớp (class). Ví dụ: nếu `BP_Barrel` có một biến `bExploded`, thì `bExploded` được nói là một thuộc tính của lớp `BP_Barrel`.

Khi trong ngữ cảnh của lớp (class), nó thường ngầm định cho việc truy cập dữ liệu định nghĩa trước.

<a name="terms-variable"></a>
###### Variable - Biến
Usually refers to a variable defined as a function argument or a local variable inside a function.

When in the context of a class, it is often used to convey discussion about its definition and what it will hold.

<a name="0"></a>
## 0. Nguyên tắc

Những nguyên tắc này được sửa đổi dựa theo  [idomatic.js style guide](https://github.com/rwaldron/idiomatic.js/).

<a name="0.1"></a>
### 0.1 Nếu dự án của bạn đã có quy chuẩn, bạn nên tuân theo quy chuẩn của nó.
Nếu bạn làm với một dự án của một team đã có quy chuẩn, bạn nên tôn trọng quy chuẩn đó. Ứu tiên quy chuẩn có sẵn trước quy chuẩn này.

Quy chuẩn là chết, con người là sống. Bạn nên đề xuất thay đổi đối với những quy chuẩn có sẵn sao cho phù hợp với tình hình thực tế.

> #### "Tranh luận về quy chuẩn là vô nghĩa. Cần phải có một quy chuẩn và bạn nên tuân thủ nó."
> [_Rebecca Murphey_](https://rmurphey.com)

<a name="0.2"></a>
### 0.2 Mọi cấu trúc, assets, và mã lệnh trong dự án nên thống nhất như một người phát triển cho dù số người tham gia dự án > 1.

Chuyển từ dự án này sang dự án khác không để tình trạng học lại cấu trúc và quy chuẩn. Tuân thủ nghiêm khắc quy chuẩn sẽ triệt tiêu sự phán đoán mơ hồ không cần thiết.
Điều này cho phép nâng cao hiệu suất làm việc, sáng tạo, duy trì bởi mỗi cá nhân không cần phải suy nghĩ nhiều về các quy chuẩn riêng. Đơn giản là làm theo quy chuẩn. Quy chuẩn này được viết với những nhu cầu thực tế nhất, tuân theo quy chuẩn này bạn sẽ tối thiểu hoá việc phải truy tìm những lỗi khó hiểu.

<a name="0.3"></a>
### 0.3 Anh em đồng nghiệp đừng để anh em đồng nghiệp phạm quy. Nếu thấy lỗi thì bảo nhau sửa nhé.

Khi làm việc trong nhóm hoặc thảo luận với cộng đồng (discord/reddit/forum/stackOverFlow...). Sẽ dễ dàng hơn nếu muốn tìm kiếm sự trợ giúp cho những người làm việc có quy chuẩn. Không ai thích nhìn vào mớ bòng bong đồ hình Blueprint với những cái tên vô nghĩa, khó hiểu.

Khi giúp người nào đó nếu họ có quy chuẩn của họ, hay sử dụng nó, nếu họ không có quy chuẩn thì dắt vào đây.

<a name="0.4"></a>
### 0.4 Một team không có quy chuẩn không phải là một team

<a name="0.5"></a>
### 0.5 Đừng phá luật

Tôn trọng bản quyền, pháp luật:

* Không xuất bản nội dung mà bạn không có quyền xuất bản.
* Không vi phạm bản quyền hay thương hiệu của người khác.
* Không ăn cắp nội dung
* Tuân thủ các giới hạn bản quyền về nội dung.

<a name="00"></a>
## 00. Những điểm bắt buộc toàn diện

@TODO: Make this section 1 and update this document accordingly. Or maybe we don't?

<a name="00.1"></a>
### 00.1 Ký tự bị cấm

<a name="identifiers-1"></a>
#### Những định danh

Bất cứ `Identifier` của bất cứ loại nào, **không bao giờ** sử dụng trừ khi bắt buộc phải:

* Bất cứ kiểu ký tự khoảng trắng nào (space, tab, empty character ...)
* Dấu gạch chéo ngược `\`
* Biểu tượng vd: `#!@$%`
* Các ký tự Unicode

Bất cứ `Identifier` chỉ nên có các ký tự sau đây(the RegEx `[A-Za-z0-9_]+`)

* ABCDEFGHIJKLMNOPQRSTUVWXYZ
* abcdefghijklmnopqrstuvwxyz
* 1234567890
* _ (hạn chế)

Lý do cho việc này để đảm bảo tính tương thích cao nhất cho tất cả dữ liệu trên tất cả các nền tảng, công cụ, ngăn ngừa downtime do việc xử lý các ký tự xấu trong định danh ở các phần mã lệnh bạn không kiểm soát được

<a name="anc"></a>
<a name="1"></a>
## 1. Quy tắc đặt tên Asset

Quy tắc đặt tên Asset phải được coi như luật. Một dự án tuân thủ quy tắc đặt tên các asset sẽ dễ dàng quản lý, tìm kiếm, phân loại, bảo trì, duy trì.

Hầu hết mọi thứ đều có tiền tố là từ viết tắt cho kiểu asset tiếp đến là dấu gạch nối.

<a name="base-asset-name"></a>
<a name="1.1"></a>
### 1.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`
Trong đó: 
Prefix: Tiền tố
Base Asset Name: Tên cơ sở
Variant: Biến thể
Suffix: Hậu tố

Tất cả assets phải có _BaseAssetName_. Base name là một nhóm các asset liên quan đến nhau một cách logic. Các asset cùng một nhóm phải tuân thủ quy tắc `Prefix_BaseAssetName_Variant_Suffix`.

Tên asset phải mang tính gợi ý đến chủ thể, chức năng, tính chất của asset. Sau đây là một số quy tắc chi tiết.

`Prefix` và `Suffix` được đặt bởi kiểu asset theo bảng bổ nghĩa [Asset Name Modifier](#asset-name-modifiers).

`BaseAssetName` nên được đặt một cách ngắn gọn, dễ nhận hiểu và liên quan tới bối cảnh của nhóm asset. Ví dụ: Nếu bạn có một nhân vật tên là Bob, tất cả asset liên quan tới Bob phải có tên cơ sở `BaseAssetName` == `Bob`.

Cho những biến thể đặc biệt của assets, `Variant` cần ngắn, dễ hiểu, thể hiện một cách logic về nhóm assets và tập hợp con của nhóm assets. Ví dụ: Nếu Bob có nhiều bề ngoài khác nhau, mỗi bề ngoài cần phải dùng `Bob` làm tên cơ sở nhưng có thêm phần biến thể `Variant`. Một Bob tàn ác sẽ được đặt tên là `Bob_TanAc` và Bob cổ điển sẽ được đặt tên là `Bob_CoDien`. Nên đặt tên bằng tiếng Anh sẽ ngắn gọn và xúc tích hơn. Ví dụ: `Bob_Evil`, `Bob_Retro`.


Cho những biến thể của các asset phổ thông. `Variant` dùng 2 chữ số bắt đầu từ `01`. Ví dụ cho những hòn đá không có gì đặc biệt `Rock_01`, `Rock_02`, `Rock_03`... Trừ những trường hợp vô cùng hiếm không nên để quá 3 chữ số. Nếu có hơn 100 assets đặt tên như vậy thì nên suy nghĩ về việc đặt lại tên cơ sở, hoặc nhiều tên biến thể hơn.

Tuỳ thuộc vào tên biến thể, chúng ta có thể ghép nối các phần biến thể với nhau. Ví dụ:
Các asset sàn nhà `Flooring` cho một dự án Arch Viz `Flooring` với các phần biến thể ghép như sau `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

<a name="1.1-examples"></a>
#### 1.1 Ví dụ

##### 1.1e1 Bob

| Kiểu Asset              | Tên Asset                                                  |
| ----------------------- | ---------------------------------------------------------- |
| Skeletal Mesh           | SK_Bob                                                     |
| Material                | M_Bob                                                      |
| Texture (Diffuse/Albedo)| T_Bob_D                                                    |
| Texture (Normal)        | T_Bob_N                                                    |
| Texture (Evil Diffuse)  | T_Bob_Evil_D                                               |

##### 1.1e2 Rocks

| Kiểu Asset              | Asset                                                      |
| ----------------------- | ---------------------------------------------------------- |
| Static Mesh (01)        | S_Rock_01                                                  |
| Static Mesh (02)        | S_Rock_02                                                  |
| Static Mesh (03)        | S_Rock_03                                                  |
| Material                | M_Rock                                                     |
| Material Instance (Snow)| MI_Rock_Snow                                               |

<a name="asset-name-modifiers"></a>
<a name="1.2"></a>
### 1.2 Phần bổ nghĩa cho tên Asset

When naming an asset, use these tables to determine the prefix and suffix to use with an asset's [Base Asset Name](#base-asset-name).

<a name="anc-common"></a>
<a name="1.2.1"></a>
#### 1.2.1 Most Common

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Map             |            |            | [Phải ở trong thư mục tên Map](#2.4) |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Blueprint               | BP_        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | S_         |            | Nhiều nơi dùng SM_. Chúng ta dùng S_.         |
| Skeletal Mesh           | SK_        |            |                                  |
| Texture                 | T_         | _?         | Xem [Textures](#anc-textures)    |
| Particle System         | PS_        |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-animations"></a>
<a name="1.2.2"></a>
#### 1.2.2 Animations

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Aim Offset              | AO_        |            |                                  |
| Aim Offset 1D           | AO_        |            |                                  |
| Animation Blueprint     | ABP_       |            |                                  |
| Animation Composite     | AC_        |            |                                  |
| Animation Montage       | AM_        |            |                                  |
| Animation Sequence      | A_         |            |                                  |
| Blend Space             | BS_        |            |                                  |
| Blend Space 1D          | BS_        |            |                                  |
| Level Sequence          | LS_        |            |                                  |
| Morph Target            | MT_        |            |                                  |
| Paper Flipbook          | PFB_       |            |                                  |
| Rig                     | Rig_       |            |                                  |
| Skeletal Mesh           | SK_        |            |                                  |
| Skeleton                | SKEL_      |            |                                  |

<a name="anc-ai"></a>
<a name="1.2.3"></a>
### 1.2.3 Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_       |            |                                  |
| Behavior Tree           | BT_        |            |                                  |
| Blackboard              | BB_        |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_    |            |                                  |
| Environment Query       | EQS_       |            |                                  |
| EnvQueryContext         | EQS_       | Context    |                                  |

<a name="anc-bp"></a>
<a name="1.2.4"></a>
### 1.2.4 Blueprints

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Blueprint               | BP_        |            |                                  |
| Blueprint Component     | BP_        | Component  | I.e. BP_InventoryComponent       |
| Blueprint Function Library | BPFL_   |            |                                  |
| Blueprint Interface     | BPI_       |            |                                  |
| Blueprint Macro Library | BPML_      |            | Không dùng thư viện Macro nếu có thể. |
| Enumeration             | E          |            | Không gạch dưới.                   |
| Structure               | F or S     |            | Không gạch dưới.                   |
| Tutorial Blueprint      | TBP_       |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-materials"></a>
<a name="1.2.5"></a>
### 1.2.5 Materials

| Asset Type                    | Prefix     | Suffix     | Notes                            |
| ----------------------------- | ---------- | ---------- | -------------------------------- |
| Material                      | M_         |            |                                  |
| Material (Post Process)       | PP_        |            |                                  |
| Material Function             | MF_        |            |                                  |
| Material Instance             | MI_        |            |                                  |
| Material Parameter Collection | MPC_       |            |                                  |
| Subsurface Profile            | SP_        |            |                                  |
| Physical Materials            | PM_        |            |                                  |
| Decal                         | M_, MI_    | _Decal     |                                  |

<a name="anc-textures"></a>
<a name="1.2.6"></a>
### 1.2.6 Textures

| Kiểu Asset              | Prefix - Tiền tố     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _O         |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Metallic)      | T_         | _M         |                                  |
| Texture (Packed)        | T_         | _*         | Xem ghi chú phía dưới [packing](#anc-textures-packing). |
| Texture Cube            | TC_        |            |                                  |
| Media Texture           | MT_        |            |                                  |
| Render Target           | RT_        |            |                                  |
| Cube Render Target      | RTC_       |            |                                  |
| Texture Light Profile   | TLP        |            |                                  |

<a name="anc-textures-packing"></a>
<a name="1.2.6.1"></a>
#### 1.2.6.1 Texture Packing
Thực hành đóng gói nhiều lớp texture vào một texture là một việc phổ biến. Ví dụ đóng gói `Emissive`, `Roughness`, `Ambient Occlusion` thành 3 kênh Red, Green, and Blue channels của vật liệu. Để xác định hậu tố, đơn giản là nối 3 hậu tố của 3 phần lại với nhau: `_ERO`.

> Kênh Alpha/Opacity tồn tại trong Diffuse/Albedo texture là phổ biến nên có thể ngầm hiểu và bỏ qua hậu tố `A` sau `_D`

Đóng gói 4 kênh data vào một texture (RGBA) là ko nên ngoại trừ trường hợp texture Diffuse/Albedo. Bởi việc này phát sinh nhiều vấn đề hơn là không có.

<a name="anc-misc"></a>
<a name="1.2.7"></a>
### 1.2.7 Khác

| Asset Type                 | Prefix     | Suffix     | Notes                            |
| -------------------------- | ---------- | ---------- | -------------------------------- |
| Animated Vector Field      | VFA_       |            |                                  |
| Camera Anim                | CA_        |            |                                  |
| Color Curve                | Curve_     | _Color     |                                  |
| Curve Table                | Curve_     | _Table     |                                  |
| Data Asset                 | *_         |            | Tiền tố nên dựa trên lớp / class. |
| Data Table                 | DT_        |            |                                  |
| Float Curve                | Curve_     | _Float     |                                  |
| Foliage Type               | FT_        |            |                                  |
| Force Feedback Effect      | FFE_       |            |                                  |
| Landscape Grass Type       | LG_        |            |                                  |
| Landscape Layer            | LL_        |            |                                  |
| Matinee Data               | Matinee_   |            |                                  |
| Media Player               | MP_        |            |                                  |
| File Media Source          | FMS_       |            |                                  |
| Object Library             | OL_        |            |                                  |
| Redirector                 |            |            | These should be fixed up ASAP.   |
| Sprite Sheet               | SS_        |            |                                  |
| Static Vector Field        | VF_        |            |                                  |
| Substance Graph Instance   | SGI_       |            |                                  |
| Substance Instance Factory | SIF_       |            |                                  |
| Touch Interface Setup      | TI_        |            |                                  |
| Vector Curve               | Curve_     | _Vector    |                                  |

<a name="anc-paper2d"></a>
<a name="1.2.8"></a>
### 1.2.8 Paper 2D

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Paper Flipbook          | PFB_       |            |                                  |
| Sprite                  | SPR_       |            |                                  |
| Sprite Atlas Group      | SPRG_      |            |                                  |
| Tile Map                | TM_        |            |                                  |
| Tile Set                | TS_        |            |                                  |

<a name="anc-physics"></a>
<a name="1.2.9"></a>
### 1.2.9 Physics

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Physical Material       | PM_        |            |                                  |
| Physics Asset           | PHYS_      |            |                                  |
| Destructible Mesh       | DM_        |            |                                  |

<a name="anc-sounds"></a>
<a name="1.2.10"></a>
### 1.2.10 Sounds

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Dialogue Voice          | DV_        |            |                                  |
| Dialogue Wave           | DW_        |            |                                  |
| Media Sound Wave        | MSW_       |            |                                  |
| Reverb Effect           | Reverb_    |            |                                  |
| Sound Attenuation       | ATT_       |            |                                  |
| Sound Class             |            |            | Không tiền tố, hậu tố. Nên đặt trong folder tên SoundClasses |
| Sound Concurrency       |            | _SC        | Đặt tên sau tên SoundClass |
| Sound Cue               | A_         | _Cue       |                                  |
| Sound Mix               | Mix_       |            |                                  |
| Sound Wave              | A_         |            |                                  |

<a name="anc-ui"></a>
<a name="1.2.11"></a>
### 1.2.11 Giao diện người dùng - UI

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Font                    | Font_      |            |                                  |
| Slate Brush             | Brush_     |            |                                  |
| Slate Widget Style      | Style_     |            |                                  |
| Widget Blueprint        | WBP_       |            |                                  |

<a name="anc-effects"></a>
<a name="1.2.12"></a>
### 1.2.12 Hiệu ứng

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Particle System         | PS_        |            |                                  |
| Material (Post Process) | PP_        |            |                                  |

**[⬆ Trở lên trên](#Mục lục)**

<a name="2"></a>
<a name="structure"></a>
## 2. Cấu trúc thư mục

Cấu trúc thư mục cần được tôn trọng tương tự như các quy tắc đặt tên. Có nhiều cách để đặt tên thư mục trong dự án UE. Trong quy chuẩn này chúng ta sẽ sử dụng cấu trúc thư mục phục vụ cho việc lọc, tìm kiếm của Content Browser.

> Nếu đã sử dụng các tiền tố và hậu tố trong quy tắc đặt tên ở trên [Quy tắc đặt tên](#1.2), sử dụng thư mục để chứa các asset cùng loại là không cần thiết ví dụ các folder tên `Meshes`, `Textures`, and `Materials` bởi các asset này đã được phân loại bằng tiền tố và hậu tố cùng các bộ lọc của content browser.

<a name="2e1"><a>
### 2e1 Ví dụ về cấu trúc thư mục
<pre>
|-- Content
    |-- <a href="#2.2">GenericShooter</a>
        |-- Art
        |   |-- Industrial
        |   |   |-- Ambient
        |   |   |-- Machinery
        |   |   |-- Pipes
        |   |-- Nature
        |   |   |-- Ambient
        |   |   |-- Foliage
        |   |   |-- Rocks
        |   |   |-- Trees
        |   |-- Office
        |-- Characters
        |   |-- Bob
        |   |-- Common
        |   |   |-- <a href="#2.7">Animations</a>
        |   |   |-- Audio
        |   |-- Jack
        |   |-- Steve
        |   |-- <a href="#2.1.3">Zoe</a>
        |-- <a href="#2.5">Core</a>
        |   |-- Characters
        |   |-- Engine
        |   |-- <a href="#2.1.2">GameModes</a>
        |   |-- Interactables
        |   |-- Pickups
        |   |-- Weapons
        |-- Effects
        |   |-- Electrical
        |   |-- Fire
        |   |-- Weather
        |-- <a href="#2.4">Maps</a>
        |   |-- Campaign1
        |   |-- Campaign2
        |-- <a href="#2.8">MaterialLibrary</a>
        |   |-- Debug
        |   |-- Metal
        |   |-- Paint
        |   |-- Utility
        |   |-- Weathering
        |-- Placeables
        |   |-- Pickups
        |-- Weapons
            |-- Common
            |-- Pistols
            |   |-- DesertEagle
            |   |-- RocketPistol
            |-- Rifles
</pre>

Lý do cho cấu trúc này được liệt kê ở phần phụ sau

<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Tên thư mục

Có những quy tắc chung cho việc đặt tên các thư mục trong cấu trúc nội dung

<a name="2.1.1"></a>
#### 2.1.1 Luôn sử dụng cấu trúc PascalCase [<sup>*</sup>](#terms-cases)

Ví dụ: `DesertEagle`, `RocketPistol`, and `ASeriesOfWords`.

Xem [Chữ cái viết hoa](#terms-cases).

<a name="2.1.2"></a>
#### 2.1.2 Không bao giờ sử dụng ký tự khoảng trắng(space, tab...)

[2.1.1](#2.1.1), Các ký tự khoảng trắng làm cho các công cụ xử lý hàng loạt gặp khó khăn. Lý tưởng nhất nên đặt dự án của bạn ở thư mục gốc ví dụ như `D:\Project` thay vì `C:\Users\My Name\My Documents\Unreal Projects`.

<a name="2.1.3"></a>
#### 2.1.3 Không sử dụng ký tự Unicode và các biểu tượng.

Nếu một trong các nhân vật của bạn tên 'Zoë', thư mục của nó nên tên là `Zoe`. Các ký tự Unicode còn tệ hơn [Khoảng trắng](#2.1.2) cho các công cụ engineering bởi một vài phần của UE không hỗ trợ ký tự Unicode.

Một ví dụ: Nếu dự án của bạn gặp vấn đề [không thể giải thích](https://answers.unrealengine.com/questions/101207/undefined.html)  và tên username trên máy tính của bạn có chứa kí tự Unicode (vd: tên bạn là `Nguyễn`), bất cứ dự án nào năm dưới thư mục `My Documents` sẽ gặp vấn đề này. Thường chỉ cần di chuyển dự án của bạn vào thư mục gốc vd như `D:\Project` sẽ fix được vấn đề khó hiểu này.

Sử dụng các ký tự ngoài `a-z`, `A-Z`, and `0-9` such as `@`, `-`, `_`, `,`, `*`, và `#` cũng có thể dẫn đến các lỗi khó hiểu trên các nền tảng khác nhau, source control và các công cụ engineering yếu.

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Sử dụng thư mục cấp cao nhất cho những assets chỉ định

Tất cả assets của dự án cần tồn tại trong thử mục đặt tên sau dự án. Ví dụ dự án của chúng ta tên là 'Generic Shooter'. _tất cả_ content của nó phải ở trong thư mục `Content/GenericShooter`.

> Thư mục `Developers` không dùng cho các asset mà dự án phụ thuộc vào. Xem [Thư mục Developer](#2.3) để biết thêm chi tiết.

Có nhiều lý do cho phương pháp tiếp cận này.

<a name="2.2.1"></a>
#### 2.2.1 Không asset toàn cục (Global)

Thông thường trong các quy chuẩn viết mã lệnh lập trình, chúng ta không nên làm ô nhiễm không gian biến toàn cục vì vậy cũng theo nguyên lý này nếu asset được cho phép tồn tại ngoài thư mục của dự án nó sẽ trở nên khó để áp đặt các quy chuẩn cấu trúc và vì thế sẽ phát sinh các thói quen xấu trong việc tổ chức sắp xếp assets.

Mỗi asset cần phải có mục đích của nó, nếu không nó sẽ không thuộc về dự án. Nếu asset là một thử nghiệm và không được sử dụng trong dự án nó nên đặt trong thư mục [`Developer`](#2.3).

<a name="2.2.2"></a>
#### 2.2.2 Giảm thiểu xung đột trong migration

Khi làm việc với nhiều dự án cùng lúc, việc sử dụng asset từ dự án này sang dự án khác là việc phổ biến. Khi việc này xảy ra, cách dễ dàng nhất là sử dụng chức năng Migrate của Content Browser để copy cả những phần phụ thuộc.

Những phụ thuộc này là nguồn gốc của rắc rối. Nếu assets của 2 dự án đều không có thư mục cấp cao nhất (top level folder) và nếu như cả 2 đều có tên asset giống nhau hoặc asset đã migrate từ trước, đợt migration mới này sẽ ghi đè và xoá sạch những thay đổi ở asset đã có 

Đây cũng là lý do chính mà đội ngũ Marketplace của Epic áp đặt chính sách và tiêu chuẩn này cho các asset được xuất bản lên Marketplace

Sau khi migration, hợp nhất an toàn các assets bằng công cụ 'Replace References' trong Content Browser. Sự xuất hiện của một thư mục không thuộc top level dự án xác định rõ ràng đây là thư mục cần được hợp nhất vào dự án. Một khi các asset(tài nguyên game) đã được hợp nhất hoàn toàn với dự án sẽ không còn một folder nào khác ngoài folder project. Phương pháp này _100%_ đảm bảo bất cứ sự hợp nhất nào cũng diễn ra một cách an toàn.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Ví dụ vật liệu chủ

Ví dụ, nếu bạn tạo một vật liệu chủ ở dự án A này và muốn sử dụng nó trong dự án B, vì thế bạn migrate vật liệu chủ từ A sang B. Nếu vật liệu này không ở trong thư mục dự án bậc 1, ví dụ `Content/MaterialLibrary/M_Master`. Nếu dự án B không có vật liệu `M_Master`, mọi việc sẽ diễn ra suôn sẻ.

Theo tiến trình phát triển của dự án, vật liệu chủ của từng dự án sẽ có sự biến đổi phù hợp với mục đích của dự án.

Vấn để nảy sinh khi, một artist của dự án A tạo ra một nhóm các static mesh hữu ích và một vài artist khác muốn sử dụng nó trong dự án của họ. Nếu artist của dự án A sử dụng bản sao vật liệu trong `Content/MaterialLibrary/M_Master` vì họ được hướng dẫn như thế, khi tiến hành migrate sẽ rất có khả năng xung đột với lần migrate trước của `Content/MaterialLibrary/M_Master`.

Sự cố này khó đoán trước được bởi người migrate những static mesh này không cùng một người đã quen thuộc với master material của cả 2 dự án. Họ thậm chí còn không biết những static mesh này phụ thuộc vào Material Instances cái phụ thuộc vào Master Material. Công cụ migrate sẽ di chuyển cả chuỗi phụ thuộc cùng với asset cần migrate vì vậy nó sẽ mang theo cả `Content/MaterialLibrary/M_Master` khi nó sao chép asset từ dự án nguồn sang dự án mục tiêu và vô hình chung ghi đè lên asset đã có của dự án mục tiêu

Nếu ở thời điểm này Vật liệu chủ cho cả 2 dự án không tương thích với nhau, chúng ta đã mạo hiểm khả năng làm hỏng cả chuỗi thư viện vật liệu của dự án và các asset khác phụ thuộc vào nó bởi đơn giản là chúng ta đã không đặt các asset vào thư mục bậc 1 của dự án.

<a name="2.2.3"></a>
#### 2.2.3 Thêm tài nguyên thư viện, Templates và Marketplace Samples được đảm bảo an toàn.

Mở rọng cho [2.2.2](#2.2.2), nếu một thành viên quyết định thêm tài nguyên mẫu, template hoặc tài nguyên mua từ Marketplace, tiến trình này được đảm bảo an toàn nếu dự án của chúng ta nằm trong cấu trúc thư mục bậc 1, những tài nguyên mới này sẽ không xung đột với tài nguyên trong dự án của chúng ta.

Chúng ta không thể hoàn toàn tin tưởng các tài nguyên từ Marketplace luôn luôn tuân thủ quy tắc [Thư mục bậc 1](#2.2). Có những tài nguyên mà phần lớn nội dung của nó ở thư mục bậc 1 và cũng có vài tài nguyên chỉnh sửa nội dung của Epic sample cùng với nhiều files làm ô nhiễm không gian thư mục toàn cục (global) `Content`

Khi tuân thử theo [2.2](#2.2), sự xung đột tồi tệ nhất mà bạn có thể gặp phải là 2 tài nguyên từ marketplace có cùng nội dung từ Epic sample. Nếu tất cả tài nguyên của chúng ta nằm trong một thư mục cụ thể, bao gồm cả sample content mà chúng ta đã di rời vào thư mục bậc 1 của dự án, dự án của chúng ta sẽ không bao giờ đổ vỡ.

<a name="2.2.4"></a>
#### 2.2.4 DLC, Bản vá, Dự án con sẽ dễ dàng duy trì, bảo trì hơn.

Nếu dự án của bạn có kế hoạch xuất bản DLC hoặc có nhiều dự án con liên quan tới có khả năng sẽ migrate ra ngoài, hoặc không cooked khi build, tài nguyên của những dự án như thế phải có riêng thư mục bậc 1. Việc này cho phép cook DLC từ dự án chủ dễ dàng hơn. Những dự án con cũng có thể migrate ra vào dễ dàng. Nếu chúng ta cần thay đổi vật liệu cảu một tài nguyên hoặc thêm một số tính năng riêng biệt ghi đè trong một bản vá, chúng ta có thể dễ dàng đặt những thay đổi đó trong thư mục vá và làm việc một cách an tâm là nó sẽ không gây hỏng dự án gốc.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Sử dụng thư mục `Developers` cho những thử nghiệm cục bộ

Trong quá trình phát triển dự án, các thành viên sẽ có thử nghiệm rất nhiều vì vậy cần một không gian an toàn để họ có thể thực hiện các thử nghiệm của mình mà không gây ảnh hưởng tới dự án. Đây là một công việc liên tục nên chúng ta sẽ muốn cho nó vào server quản lý phiên bản. Không phải tất cả các team đều có nhu cầu sử dụng thư mục Developer, nhưng một khi đã sử dụng thì thường gặp các vấn đề khi subbmit tài nguyên lên source control.

Một sự cố phổ biến khác là các thành viên chẳng may sử dụng những tài nguyên chưa hoàn thiện, các sự cố nảy sinh tiếp theo do các tài nguyên này bị xoá đi. 

Ví dụ: Một artist đang cải tiến các modul các static meshes và vẫn đang liên tục cải tiến về mặt kích thước, đường dóng cho thật đúng. Các artist thiết kế bối cảnh nếu thấy những tài nguyên này trong thư mục chính của dự án và sử dụng nó để thiết kế bối cảnh mà không biết rằng nó có thể bị bỏ đi sẽ dẫn đến lãng phí công sức thời gian của nhiều người.

The Content Browser mặc định sẽ ẩn thư mục Developer tránh những sự cố kiểu này xảy ra.

Khi những tài nguyên này sẵn sàng được sử dụng, artist di dời những tài nguyên này vào thư mục cụ thể trong dự án và sử dụng công cụ *fix up redirectors* 'thăng cấp' tài nguyên từ cấp độ thử nghiệm lên cấp độ production.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 Tất cả Map[<sup>*</sup>](#terms-level-map) Files phải nằm trong folder Maps.

File map có những quy tắc đặc biệt riêng và tuỳ thuộc mỗi dự án, đặc biệt là sử dụng sub-levels hoặc level streaming. Dù tuân thủ theo hệ thống nào thì tất cả map đều thuộc về `/Content/Project/Maps`.

Để có thể truyền đạt tới bất cứ ai để mở một map mà không cần phải giải thích tiết kiệm rất nhiều thời gian. Sử dụng thư mục con trong `Maps` cũng phổ biến ví dụ `Maps/Campaign1/` or `Maps/Arenas`, nhưng quan trọng nhất là chúng đều nằm trong `/Content/Project/Maps`.

Đơn giản hoá quá trình cook. Tập hợp các level cho quá trình build. Nếu các Level ở cùng một thư mục hạn chế khả năng cook bị sót.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Sử dụng thư mục `Core` cho các Blueprint và Assets cốt lõi

Sử dụng thư mục `/Content/Project/Core` cho những tài nguyên cốt yếu. Ví dụ: base `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState` ...

Những thành viên không thuộc team dev gần như không có lý do để vào khu vực thư mục `Core` này. Tuân thủ quy tắc cấu trúc, designer nên thêm những thay đổi tính năng của họ ở trong lớp con. Những người thiết kế môi trường nên sử dụng Blueprints có sẵn trong những folder chỉ định thay vì chỉnh sửa base class.

Ví dụ: Nếu dự án có những vật phẩm nhặt được (Pickups) cần được đặt trong level, cần có một lớp vật phẩm gốc (base class) trong thư mục `Core/Pickups` định nghĩa những thuộc tính, hành vi cơ bản của lớp Pickup. Những vật phẩm cụ thể ví dụ như Health hoặc Ammo nên ở trong thư mục `/Content/Project/Placeables/Pickups/`. Người thiết kế game có thể định nghĩa và tinh chỉnh những vật phẩm trong thư mục này nhưng họ không nên động chạm đến `Core/Pickups` vì có khả năng họ sẽ làm hỏng những vật phẩm khác trên toàn dự án.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Không tạo thư mục `Assets` hoặc kiểu `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Tạo thư mục `Assets` là dư thừa.
Mọi Assets đều là Assets.

<a name="2.6.2"></a>
#### 2.6.2 Thư mục tên `Meshes`, `Textures`, hoặc `Materials` cũng là dư thừa.

Tất cả tên của asset phải được đặt tên với chủ ý phân loại kiểu asset trong tư tưởng. Sử dụng tên thư mục để phân loại là không cần thiết bởi Content Browser đã có công cụ phân loại mạnh mẽ và ưu thế hơn.

Để xem các static mesh trong `Environment/Rocks/`? Đơn giản là bật filter Static Mesh. Nếu tất cả asset đều được đặt tên đúng, chúng cũng sẽ được sắp xếp theo thứ tự alphabe cho dù có các thành phần tiền tố. Điều này cũng triệt tiêu khả năng phải `Control-Click` để chọn nhiều thư mục trong `Content Browser`.

> Không những thế full path name của một asset cũng trở nên gọn gàng hơn. Tiền tố `S_` chỉ có 2 chữ cái trong khi `Meshes/` là 7 chữ cái.

Loại trừ các trường hợp bất khả kháng như có ai đó đặt nhầm static mesh hoặc texture vào thư mục `Materials`.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Những Asset đồ sộ cần có cấu trúc thư mục riêng của nó.

Đây có thể coi là một "ngoại lệ giả" pseudo-exception đối với [2.6](#2.6).

Có những kiểu asset có rất nhiều file liên quan, phụ thuộc mà trong đó mỗi asset lại có một mục đích đặc biệt riêng. Hai kiểu phổ biến là Animation và Audio. Nếu chúng ta thấy rằng có hơn 15 asset kiểu đó thuộc về nhau, chúng nên ở cùng nhau.

Ví dụ: Đoạn animation được nhiều nhân vật dùng nên nằm trong thư mục `Characters/Common/Animations` và có thể có những thư mục con như `Locomotion` hoặc `Cinematic`.

> Những điều này không áp dụng cho nhưng asset kiểu texture hoặc material. Rất phổ biến cho việc thư mục `Rocks` có một lượng lớn texture nếu có một lượng lớn rocks, tuy nhiên những texture này chỉ liên quan tới một vài hòn đá cụ thể và cần phải được đặt tên phù hợp. Mặc dù những texture này là một phần của [Material Library](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

Những vật liệu chủ, vật liệu lớp (layered materials), hoặc bất cứ dạng nào không thuộc về một asset cụ thể. Những asset này phải được đặt trong `Content/Project/MaterialLibrary`.

Bằng cách này toàn bộ các vật liệu 'toàn cục' phải ở cùng một chỗ và dễ dàng truy cập.

> Điều này cũng tuân thủ quy tắc 'chỉ sử dụng vật liệu nhân bản'. If all artists and assets should be using material instances, then the only regular material assets that should exist are within this folder. You can easily verify this by searching for base materials in any folder that isn't the `MaterialLibrary`.

Thư mục `MaterialLibrary` không nhất thiết chỉ chứa mỗi vật liệu. Những texture phụ trợ, hàm material, và những thứ tự nhiên thuộc về thư mục này như texture noise chung chung nên ở thư mục `MaterialLibrary/Utility`.

Bất cứ thử nghiệm hoặc tìm lỗi về vật liệu nào nên nằm trong `MaterialLibrary/Debug`. Điều này làm cho những vật liệu lỗi dễ đàng được loại bỏ trước khi đóng gói và xuất bản.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 Không để thư mục nào bị trống

Tránh làm phân mảnh thư mục content browser bởi các thư mục trống.

Nếu có thư mục trống không xoá được:
1. Đảm bảo là bạn sử dụng source control. (trong tương lai)
1. Dùng lệnh Fix Up Redirectors.
1. Mở thư mục trên ổ đĩa và xoá những assets bên trong.
1. Đóng editor.
1. Đồng bộ hoá với source control (i.e. Perforce, gitCentral)
1. Mở Unreal Editor. Xác nhận mọi thứ vẫn hoạt động. Nếu không thì đảo ngược quá trình, xem xét mọi thứ sai ở đâu và thử lại.
1. Đảm bảo thư mục đã bị loại.
1. Xác nhận thay đổi đến source control.

**[⬆ Trở lên trên](#Mục lục)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

Phân này tập chung vào các lớp Blueprint. Bất cứ khi nào có thể, nên sử dụng theo tiêu chuẩn của[Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Remember: Blueprinting badly bears blunders, beware! (Phrase by [KorkuVeren](http://github.com/KorkuVeren))

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compiling - Biên dịch

Tất cả blueprint cần được biên dịch sạch lỗi và cảnh báo. Chúng ta nên sửa những cảnh bảo và lỗi của blueprint ngay lập tức vì chúng có thể nhanh chóng chồng chéo lên nhau và tạo nên những lỗi không ngờ được.

Không submit blueprints lỗi lên source control. Nếu phải lưu chúng lên source control hãy shelve. 
Shelve : Lưu thay đổi mà không đăng ký vào Source Control.

Blueprint lỗi có thể tạo ra nhiều kiểu lỗi như mất liên kết tham chiếu, hành vi không dự đoán trước, lỗi cooking, thường xuyên phải biên dịch lại không cần thiết. Một blueprint bị lỗi có đủ sức mạnh để phá hỏng hoàn toàn game.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables - Biến

Hai từ `variable` và `property` có thể dùng thay thế cho nhau.

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Naming - Đặt tên

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Nouns - Danh từ

Tất cả các biến non-boolean cần có tên rõ ràng, không mơ hồ, gợi nhớ.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

Biến non-boolean cần phải ở dạng [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Ví dụ:

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Biến Boolean tiền tố `b`

Tất cả biến boolean phải đặt tên ở dạng PascalCase với tiền tố `b`.

Ví dụ: Sử dụng `bDead` và `bEvil`, **không dùng** `Dead` and `Evil`.

Trình sửa đổi Blueprint tự biết cách không thêm tiền tố `b` để hiển thị một cách thân thiện.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Tên Boolean

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1  Thông tin chung và thông tin độc lập

Tất cả biến Booleans cần đặt tên gợi mở thông tin nhất một cách có thể khi có khả năng. Không thêm những từ dạng câu hỏi như `Is`. Trường hợp này để dành cho tên function

Ví dụ: Dùng `bDead` và `bHostile` **không dùng** `bIsDead` và `bIsHostile`.

Không sử dụng những động từ như `bRunning`. Động từ thường dẫn đến những trạng thái phức hợp.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Trạng thái phức hợp - Complex States

Không dùng booleans để diễn tả các trạng thái phức hợp/hoặc phụ thuộc. Làm cho việc thêm và bớt các trạng thái trở nên phức tạp, khó đọc. Dùng biến enumeration thay cho việc đó.

Ví dụ: Khi định nghĩa một vũ khí, **không dùng** `bReloading` và `bEquipping` nếu một vũ khí không thể cùng nạp và trang bị. Thay vì thế hãy định nghĩa biến enumeration tên `EWeaponState` và sử dụng biến với cái tên này `WeaponState`. Điều này làm cho việc thêm các trạng thái khác của vũ khí dễ dàng hơn nhiều.

Ví dụ: **Không dùng** `bRunning` nếu như chúng ta cũng cần các trạng thái khác như `bWalking` hoặc `bSprinting`. Những biến này cần được định nghĩa thuộc dạng enumeration với các trạng thái được đặt tên rõ ràng.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Lưu ý đến ngữ cảnh

Tất cả các tên biến phải không bị thừa thãi đối với ngữ cảnh bởi tất cả các biến tham chiếu trong Blueprint sẽ luôn phải có ngữ cảnh.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Ví dụ:

Xem xét biến Bluerprint trong `BP_PlayerCharacter`.

**Bad**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

Tất cả cá biến trên đều có tên thừa thãi. Ngầm định rằng tất cả biến của `BP_PlayerCharacter` là thuộc về chính nó bởi `BP_PlayerCharacter` là thứ định nghĩa những biến này.

**Good**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 Không thêm kiểu dữ liệu cơ bản.

Booleans, integers, floats, and enumerations là kiểu dữ liệu cơ bản.
Strings và vectors trong Blueprint được coi là dữ liệu cơ bản. Tuy nhiên về mặt kỹ thuật thì chúng không phải là dữ liệu cơ bản.

> Trong khi vector cấu thành từ 3 số thực giống như rotators.

> _không_ được coi dữ liệu dạng Text là kiểu dữ liệu cơ bản, Text là một đối tượng có nhiều hàm ẩn trong nó. Kiểu dữ liệu cơ bản của chuỗi ký tự là `String`, không phải `Text`.

Kiểu dữ liệu cơ bản không được có tên kiểu dữ liệu của nó trong tên biến.

Ví dụ: Sử dụng `Score`, `Kills`, và `Description` **không dùng** `ScoreFloat`, `FloatKills`, `DescriptionString`.

Điều này chỉ ngoại lệ khi biến đó thể hiện 'số lượng của' cái gì đó để đếm _và_ khi không có nó thì sẽ khó đọc.

Ví dụ: Một Actor tạo hàng rào cần số X các cột. Lưu trữ số X trong `NumPosts` hoặc `PostCount` thay vì `Posts` bởi `Posts` có thể bị nhầm lẫn với mảng các biến kiểu `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Nên thêm tên cho các kiểu dữ liệu phức hợp.

Những kiểu dữ liệu phức hợp là biến cấu tạo từ tập hợp các biến cơ bản. Struct, Classes, Interface, và các biến có các hành vi ẩn như `Text` và `Name` là những biến phức hợp.

>Trong khi một Mảng các biến cơ bản là danh sách các biến, tuy nhiên Mảng không làm thay đổi tính chất 'atomicness' của kiểu biến.

Những biến này nên thêm tên kiểu biến tuy nhiên vẫn phải xem xét các tới yếu tố ngữ cảnh.

Nếu một class sở hữu một bản sao của một biến phức hợp, ví dụ: `BP_PlayerCharacter` sở hữu một `BP_Hat`, nó nên được lưu với tên kiểu biến mà không nên có sự thay đổi thêm nào.

Ví dụ: Sử dụng `Hat`, `Flag`, và `Ability` **không dùng** `MyHat`, `MyFlag`, và `PlayerAbility`.

Nếu một lớp không sở hữu giá trị mà một biến phức hợp thể hiện, chúng ta nên dùng danh từ cùng với kiểu biến.

Ví dụ: Nếu `BP_Turret` có khả năng target một `BP_PlayerCharacter`, Nó nên lưu target của nó là `TargetPlayer` khi ở trong ngữ cảnh của `BP_Turret`, nó nên rõ ràng rằng đây là một tham chiếu đến một kiểu biến phức hợp khác mà nó không sở hữu.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Mảng

Mảng nên tuân theo các quy tắc đặt tên như trên, nhưng nên được đặt tên là danh từ số nhiều

Ví dụ: Sử dụng `Targets`, `Hats`, và `EnemyPlayers`, **không dùng** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Biến có khả năng chỉnh sửa

Tất cả các biến có thể chỉnh sửa giá trị cho việc thiết lập hành vi của blueprint nên được đánh dấu là `Editable`.

Ngược lại, tất cả các biến không an toàn khi thay đổi giá trị thì không nên bày ra và _không_ đánh dấu là `Editable`, trừ trường hợp cho các lý do kỹ thuật, các biến được đánh dâu là `Expose On Spawn`.

Không đánh dấu `Editable` tuỳ tiện.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Tooltips

Tất cả biến `Editable`, `Expose On Spawn`, Phải có mô tả trong phần `Tooltip` về hiệu quả, ảnh hưởng của biến này tới hành vi của blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Slider và khoảng giá trị

Tất cả biến `Editable` nên sử dụng slider và khoảng giá trị nếu có những giá trị có thể gây _lỗi_ hoặc vô nghĩa

Ví dụ: Một blueprint tạo cọc hàng rào có biến tên là `PostsCount` thì những giá trị < 0 sẽ trở nên vô nghĩa. Sử dụng khoảng giá trị để thiết lập 0 là giá trị nhỏ nhất.

Nếu một biến tuỳ chỉnh được sử dụng trong phần Construction Script, cần phải có Slider Range để không vô tình gán những giá trị quá lớn hoặc quá nhỏ có thể làm crash chương trình.
Khoảng giá trị chỉ cần thiết nếu được xác định. Trong khi Slider Range ngăn ngừa nguy cơ gán những giá trị quá lớn hoặc quá nhỏ. Khoảng giá không xác định cho phép gán những giá trị nằm ngoài Slider Range được coi là "nguy hiểm" tuy nhiên vẫn là giá trị đúng.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categories - Danh mục

Nếu một lớp chỉ có một số lượng nhỏ các biến thì danh mục không cần thiết.

Nếu một lớp có từ (5-10) tuỳ biến, tất cả `Editable` biến nên có danh mục không thuộc default. Một cái tên phổ biến có thể là `Config`.

Những biến không tuỳ chỉnh được nên ở trong danh mục được chú giải rõ ràng về cách thức sử dụng chúng.

> Chúng ta có thể định dạng danh mục con bằng cách sử dụng ký tự `|`, Ví dụ: `Config | Animations`.

Ví dụ:  Một lớp vũ khí có thể được tổ chức như sau:

    |-- Config
    |    |-- Animations
    |    |-- Effects
    |    |-- Audio
    |    |-- Recoil
    |    |-- Timings
    |-- Animations
    |-- State
    |-- Visuals

<a name="3.2.4"></a>
<a name="bp-vars-access"></a>
#### 3.2.4 phạm vi truy cập biến

Trong C++, các biến đều có khái niệm về phạm vi truy cập. Public có nghĩa là các đoạn code ở ngoài class cũng có thể truy cập. Protected có nghĩa là chỉ trong class và class con có thể truy cập. Private nghĩa là chỉ trong class mới được truy cập, class con cũng không thể truy cập.

Blueprints hiện tại không có khái niệm biến Protected.

Coi như `Editable` biến là biến public. Biến non-editable là biến protected.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Biến Private

Chỉ dùng nếu biết rằng biến này chỉ nên được dùng trong class hiện tại

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Hiển thị nâng cao

Nếu một biến có thể tuỳ biến nhưng thường không nên động vào thì nên đánh dấu là `Advanced Display` để ẩn biến này đi trừ khi advanced display được tick sổ ra.

Để tìm `Advanced Display` nó nằm trong detail panel.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Các biến tạm thời (Transient)

Các biến tạm thời là các biến không cần lưu các giá trị, không cần nạp, cần có giá trị khởi tạo là zero hoặc null. Đây là một cách thức hữu ích cho việc tham chiếu tới các đối tượng và actors mà giá trị của nó là không biết được cho tới khi hoạt động (run-time). Điều này ngăn ngừa trình biên tập (editor) lưu trữ một phiên bản tham chiếu tới nó, tăng tốc sự lưu trữ và nạp của blueprin class.

Bởi vì vậy, tất cả các biến tạm thời nên luôn được khởi tạo là zero hoặc null. Không thì sẽ dẫn đến khó khăn trong quá trình debug lỗi.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Biến thiết lập (Config Variables)

Đừng dùng flag `Config Variable`. Điều này sẽ làm cho designers khó điều chỉnh hành vi của blueprint. Các biến thiết lập chỉ nên sử dụng trong C++ vì lí do hiếm khi thay đổi những thông số thiết lập ấy (ví dụ: PI = 3.141592654...) Nghĩ tới chúng như những biến `Advanced Advanced Display`.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Hàm, Sự kiện, Phát sự kiện

Phần này bàn về cách chúng ta nên tạo ra các hàm, sự kiện, và phát sự kiện. Mọi thứ áp dụng vào hàm cần được áp dụng vào event, trừ khi có ghi chú.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Đặt tên hàm

Đặt tên hàm, sự kiện, phát sự kiện là một việc tối quan trọng. Chỉ cần dựa vào cái tên có thể đưa ra một vài dữ kiện về hàm đấy. Ví dụ:

* Đây có phải là một hàm thuần khiết? / Is it a pure function? 
* Đây có phải là một hàm lấy thông tin trạng thái? / Is it fetching state information?
* Đây là một hàm xử lý? / Is it a handler?
* Đây là một RPC? / Is it an RPC?
* Mục đích của nó là gì? / What is its purpose?

Những câu hỏi trên hoặc nhiều hơn đều có thể được trả lời nếu tên hàm được đặt tên một cách xác đáng. 

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 Tất cả các hàm nên là động từ.

Tất cả các hàm và sự kiện đều thực hiện các dạng hành động, có thể là lấy thông tin, tính toán dữ liệu, kích nổ cái gì đó. Vì vậy tất cả các hàm phải nên lấy động từ làm khởi điểm và đặt trong thì hiện tại khi có thể. Chúng cũng nên có một vài ngữ cảnh về việc chúng làm gì.

Hàm `OnRep`, xử lý sự kiện, phát sự kiện, là những ngoại lệ trong trường hợp này.

Những ví dụ tốt:

* `Fire` - 1 ví dụ tốt nếu nó trong lớp Character / Weapon, vì nó có ngữ cảnh. Không tốt nếu trong lớp Barrel / Grass / hay lớp ngẫu nhiên nào khác.
* `Jump` - Tốt nếu nằm trong lớp Character không thì phải cần ngữ cảnh.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" là động từ tobe.](http://writingexplained.org/is-is-a-verb)

Ví dụ tệ:

* `Dead` - là chết? Sẽ chết?
* `Rock`
* `ProcessData` - Mơ hồ, những từ này không có ý nghĩa cụ thể về công việc nó đang làm.
* `PlayerState` - Danh từ mơ hồ.
* `Color` - Động từ thiếu ngữ cảnh hay là danh từ mơ hồ.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Hàm Property RepNotify luôn đặt là `OnRep_Variable`. Đây là quy tắc bắt buộc bởi trình biên tập Blueprint. Nếu chúng ta viết hàm `OnRep` trong C++, nó cũng nên tuân theo quy tắc này khi exposing nó cho Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Hàm thông tin trả về giá trị Boolean nên là câu hỏi ?

Khi tạo một hàm không làm thay đổi trạng thái hoặc thay đổi đối tượng mà chỉ đơn thuần là lấy thông tin, trạng thái, hoặc tính toán giá trị đúng/sai, nó nên hỏi câu hỏi. Điều này cũng nên tuân theo quy tắc động từ [the verb rule](#bp-funcs-naming-verbs).

Đây là một điều cực kỳ quan trọng bởi nếu không phải là câu hỏi thì sẽ được ngầm hiểu là hàm này thực hiện một số hành động, tác vụ và giá trị trả về là kết quả thành công của chuỗi hành động đó.

Một số ví dụ tốt:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" là một động từ.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" là thời quá khứ của "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Sử dụng "was" khi có ý là 'previous frame' hoặc 'previous state'.
* `CanReload` - ["Can" là động từ.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Ví dụ tệ:

* `Fire` - Đang cháy? Sẽ cháy? Bắn?
* `OnFire` - Có thể bị nhẫm lẫn với phát sự kiện cho việc bắn.
* `Dead` - Chết chưa? sẽ chết?
* `Visibility` - Có nhìn thấy? Thiết lập nhìn thấy? Một điều kiện?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Xử lý sự kiện và Phát sự kiện nên bắt đầu với `On`

Bất kỳ hàm nào xử lý sự kiện hoặc phát sự kiện phải bắt đầu với `On` và tuân thủ theo quy tắc động từ [the verb rule](#bp-funcs-naming-verbs). Động từ có thể chuyển xuống cuối và dùng thời quá khứ nếu dễ hiểu hơn.

Từ `On` trong [Cụm từ](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) được miễn theo quy tắc động từ.

`Handle` Không được phép sử dụng. Trong 'Unreal' sử dụng `On` thay vì `Handle`, trong khi các frameworks khác sẽ dùng `Handle` thay vì `On`.

Ví dụ tốt:

* `OnDeath` - Cụm từ phổ biến trong game dev
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Ví dụ tệ:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Các thủ tục gọi từ xa cần đi kèm với tiền tố là mục tiêu / Remote Procedure Calls (RPC) Should Be Prefixed With Target
RPC: Các hàm được gọi local nhưng thực thi trên máy khác (riêng biệt với máy gọi hàm)

Bất cứ khi nào một hàm RPC được tạo, nó phải được đi kèm với tiền tố `Server`, `Client`, hoặc `Multicast`. Không có ngoại lệ.

Sau các tiền tố, tuân theo các luật khác trong việc đặt tên.

Ví dụ:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Ví dụ tệ:

* `FireWeapon` - Không cho biết nó là một hàm RPC.
* `ServerClientBroadcast` - Nhầm lẫn.
* `AllNotifyDeath` - Sử dụng `Multicast`, Đừng bao giờ dùng `All`.
* `ClientWeapon` - Không động từ, không hiểu làm gì, mơ hồ.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 Tất cả các hàm phải có node return

Tất cả các hàm phải có node return, không ngoại lệ.

Return nodes thể hiện rõ ràng nó là điểm cuối cùng của chuỗi lệnh. Trong Blueprint có thể sử dụng các node như `Sequence`, `ForLoopWithBreak`, dây nối ngược nodes, minh bạch về dòng thực thi của các chuỗi lệnh là điều quan trọng cho sự dễ hiểu, bảo trì, gỡ lỗi.

Trình biên dịch Blueprint có khả năng đi theo dòng thực thi lệnh và cảnh bảo nếu có một nhánh lệnh có những thứ chưa xử lý hoặc lỗi nếu chúng ta sử dụng node return.

Trong trường hợp một lập trình viên thêm một pin vào node Sequence hoặc thêm logic vào sau vòng lặp, nhưng vòng lặp lại trả về sớm hơn. Kết quả này có thể gây ra một lỗi trong dòng thực thi sau này. Cảnh bảo từ trình biên dịch Blueprint có thể cho thấy vấn đề ngay tức khắc.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 Không hàm nào nên có hơn 50 Nodes

Đơn giản, nếu có hàm nào nhiều node hơn như vậy thì nên phá vỡ ra thành những hàm nhỏ hơn để đảm bảo tính dễ đọc và dễ bảo trì.

Những node sau không tính vào con số 50 vì nó không làm tăng sự phức tạp của hàm:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 Tất cả hàm công khai phải có mô tả

Quy tắc này cũng áp dụng nhiều đối với marketplace blueprints để cho người khác dễ sử dụng và hiểu về blueprint API của chúng ta. Không nên lãng phí thời gian của đồng nghiệp cho việc họ phải mất thời gian dò xem công dụng và cách dùng của Blueprint này là gì cũng như lãng phí thời gian phải giải thích cho người khác mỗi khi có người khác sử dụng

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5  Tất cả các hàm Plugin phải được cho vào danh mục của tên Plugin

Nếu dự án của chúng ta bao gồm một plugin định nghĩa hàm `static` `BlueprintCallable`
, chúng phải được cho vào danh mục tên plugin hoặc danh mục con của plugin.

Ví dụ, `Zed Camera Interface` hoặc `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

Phần này nói về những quy tắc áp dụng tới tất cả Blueprint graphps.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 Không rối như mớ bòng bong.

Những đường nối phải rõ ràng điểm bắt đầu và kết thúc. Đừng nên mất thời gian để người khác phải sắp xếp lại các node, đường dây mới có thể hiểu chuyện gì đang xảy ra, tốn thời gian của nhau.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Căn dóng theo đường dây không phải node

Chúng ta không thể luôn tuỳ chỉnh kích thước của node, pin nhưng luôn có thể căn chỉnh vị trí của nó qua đó điều chỉnh vị trí của dây nối. Đường dây thẳng rõ ràng dòng chảy của mạch sự kiện. Sử dụng lệnh làm thẳng (chọn BP nodes). Hotkey: Q

Trường hợp tốt: Những node được căn dóng để tạo đường thẳng cho dòng thực thi.
![Aligned By Wires](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Trường hợp xấu: Dòng thực thi không thẳng vì căn dóng theo node.
![Bad](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Trường hợp chấp nhận được: Có một vài node cứng đầu không chịu hợp tác dù chúng ta cố gắng căn dóng như thế nào đi nữa. Trong trường hợp này hạn chế tối đa đường lắt léo bằng cách đưa các node lại gần nhau.
![Acceptable](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 Các đường thực thi (màu trắng) là ưu tiên cao nhất.

Nếu chúng ta phải quyết định giữa việc làm thẳng đường thực thi hay làm thẳng đường dữ liệu thì luôn chọn làm thẳng đường thực thi.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs phải được comment có ý thức, hiệu quả

Khối các node phải được bao bởi comment mô tả hành vi của nó. Trong khi mỗi hàm phải được đặt tên sao cho mỗi node đều dễ hiểu, nhóm các node phục vụ một mục đích thì phải có block comment cho mục đích đó. Nếu tên hàm đã đủ cho mục đích đó thì không cần comment

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs phải xử lý ngoại lệ Casting hợp lý

Nếu một hàm hoặc sự kiện được coi như luôn cast thành công thì phải có cảnh báo khi cast fail để có thể biết sự cố xuất hiện ở đâu

Điều này không có nghĩa là tất cả các cast node luôn phải có xử lý fail. Trong nhiều trường hợp ví dụ như collisions thì cast fail không cần phải xử lý ngoại lệ mà chỉ cần cho dòng thực thi ngừng lại.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs không nên có node treo, node không sử dụng.

Tất cả các nodes trong blueprin phải có mục đích của nó. Không nên để những node trống, treo, không có trong dòng thực thi.

**[⬆ Trở lên trên](#Mục lục)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Lưới tĩnh / Static Meshes

Phần này sẽ nói về Static Meshes và những thứ liên quan.

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

Linter: Là một phần mềm tự động kiểm tra dự án xem có tuân thủ các quy tắc được đặt ra trong guideline không. Hiện tại chúng ta chưa có

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 Tất cả meshes phải có UVs

Đơn giản. Tất cả meshes, ko kể nó được sẽ được sử dụng như thế nào, đều không được thiếu UVs.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 Tất cả Meshes phải có UVs cho Lightmaps (non overlap)

Phục vụ cho việc bake lighting

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs phải được setup chính xác.

Mỗi mesh đều phải có LODs cho các khoảng cách nhìn khác nhau. Điều này sẽ tiếp tục được xem xét với phương pháp làm việc mới khi có sự xuất hiện của Nanite.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Các module không có socket phải snap vào lưới đơn vị (grid) chuẩn xác

Để các module ghép vào nhau như những mảnh lego và tạo nên những thứ lớn hơn.
Dựa trên tiêu chuẩn của Epic Marketplace Module phải snap khi grid đặt là 10 units hoặc lớn hơn.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 Tất cả mesh phải có Collision

Dù cho có thể không dùng đến Collision cho tính toán va chạm nhưng nhiều tác vụ tính toán khác engine có thể dùng đến Collision có thể kể đến như bounds calculations, occlusion, and lighting.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 Tất cả các lưới phải được Scaled 1:1 đúng kích thước vật lý mong muốn.

Nếu có sử dụng đến scale thì việc scale đấy phải là việc bắt buộc có chủ đích chứ không phải là scale sửa lỗi kích thước ko đúng.

**[⬆ Trở lên trên](#Mục lục)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 Không bao giờ dùng dấu cách, khoảng trắng.

Như đã nhắc đến trong [00.1 Định danh bị cấm](#00), tất cả khoảng trắng và dấu cách là bị cấm. Điều này đặc biệt phải tuân thủ khi làm việc với Niagara khi mà một số script hoặc HLSL trong Niagara sẽ rất khó hay gần như không tham chiếu được tới các định danh có dấu cách, khoảng trắng.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


**[⬆ Trở lên trên](#Mục lục)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[Xem chú giải](#terms-level-map) "levels" và "maps".

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 Không lỗi hoặc cảnh báo

Sử dụng map check để kiểm tra và xử lý tất cả các lỗi, cảnh báo, tránh để các lỗi chồng chất lên nhau

Ghi chú: Linter thậm chí còn khắt khe hơn trong việc kiểm tra lỗi và bắt cả những lỗi khi load level mà trình biên tập sẽ bỏ qua. (Hiện tại chưa có Linter cho UE5)

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Ánh sáng phải Built

Trong quá trình phát triển có thể không built nhưng nếu thửu nghiệm test/internal/shipping thì phải build ánh sáng.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 Không Z Fighting (trùng mặt)

Level không được có hiện tượng trùng mặt ở những nơi mà player có thể tiếp cận và có tầm nhìn
[z-fighting](https://en.wikipedia.org/wiki/Z-fighting)

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Quy tắc của Marketplace

Nếu dự án của chúng ta được bán trên Marketplace, nó cần tuân thủ quy tắc của Marketplace.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
#### 6.4.1 Level Tổng quan

Nếu dự án có chứa các asset cần minh hoạ hoặc demo cần phải có map tên là "Overview".

Bản đồ này nếu để minh hoạ asset thì phải setup tuân thủ [Quy chuẩn của Epic](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

Ví dụ, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
#### 6.4.2 Demo Level

Nếu dự án của chúng ta có những asset cần demo thì phải có map tên là "Demo". Map này phải có dạng tài liệu giới thiệu hướng dẫn sử dụng trọng điểm trong đó. Xem ví dụ của Epic

Nếu dự án là một cơ chế chơi game hoặc dạng hệ thống chứ không phải là tập hợp các art asset có thể đặt tên ví dụ như: 

Ví dụ, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Trở lên trên](#Mục lục)**


<a name="7"></a>
<a name="textures"></a>
## 7. Textures

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Độ phân giải phải là luỹ thừa của 2

Có thể không phải là hình vuông nhưng các cạnh phải là luỹ thừa của 2.

Ví dụ: `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Mật độ texture phải đồng nhất.

Tất cả texture phải có kích thước phù hợp với mục đích sử dụng. Mỗi một dự án lại có một mật độ phù hợp khác nhau, nhưng các texture trong cùng dự án phải có mật độ đồng nhất.

Ví dụ, nếu một dự án yêu cầu mật độ là 8 pixel/unit thì cho hình hộp 100x100 unit cần texture độ phân giải là 1024x1024, vì đó là con số gần nhất mà vẫn thoả mãn điều kiện luỹ thừa của 2 và mật độ yêu cầu của dự án

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures không lớn hơn 8192

Lãng phí tài nguyên hệ thống, trừ khi có lý do rõ ràng bắt buộc phải dùng.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures phải nhóm đúng

Mỗi texture phải có thuộc tính Texture Group cho LOD và phải được thiết lập đúng dựa trên cách sử dụng. Ví dụ, tất cả UI texture phải thuộc nhóm UI Texture Group.

**[⬆ Trở lên trên](#Mục lục)**


## Những người đóng góp chính

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Bản quyền (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Trở lên trên](#Mục lục)**


## Sửa đổi bổ xung

Khuyến khích sử dụng và chỉnh sửa cho phù hợp team của mình. Dưới đây, chúng ta có thể liệt kê một số sửa đổi đối với quy chuẩn. Điều này cho phép chúng ta cập nhật định kỳ quy chuẩn mà không bị xung đột với quy chuẩn gốc.

# };
