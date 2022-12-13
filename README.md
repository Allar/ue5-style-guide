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
    - [3.2.4 Độ sâu truy cập của biến](#bp-vars-access)
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
Thực hành đóng gói nhiều lớp texture vào một texture là một việc phổ biến. Một ví dụ là đóng gói `Emissive`, `Roughness`, `Ambient Occlusion` thành 3 kênh Red, Green, and Blue channels của vật liệu. Để xác định hậu tố, đơn giản là nối 3 hậu tố của 3 phần lại với nhau: `_ERO`.

> Bao gồm kênh Alpha/Opacity vào trong kênh alpha của Diffuse/Albedo texture là phổ biến nên có thể ngầm hiểu và bỏ qua hậu tố `A` sau `_D`

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

**[⬆ Back to Top](#table-of-contents)**

<a name="2"></a>
<a name="structure"></a>
## 2. Cấu trúc thư mục

Cấu trúc thư mục cần được tôn trọng tương tự như các quy tắc đặt tên. Có nhiều cách để đặt tên thư mục trong dự án UE. Trong quy chuẩn này chúng ta sẽ sử dụng cấu trúc thư mục phục vụ cho việc lọc, tìm kiếm của Content Browser.

> Nếu đã sử dụng các tiền tố và hậu tố trong quy tắc đặt tên ở trên [Quy tắc đặt tên](#1.2), sử dụng thư mục để chứa các asset cùng loại là dư thừa ví dụ các folder tên `Meshes`, `Textures`, and `Materials` bởi các asset này đã được phân loại bằng tiền tố và hậu tố cùng các bộ lọc của content browser.

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

Đây cũng là lý do chính mà đội ngũ Marketplace của Epic áp đặt chính sách và tiêu chuẩn này cho các asset được xuất bản lên chợ.


After a migration, safe merging of assets can be done using the 'Replace References' tool in the content browser with the added clarity of assets not belonging to a project's top level folder are clearly pending a merge. Once assets are merged and fully migrated, there shouldn't be another top level folder in your Content tree. This method is _100%_ guaranteed to make any migrations that occur completely safe.

<a name="2.2.2e1"></a>
##### 2.2.2e1 Master Material Example

For example, say you created a master material in one project that you would like to use in another project so you migrated that asset over. If this asset is not in a top level folder, it may have a name like `Content/MaterialLibrary/M_Master`. If the target project doesn't have a master material already, this should work without issue.

As work on one or both projects progress, their respective master materials may change to be tailored for their specific projects due to the course of normal development.

The issue comes when, for example, an artist for one project created a nice generic modular set of static meshes and someone wants to include that set of static meshes in the second project. If the artist who created the assets used material instances based on `Content/MaterialLibrary/M_Master` as they're instructed to, when a migration is performed there is a great chance of conflict for the previously migrated `Content/MaterialLibrary/M_Master` asset.

This issue can be hard to predict and hard to account for. The person migrating the static meshes may not be the same person who is familiar with the development of both project's master material, and they may not be even aware that the static meshes in question rely on material instances which then rely on the master material. The Migrate tool requires the entire chain of dependencies to work however, and so it will be forced to grab `Content/MaterialLibrary/M_Master` when it copies these assets to the other project and it will overwrite the existing asset.

It is at this point where if the master materials for both projects are incompatible in _any way_, you risk breaking possibly the entire material library for a project as well as any other dependencies that may have already been migrated, simply because assets were not stored in a top level folder. The simple migration of static meshes now becomes a very ugly task.

<a name="2.2.3"></a>
#### 2.2.3 Samples, Templates, and Marketplace Content Are Risk-Free

An extension to [2.2.2](#2.2.2), if a team member decides to add sample content, template files, or assets they bought from the marketplace, it is guaranteed, as long your project's top-level folder is uniquely named,that these new assets will not interfere with your project.

You can not trust marketplace content to fully conform to the [top level folder rule](#2.2). There exists many assets that have the majority of their content in a top level folder but also have possibly modified Epic sample content as well as level files polluting the global `Content` folder.

When adhering to [2.2](#2.2), the worst marketplace conflict you can have is if two marketplace assets both have the same Epic sample content. If all your assets are in a project specific folder, including sample content you may have moved into your folder, your project will never break.

<a name="2.2.4"></a>
#### 2.2.4 DLC, Sub-Projects, and Patches Are Easily Maintained

If your project plans to release DLC or has multiple sub-projects associated with it that may either be migrated out or simply not cooked in a build, assets relating to these projects should have their own separate top level content folder. This make cooking DLC separate from main project content far easier. Sub-projects can also be migrated in and out with minimal effort. If you need to change a material of an asset or add some very specific asset override behavior in a patch, you can easily put these changes in a patch folder and work safely without the chance of breaking the core project.

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Use Developers Folder For Local Testing

During a project's development, it is very common for team members to have a sort of 'sandbox' where they can experiment freely without risking the core project. Because this work may be ongoing, these team members may wish to put their assets on a project's source control server. Not all teams require use of Developer folders, but ones that do use them often run into a common problem with assets submitted to source control.

It is very easy for a team member to accidentally use assets that are not ready for use, which will cause issues once those assets are removed. For example, an artist may be iterating on a modular set of static meshes and still working on getting their sizing and grid snapping correct. If a world builder sees these assets in the main project folder, they might use them all over a level not knowing they could be subject to incredible change and/or removal. This causes massive amounts of re-working for everyone on the team to resolve.

If these modular assets were placed in a Developer folder, the world builder should never have had a reason to use them and the whole issue would never happen. The Content Browser has specific View Options that will hide Developer folders (they are hidden by default) making it impossible to accidentally use Developer assets under normal use.

Once the assets are ready for use, an artist simply has to move the assets into the project specific folder and fix up redirectors. This is essentially 'promoting' the assets from experimental to production.

<a name="2.4"></a>
<a name="structure-maps"></a>
### 2.4 All Map[<sup>*</sup>](#terms-level-map) Files Belong In A Folder Called Maps

Map files are incredibly special and it is common for every project to have its own map naming system, especially if they work with sub-levels or streaming levels. No matter what system of map organization is in place for the specific project, all levels should belong in `/Content/Project/Maps`.

Being able to tell someone to open a specific map without having to explain where it is is a great time saver and general 'quality of life' improvement. It is common for levels to be within sub-folders of `Maps`, such as `Maps/Campaign1/` or `Maps/Arenas`, but the most important thing here is that they all exist within `/Content/Project/Maps`.

This also simplifies the job of cooking for engineers. Wrangling levels for a build process can be extremely frustrating if they have to dig through arbitrary folders for them. If a team's maps are all in one place, it is much harder to accidentally not cook a map in a build. It also simplifies lighting build scripts as well as QA processes.

<a name="2.5"></a>
<a name="structure-core"></a>
### 2.5 Use A `Core` Folder For Critical Blueprints And Other Assets

Use `/Content/Project/Core` folder for assets that are absolutely fundamental to a project's workings. For example, base `GameMode`, `Character`, `PlayerController`, `GameState`, `PlayerState`, and related Blueprints should live here.

This creates a very clear "don't touch these" message for other team members. Non-engineers should have very little reason to enter the `Core` folder. Following good code structure style, designers should be making their gameplay tweaks in child classes that expose functionality. World builders should be using prefab Blueprints in designated folders instead of potentially abusing base classes.

For example, if your project requires pickups that can be placed in a level, there should exist a base Pickup class in `Core/Pickups` that defines base behavior for a pickup. Specific pickups such as a Health or Ammo should exist in a folder such as `/Content/Project/Placeables/Pickups/`. Game designers can define and tweak pickups in this folder however they please, but they should not touch `Core/Pickups` as they may unintentionally break pickups project-wide.

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 Do Not Create Folders Called `Assets` or `AssetTypes`

<a name="2.6.1"></a>
#### 2.6.1 Creating a folder named `Assets` is redundant

All assets are assets.

<a name="2.6.2"></a>
#### 2.6.2 Creating a folder named `Meshes`, `Textures`, or `Materials` is redundant

All asset names are named with their asset type in mind. These folders offer only redundant information and the use of these folders can easily be replaced with the robust and easy to use filtering system the Content Browser provides.

Want to view only static mesh in `Environment/Rocks/`? Simply turn on the Static Mesh filter. If all assets are named correctly, they will also be sorted in alphabetical order regardless of prefixes. Want to view both static meshes and skeletal meshes? Simply turn on both filters. This eliminates the need to potentially have to `Control-Click` select two folders in the Content Browser's tree view.

> This also extends the full path name of an asset for very little benefit. The `S_` prefix for a static mesh is only two characters, whereas `Meshes/` is seven characters.

Not doing this also prevents the inevitability of someone putting a static mesh or a texture in a `Materials` folder.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Very Large Asset Sets Get Their Own Folder Layout

This can be seen as a pseudo-exception to [2.6](#2.6).

There are certain asset types that have a huge volume of related files where each asset has a unique purpose. The two most common are Animation and Audio assets. If you find yourself having 15+ of these assets that belong together, they should be together.

For example, animations that are shared across multiple characters should lay in `Characters/Common/Animations` and may have sub-folders such as `Locomotion` or `Cinematic`.

> This does not apply to assets like textures and materials. It is common for a `Rocks` folder to have a large amount of textures if there are a large amount of rocks, however these textures are generally only related to a few specific rocks and should be named appropriately. Even if these textures are part of a [Material Library](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

If your project makes use of master materials, layered materials, or any form of reusable materials or textures that do not belong to any subset of assets, these assets should be located in `Content/Project/MaterialLibrary`.

This way all 'global' materials have a place to live and are easily located.

> This also makes it incredibly easy to enforce a 'use material instances only' policy within a project. If all artists and assets should be using material instances, then the only regular material assets that should exist are within this folder. You can easily verify this by searching for base materials in any folder that isn't the `MaterialLibrary`.

The `MaterialLibrary` doesn't have to consist of purely materials. Shared utility textures, material functions, and other things of this nature should be stored here as well within folders that designate their intended purpose. For example, generic noise textures should be located in `MaterialLibrary/Utility`.

Any testing or debug materials should be within `MaterialLibrary/Debug`. This allows debug materials to be easily stripped from a project before shipping and makes it incredibly apparent if production assets are using them if reference errors are shown.

<a name="2.9"></a>
<a name="structure-no-empty-folders"></a>
### 2.9 No Empty Folders

There simply shouldn't be any empty folders. They clutter the content browser.

If you find that the content browser has an empty folder you can't delete, you should perform the following:
1. Be sure you're using source control.
1. Immediately run Fix Up Redirectors on your project.
1. Navigate to the folder on-disk and delete the assets inside.
1. Close the editor.
1. Make sure your source control state is in sync (i.e. if using Perforce, run a Reconcile Offline Work on your content directory)
1. Open the editor. Confirm everything still works as expected. If it doesn't, revert, figure out what went wrong, and try again.
1. Ensure the folder is now gone.
1. Submit changes to source control.

**[⬆ Back to Top](#table-of-contents)**


<a name="3"></a>
<a name="bp"></a>
## 3. Blueprints

This section will focus on Blueprint classes and their internals. When possible, style rules conform to [Epic's Coding Standard](https://docs.unrealengine.com/latest/INT/Programming/Development/CodingStandard).

Remember: Blueprinting badly bears blunders, beware! (Phrase by [KorkuVeren](http://github.com/KorkuVeren))

<a name="3.1"></a>
<a name="bp-compiling"></a>
### 3.1 Compiling

All blueprints should compile with zero warnings and zero errors. You should fix blueprint warnings and errors immediately as they can quickly cascade into very scary unexpected behavior.

Do *not* submit broken blueprints to source control. If you must store them on source control, shelve them instead.

Broken blueprints can cause problems that manifest in other ways, such as broken references, unexpected behavior, cooking failures, and frequent unneeded recompilation. A broken blueprint has the power to break your entire game.

<a name="3.2"></a>
<a name="bp-vars"></a>
### 3.2 Variables

The words `variable` and `property` may be used interchangeably.

<a name="3.2.1"></a>
<a name="bp-var-naming"></a>
#### 3.2.1 Naming

<a name="3.2.1.1"></a>
<a name="bp-var-naming-nouns"></a>
##### 3.2.1.1 Nouns

All non-boolean variable names must be clear, unambiguous, and descriptive nouns.

<a name="3.2.1.2"></a>
<a name="bp-var-naming-case"></a>
##### 3.2.1.2 PascalCase

All non-boolean variables should be in the form of [PascalCase](#terms-cases).

<a name="3.2.1.2e"></a>
###### 3.2.1.2e Examples

* `Score`
* `Kills`
* `TargetPlayer`
* `Range`
* `CrosshairColor`
* `AbilityID`

<a name="3.2.1.3"></a>
<a name="bp-var-bool-prefix"></a>
##### 3.2.1.3 Boolean `b` Prefix

All booleans should be named in PascalCase but prefixed with a lowercase `b`.

Example: Use `bDead` and `bEvil`, **not** `Dead` and `Evil`.

UE4 Blueprint editors know not to include the `b` in user-friendly displays of the variable.

<a name="3.2.1.4"></a>
<a name="bp-var-bool-names"></a>
##### 3.2.1.4 Boolean Names

<a name="3.2.1.4.1"></a>
###### 3.2.1.4.1 General And Independent State Information

All booleans should be named as descriptive adjectives when possible if representing general information. Do not include words that phrase the variable as a question, such as `Is`. This is reserved for functions.

Example: Use `bDead` and `bHostile` **not** `bIsDead` and `bIsHostile`.

Try to not use verbs such as `bRunning`. Verbs tend to lead to complex states.

<a name="3.2.1.4.2"></a>
###### 3.2.1.4.2 Complex States

Do not to use booleans to represent complex and/or dependent states. This makes state adding and removing complex and no longer easily readable. Use an enumeration instead.

Example: When defining a weapon, do **not** use `bReloading` and `bEquipping` if a weapon can't be both reloading and equipping. Define an enumeration named `EWeaponState` and use a variable with this type named `WeaponState` instead. This makes it far easier to add new states to weapons.

Example: Do **not** use `bRunning` if you also need `bWalking` or `bSprinting`. This should be defined as an enumeration with clearly defined state names.

<a name="3.2.1.5"></a>
<a name="bp-vars-naming-context"></a>
##### 3.2.1.5 Considered Context

All variable names must not be redundant with their context as all variable references in Blueprint will always have context.

<a name="3.2.1.5e"></a>
###### 3.2.1.5e Examples

Consider a Blueprint called `BP_PlayerCharacter`.

**Bad**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

All of these variables are named redundantly. It is implied that the variable is representative of the `BP_PlayerCharacter` it belongs to because it is `BP_PlayerCharacter` that is defining these variables.

**Good**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

<a name="3.2.1.6"></a>
<a name="bp-vars-naming-atomic"></a>
##### 3.2.1.6 Do _Not_ Include Atomic Type Names

Atomic or primitive variables are variables that represent data in their simplest form, such as booleans, integers, floats, and enumerations.

Strings and vectors are considered atomic in terms of style when working with Blueprints, however they are technically not atomic.

> While vectors consist of three floats, vectors are often able to be manipulated as a whole, same with rotators.

> Do _not_ consider Text variables as atomic, they are secretly hiding localization functionality. The atomic type of a string of characters is `String`, not `Text`.

Atomic variables should not have their type name in their name.

Example: Use `Score`, `Kills`, and `Description` **not** `ScoreFloat`, `FloatKills`, `DescriptionString`.

The only exception to this rule is when a variable represents 'a number of' something to be counted _and_ when using a name without a variable type is not easy to read.

Example: A fence generator needs to generate X number of posts. Store X in `NumPosts` or `PostsCount` instead of `Posts` as `Posts` may potentially read as an Array of a variable type named `Post`.

<a name="3.2.1.7"></a>
<a name="bp-vars-naming-complex"></a>
##### 3.2.1.7 Do Include Non-Atomic Type Names

Non-atomic or complex variables are variables that represent data as a collection of atomic variables. Structs, Classes, Interfaces, and primitives with hidden behavior such as `Text` and `Name` all qualify under this rule.

> While an Array of an atomic variable type is a list of variables, Arrays do not change the 'atomicness' of a variable type.

These variables should include their type name while still considering their context.

If a class owns an instance of a complex variable, i.e. if a `BP_PlayerCharacter` owns a `BP_Hat`, it should be stored as the variable type as without any name modifications.

Example: Use `Hat`, `Flag`, and `Ability` **not** `MyHat`, `MyFlag`, and `PlayerAbility`.

If a class does not own the value a complex variable represents, you should use a noun along with the variable type.

Example: If a `BP_Turret` has the ability to target a `BP_PlayerCharacter`, it should store its target as `TargetPlayer` as when in the context of `BP_Turret` it should be clear that it is a reference to another complex variable type that it does not own.


<a name="3.2.1.8"></a>
<a name="bp-vars-naming-arrays"></a>
##### 3.2.1.8 Arrays

Arrays follow the same naming rules as above, but should be named as a plural noun.

Example: Use `Targets`, `Hats`, and `EnemyPlayers`, **not** `TargetList`, `HatArray`, `EnemyPlayerArray`.


<a name="3.2.2"></a>
<a name="bp-vars-editable"></a>
#### 3.2.2 Editable Variables

All variables that are safe to change the value of in order to configure behavior of a blueprint should be marked as `Editable`.

Conversely, all variables that are not safe to change or should not be exposed to designers should _not_ be marked as editable, unless for engineering reasons the variable must be marked as `Expose On Spawn`.

Do not arbitrarily mark variables as `Editable`.

<a name="3.2.2.1"></a>
<a name="bp-vars-editable-tooltips"></a>
##### 3.2.2.1 Tooltips

All `Editable` variables, including those marked editable just so they can be marked as `Expose On Spawn`, should have a description in their `Tooltip` fields that explains how changing this value affects the behavior of the blueprint.

<a name="3.2.2.2"></a>
<a name="bp-vars-editable-ranges"></a>
##### 3.2.2.2 Slider And Value Ranges

All `Editable` variables should make use of slider and value ranges if there is ever a value that a variable should _not_ be set to.

Example: A blueprint that generates fence posts might have an editable variable named `PostsCount` and a value of -1 would not make any sense. Use the range fields to mark 0 as a minimum.

If an editable variable is used in a Construction Script, it should have a reasonable Slider Range defined so that someone can not accidentally assign it a large value that could crash the editor.

A Value Range only needs to be defined if the bounds of a value are known. While a Slider Range prevents accidental large number inputs, an undefined Value Range allows a user to specify a value outside the Slider Range that may be considered 'dangerous' but still valid.

<a name="3.2.3"></a>
<a name="bp-vars-categories"></a>
#### 3.2.3 Categories

If a class has only a small number of variables, categories are not required.

If a class has a moderate amount of variables (5-10), all `Editable` variables should have a non-default category assigned. A common category is `Config`.

If a class has a large amount of variables, all `Editable` variables should be categorized into sub-categories using the category `Config` as the base category. Non-editable variables should be categorized into descriptive categories describing their usage.

> You can define sub-categories by using the pipe character `|`, i.e. `Config | Animations`.

Example: A weapon class set of variables might be organized as:

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
#### 3.2.4 Variable Access Level

In C++, variables have a concept of access level. Public means any code outside the class can access the variable. Protected means only the class and any child classes can access this variable internally. Private means only this class and no child classes can access this variable.

Blueprints do not have a defined concept of protected access currently.

Treat `Editable` variables as public variables. Treat non-editable variables as protected variables.

<a name="3.2.4.1"></a>
<a name="bp-vars-access-private"></a>
##### 3.2.4.1 Private Variables

Unless it is known that a variable should only be accessed within the class it is defined and never a child class, do not mark variables as private. Until variables are able to be marked `protected`, reserve private for when you absolutely know you want to restrict child class usage.

<a name="3.2.5"></a>
<a name="bp-vars-advanced"></a>
#### 3.2.5 Advanced Display

If a variable should be editable but often untouched, mark it as `Advanced Display`. This makes the variable hidden unless the advanced display arrow is clicked.

To find the `Advanced Display` option, it is listed as an advanced displayed variable in the variable details list.

<a name="3.2.6"></a>
<a name="bp-vars-transient"></a>
#### 3.2.6 Transient Variables

Transient variables are variables that do not need to have their value saved and loaded and have an initial value of zero or null. This is useful for references to other objects and actors who's value isn't known until run-time. This prevents the editor from ever saving a reference to it, and speeds up saving and loading of the blueprint class.

Because of this, all transient variables should always be initialized as zero or null. To do otherwise would result in hard to debug errors.

<a name="3.2.7"></a>
<a name="bp-vars-config"></a>
#### 3.2.8 Config Variables

Do not use the `Config Variable` flag. This makes it harder for designers to control blueprint behavior. Config variables should only be used in C++ for rarely changed variables. Think of them as `Advanced Advanced Display` variables.

<a name="3.3"></a>
<a name="bp-functions"></a>
### 3.3 Functions, Events, and Event Dispatchers

This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

<a name="3.3.1"></a>
<a name="bp-funcs-naming"></a>
#### 3.3.1 Function Naming

The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* Is it an RPC?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="3.3.1.1"></a>
<a name="bp-funcs-naming-verbs"></a>
#### 3.3.1.1 All Functions Should Be Verbs

All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should all start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

`OnRep` functions, event handlers, and event dispatchers are an exception to this rule.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

<a name="3.3.1.2"></a>
<a name="bp-funcs-naming-onrep"></a>
#### 3.3.1.2 Property RepNotify Functions Always `OnRep_Variable`

All functions for replicated with notification variables should have the form `OnRep_Variable`. This is forced by the Blueprint editor. If you are writing a C++ `OnRep` function however, it should also follow this convention when exposing it to Blueprints.

<a name="3.3.1.3"></a>
<a name="bp-funcs-naming-bool"></a>
#### 3.3.1.3 Info Functions Returning Bool Should Ask Questions

When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#bp-funcs-naming-verbs).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

<a name="3.3.1.4"></a>
<a name="bp-funcs-naming-eventhandlers"></a>
#### 3.3.1.4 Event Handlers and Dispatchers Should Start With `On`

Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#bp-funcs-naming-verbs). The verb may move to the end however if past-tense reads better.

[Collocations](http://dictionary.cambridge.org/us/grammar/british-grammar/about-words-clauses-and-sentences/collocation) of the word `On` are exempt from following the verb rule.

`Handle` is not allowed. It is 'Unreal' to use `On` instead of `Handle`, while other frameworks may prefer to use `Handle` instead of `On`.

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`
* `HandleMessage`
* `HandleDeath`

<a name="3.3.1.5"></a>
<a name="bp-funcs-naming-rpcs"></a>
#### 3.3.1.5 Remote Procedure Calls Should Be Prefixed With Target

Any time an RPC is created, it should be prefixed with either `Server`, `Client`, or `Multicast`. No exceptions.

After the prefix, follow all other rules regarding function naming.

Good examples:

* `ServerFireWeapon`
* `ClientNotifyDeath`
* `MulticastSpawnTracerEffect`

Bad examples:

* `FireWeapon` - Does not indicate its an RPC of some kind.
* `ServerClientBroadcast` - Confusing.
* `AllNotifyDeath` - Use `Multicast`, never `All`.
* `ClientWeapon` - No verb, ambiguous.


<a name="3.3.2"></a>
<a name="bp-funcs-return"></a>
#### 3.3.2 All Functions Must Have Return Nodes

All functions must have return nodes, no exceptions.

Return nodes explicitly note that a function has finished its execution. In a world where blueprints can be filled with `Sequence`, `ForLoopWithBreak`, and backwards reroute nodes, explicit execution flow is important for readability, maintenance, and easier debugging.

The Blueprint compiler is able to follow the flow of execution and will warn you if there is a branch of your code with an unhandled return or bad flow if you use return nodes.

In situations like where a programmer may add a pin to a Sequence node or add logic after a for loop completes but the loop iteration might return early, this can often result in an accidental error in code flow. The warnings the Blueprint compiler will alert everyone of these issues immediately.

<a name="3.3.3"></a>
<a name="bp-graphs-funcs-node-limit"></a>
#### 3.3.3 No Function Should Have More Than 50 Nodes

Simply, no function should have more than 50 nodes. Any function this big should be broken down into smaller functions for readability and ease of maintenance.

The following nodes are not counted as they are deemed to not increase function complexity:

* Comment
* Route
* Cast
* Getting a Variable
* Breaking a Struct
* Function Entry
* Self

<a name="3.3.4"></a>
<a name="bp-graphs-funcs-description"></a>
#### 3.3.4 All Public Functions Should Have A Description

This rule applies more to public facing or marketplace blueprints, so that others can more easily navigate and consume your blueprint API.

Simply, any function that has an access specificer of Public should have its description filled out.

<a name="3.3.5"></a>
<a name="bp-graphs-funcs-plugin-category"></a>
#### 3.3.5 All Custom Static Plugin `BlueprintCallable` Functions Must Be Categorized By Plugin Name

If your project includes a plugin that defines `static` `BlueprintCallable` functions, they should have their category set to the plugin's name or a subset category of the plugin's name.

For example, `Zed Camera Interface` or `Zed Camera Interface | Image Capturing`.

<a name="3.4"></a>
<a name="bp-graphs"></a>
### 3.4 Blueprint Graphs

This section covers things that apply to all Blueprint graphs.

<a name="3.4.1"></a>
<a name="bp-graphs-spaghetti"></a>
#### 3.4.1 No Spaghetti

Wires should have clear beginnings and ends. You should never have to mentally untangle wires to make sense of a graph. Many of the following sections are dedicated to reducing spaghetti.

<a name="3.4.2"></a>
<a name="bp-graphs-align-wires"></a>
#### 3.4.2 Align Wires Not Nodes

Always align wires, not nodes. You can't always control the size and pin location on a node, but you can always control the location of a node and thus control the wires. Straight wires provide clear linear flow. Wiggly wires wear wits wickedly. You can straighten wires by using the Straighten Connections command with BP nodes selected. Hotkey: Q

Good example: The tops of the nodes are staggered to keep a perfectly straight white exec line.
![Aligned By Wires](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-good.png?raw=true "Aligned By Wires")

Bad Example: The tops of the nodes are aligned creating a wiggly white exec line.
![Bad](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-bad.png?raw=true "Wiggly")

Acceptable Example: Certain nodes might not cooperate no matter how you use the alignment tools. In this situation, try to minimize the wiggle by bringing the node in closer.
![Acceptable](https://github.com/Allar/ue5-style-guide/blob/main/images/bp-graphs-align-wires-acceptable.png?raw=true "Acceptable")

<a name="3.4.3"></a>
<a name="bp-graphs-exec-first-class"></a>
#### 3.4.3 White Exec Lines Are Top Priority

If you ever have to decide between straightening a linear white exec line or straightening data lines of some kind, always straighten the white exec line.

<a name="3.4.4"></a>
<a name="bp-graphs-block-comments"></a>
#### 3.4.4 Graphs Should Be Reasonably Commented

Blocks of nodes should be wrapped in comments that describe their higher-level behavior. While every function should be well named so that each individual node is easily readable and understandable, groups of nodes contributing to a purpose should have their purpose described in a comment block. If a function does not have many blocks of nodes and its clear that the nodes are serving a direct purpose in the function's goal, then they do not need to be commented as the function name and  description should suffice.

<a name="3.4.5"></a>
<a name="bp-graphs-cast-error-handling"></a>
#### 3.4.5 Graphs Should Handle Casting Errors Where Appropriate

If a function or event assumes that a cast always succeeds, it should appropriately report a failure in logic if the cast fails. This lets others know why something that is 'supposed to work' doesn't. A function should also attempt a graceful recover after a failed cast if it's known that the reference being casted could ever fail to be casted.

This does not mean every cast node should have its failure handled. In many cases, especially events regarding things like collisions, it is expected that execution flow terminates on a failed cast quietly.

<a name="3.4.6"></a>
<a name="bp-graphs-dangling-nodes"></a>
#### 3.4.6 Graphs Should Not Have Any Dangling / Loose / Dead Nodes

All nodes in all blueprint graphs must have a purpose. You should not leave dangling blueprint nodes around that have no purpose or are not executed.

**[⬆ Back to Top](#table-of-contents)**


<a name="4"></a>
<a name="Static Meshes"></a>
<a name="s"></a>
## 4. Static Meshes

This section will focus on Static Mesh assets and their internals.

<a name="4.1"></a>
<a name="s-uvs"></a>
### 4.1 Static Mesh UVs

If Linter is reporting bad UVs and you can't seem to track it down, open the resulting `.log` file in your project's `Saved/Logs` folder for exact details as to why it's failing. I am hoping to include these messages in the Lint report in the future.

<a name="4.1.1"></a>
<a name="s-uvs-no-missing"></a>
#### 4.1.1 All Meshes Must Have UVs

Pretty simple. All meshes, regardless how they are to be used, should not be missing UVs.

<a name="4.1.2"></a>
<a name="s-uvs-no-overlapping"></a>
#### 4.1.2 All Meshes Must Not Have Overlapping UVs for Lightmaps

Pretty simple. All meshes, regardless how they are to be used, should have valid non-overlapping UVs.

<a name="4.2"></a>
<a name="s-lods"></a>
### 4.2 LODs Should Be Set Up Correctly

This is a subjective check on a per-project basis, but as a general rule any mesh that can be seen at varying distances should have proper LODs.

<a name="4.3"></a>
<a name="s-modular-snapping"></a>
### 4.3 Modular Socketless Assets Should Snap To The Grid Cleanly

This is a subjective check on a per-asset basis, however any modular socketless assets should snap together cleanly based on the project's grid settings.

It is up to the project whether to snap based on a power of 2 grid or on a base 10 grid. However if you are authoring modular socketless assets for the marketplace, Epic's requirement is that they snap cleanly when the grid is set to 10 units or bigger.

<a name="4.4"></a>
<a name="s-collision"></a>
### 4.4 All Meshes Must Have Collision

Regardless of whether an asset is going to be used for collision in a level, all meshes should have proper collision defined. This helps the engine with things such as bounds calculations, occlusion, and lighting. Collision should also be well-formed to the asset.

<a name="4.5"></a>
<a name="s-scaled"></a>
### 4.5 All Meshes Should Be Scaled Correctly

This is a subjective check on a per-project basis, however all assets should be scaled correctly to their project. Level designers or blueprint authors should not have to tweak the scale of meshes to get them to confirm in the editor. Scaling meshes in the engine should be treated as a scale override, not a scale correction.

**[⬆ Back to Top](#table-of-contents)**


<a name="5"></a>
<a name="Niagara"></a>
<a name="ng"></a>
## 5. Niagara

This section will focus on Niagara assets and their internals.

<a name="5.1"></a>
<a name="ng-rules"></a>
### 5.1 No Spaces, Ever

As mentioned in [00.1 Forbidden Identifiers](#00), spaces and all white space characters are forbidden in identifiers. This is especially true for Niagara systems as it makes working with things significantly harder if not impossible when working with HLSL or other means of scripting within Niagara and trying to reference an identifier.

(Original Contribution by [@dunenkoff](https://github.com/Allar/ue5-style-guide/issues/58))


**[⬆ Back to Top](#table-of-contents)**


<a name="6"></a>
<a name="Levels"></a>
<a name="levels"></a>
## 6. Levels / Maps

[See Terminology Note](#terms-level-map) regarding "levels" vs "maps".

This section will focus on Level assets and their internals.

<a name="6.1"></a>
<a name="levels-no-errors-or-warnings"></a>
### 6.1 No Errors Or Warnings

All levels should load with zero errors or warnings. If a level loads with any errors or warnings, they should be fixed immediately to prevent cascading issues.

You can run a map check on an open level in the editor by using the console command "map check".

Please note: Linter is even more strict on this than the editor is currently, and will catch load errors that the editor will resolve on its own.

<a name="6.2"></a>
<a name="levels-lighting-should-be-built"></a>
### 6.2 Lighting Should Be Built

It is normal during development for levels to occasionally not have lighting built. When doing a test/internal/shipping build or any build that is to be distributed however, lighting should always be built.

<a name="6.3"></a>
<a name="levels-no-visible-z-fighting"></a>
### 6.3 No Player Visible Z Fighting

Levels should not have any [z-fighting](https://en.wikipedia.org/wiki/Z-fighting) in all areas visible to the player.

<a name="6.4"></a>
<a name="levels-mp-rules"></a>
### 6.4 Marketplace Specific Rules

If a project is to be sold on the UE4 Marketplace, it must follow these rules.

<a name="6.4.1"></a>
<a name="levels-mp-rules-overview"></a>
#### 6.4.1 Overview Level

If your project contains assets that should be visualized or demoed, you must have a map within your project that contains the name "Overview".

This overview map, if it is visualizing assets, should be set up according to [Epic's guidelines](http://help.epicgames.com/customer/en/portal/articles/2592186-marketplace-submission-guidelines-preparing-your-assets#Required%20Levels%20and%20Maps).

For example, `InteractionComponent_Overview`.

<a name="6.4.2"></a>
<a name="levels-mp-rules-demo"></a>
#### 6.4.2 Demo Level

If your project contains assets that should be demoed or come with some sort of tutorial, you must have a map within your project that contains the name "Demo". This level should also contain documentation within it in some form that illustrates how to use your project. See Epic's Content Examples project for good examples on how to do this.

If your project is a gameplay mechanic or other form of system as opposed to an art pack, this can be the same as your "Overview" map.

For example, `InteractionComponent_Overview_Demo`, `ExplosionKit_Demo`.

**[⬆ Back to Top](#table-of-contents)**


<a name="7"></a>
<a name="textures"></a>
## 7. Textures

This section will focus on Texture assets and their internals.

<a name="7.1"></a>
<a name="textures-dimensions"></a>
### 7.1 Dimensions Are Powers of 2

All textures, except for UI textures, must have its dimensions in multiples of powers of 2. Textures do not have to be square.

For example, `128x512`, `1024x1024`, `2048x1024`, `1024x2048`, `1x512`.

<a name="7.2"></a>
<a name="textures-density"></a>
### 7.2 Texture Density Should Be Uniform

All textures should be of a size appropriate for their standard use case. Appropriate texture density varies from project to project, but all textures within that project should have a consistent density.

For example, if a project's texture density is 8 pixel per 1 unit, a texture that is meant to be applied to a 100x100 unit cube should be 1024x1024, as that is the closest power of 2 that matches the project's texture density.

<a name="7.3"></a>
<a name="textures-max-size"></a>
### 7.3 Textures Should Be No Bigger than 8192

No texture should have a dimension that exceeds 8192 in size, unless you have a very explicit reason to do so. Often, using a texture this big is simply just a waste of resources.

<a name="7.4"></a>
<a name="textures-group"></a>
### 7.4 Textures Should Be Grouped Correctly

Every texture has a Texture Group property used for LODing, and this should be set correctly based on its use. For example, all UI textures should belong in the UI texture group.

**[⬆ Back to Top](#table-of-contents)**


## Major Contributors

* [Michael Allar](http://allarsblog.com): [GitHub](https://github.com/Allar), [Twitter](https://twitter.com/michaelallar)
* [CosmoMyzrailGorynych](https://github.com/CosmoMyzrailGorynych)
* [billymcguffin](https://github.com/billymcguffin)
* [akenatsu](https://github.com/akenatsu)

## License

Copyright (c) 2016 Gamemakin LLC

See [LICENSE](/LICENSE)

**[⬆ Back to Top](#table-of-contents)**


## Amendments

We encourage you to fork this guide and change the rules to fit your team's style guide. Below, you may list some amendments to the style guide. This allows you to periodically update your style guide without having to deal with merge conflicts.

# };
