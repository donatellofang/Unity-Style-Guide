# 前言

旧目录规则

```PowerShell
\---Art
+---Enviroments
|   +---Map_Canyon
|   |   +---Dec
|   |   |   +---Materials
|   |   |   +---Models
|   |   |   +---Prefabs
|   |   |   \---Textures
|   |   +---LBuilding
|   |   |   +---Materials
|   |   |   +---Models
|   |   |   +---Prefabs
|   |   |   \---Textures
|   |   +---MBuilding
|   |   |   +---Materials
|   |   |   +---Models
|   |   |   +---Prefabs
|   |   |   \---Textures
|   |   +---Physics_Hulls
|   |   +---Road
|   |   |   +---Materials
|   |   |   +---Models
|   |   |   +---Prefabs
|   |   |   \---Textures
|   |   \---SBuilding
|   |       +---Materials
|   |       +---Models
|   |       +---Prefabs
|   |       \---Textures
```

## 旧规范优缺点

**缺点**

- 每种游戏对象下很多资产类型的文件夹，比较重复。如M1/(Materials,Models,Textures,Prefabs)。可通过Unity的Project下文件搜索过滤器。

- 场景3D按场景分类资源，场景间资源共用比较少，从场景间分离出共用资源较难快快快*作。

- 资源文件没有单独命名，比较依赖所属分类文件夹。

**优点**

- 主观上展现资产比较清晰

## 新规范优缺点

**优点**

- 美术资源Prefab分离策划程序配置，美术纯资源可直接迁移到美术工程，逻辑配置的预制件不迁移到美术工程。
- 按预制件美术资源所属名称设置预制件层级Layer？因为是美术资源的预制件，可通过工具批量根据规则设置层级。比如是机甲预制件资源，根据名称和目录自动设置层级。

 

![img](https://d7n9vj8ces.feishu.cn/space/api/box/stream/download/asynccode/?code=MzU3MDdhOTk1YWFhYTUxZGE0MmQ3YjRmMjA2YzIyYzBfUEgxTkk5emh0czByZXNtNWFYdUF2ZXhxZ2o1RlpnM1ZfVG9rZW46Ym94Y25LQlZVcDhWamJDWjduSnk3WUFEUmxmXzE2NDE2MzQzMzY6MTY0MTYzNzkzNl9WNA)



- 不再创建文件夹叫Models，Textures，或者Materials。把所有相关类型资产文件放在同一个文件夹。制作人员编辑资源时，方便预制件，模型，材质球，贴图一起编辑。而不是打开一个个文件夹，找到相关资源。制作人员可通过Unity的Project目录资源类别的方法搜索

![img](https://d7n9vj8ces.feishu.cn/space/api/box/stream/download/asynccode/?code=NWQzNGZlNjliMTJhMTU0NjQ2NzNhZjlhZTZhMDU5ZDRfeFpRWGhrU2hBTnRTcU41MTlFWVlieWVBQlVoZTRoc1RfVG9rZW46Ym94Y25nSmI4cmpjcTNtM2hnM2MyVHg5TzFCXzE2NDE2MzQzMzY6MTY0MTYzNzkzNl9WNA)

- 以前最后一个序号只为匹配命名格式，无实际意义，现在可以不填写
- 场景3D资源Dec改名为Props，因为这些资源会在场景中大量重复使用

## 综上所述

资源文件目录和命名需要考虑的因素有

1. 文件夹命名的粒度
2. 项目资源文件规划。
3. 美术资源自动化检查和设置工具
4. 上下游资源使用的习惯
5. 不能混用多套目录规则，各组的规则基本保持一致。
6. 工程结构最好的情况是，一目了然，不需要专门写备注“这是干什么的”
7. 方便一些自动化工具录入规则：预制件层级设置工具等

# 工程结构

对资源目录的规范管理和资源文件同等重要，都应该像法律一样被严格遵守。不规范的目录结构会导致严重的混乱。

```Shell
\---Art
    +---Characters
    |   +---MaterialLibrary
    |   +---TexturesLibrary
    |   +---ModelLibrary    
    |   +---NPC
    |   \---Players
    |       +---M1
    |       |   +---Configs
    |       |   \---Animations
    |       |       +---Body
    |       |       \---Equip
    |       \---M5
    |           |   M_M5_Bag_1.mat
    |           |   M_M5_WeaponDH_1.mat
    |           |   P_M5_CloakingL_1_Bip001LThigh_Skin.prefab
    |           |   P_M5_Model.prefab
    |           |   P_M5_WeaponDH_1_RH_Skin.prefab
    |           |   SK_M5_Body_1_Skin.fbx
    |           |   SK_M5_CloakingL_1_Bip001LThigh_Skin.FBX
    |           |   SK_M5_WeaponDH_1_RH_Skin.FBX
    |           |   T_M5_Bag_1_AO.tif
    |           |   T_M5_Bag_1_D.tif
    |           |   T_M5_Bag_1_E.tif
    |           |   T_M5_Bag_1_MADS.png
    |           |   T_M5_Bag_1_N.tif
    |           |   
    |       |   +---Configs
    |       |   \---Animations
    |               +---Body
    |               |       @M5_Ascend1.fbx
    |               |       @M5_DashB1.fbx
    |               |       @M5_Melee1_1_LH_MeleeAt1.FBX
    |               |       @M5_UVAL1_1_Skill2.FBX
    |               |       
    |               \---Equip
    +---Effects
    |   +---Effect_Scene
    |   +---Effect_Skill
    |   +---Effect_Whitebox
    |   +---Effect_Npc
    |   +---Common
    |   |   +---Models
    |   |   \---Textures
    +---Environments
    |   +---Architecture
    |   |   +---Buildings
    |   |   |       M_Building_Command_1_1_1.mat
    |   |   |       Sk_Building_Command_1_1.FBX
    |   |   |       T_Building_Command_1_1_1_AO.tif
    |   |   |       T_Building_Command_1_1_1_D.tif
    |   |   |       T_Building_Command_1_1_1_MADS.tif
    |   |   |       T_Building_Command_1_1_1_N.tif
    |   |   |       
    |   |   +---Indoor
    |   |   +---Props(包括格纳库道具模型及动画)
    |   |   \---Roads
    |   +---Decals
    |   +---MaterialLibrary
    |   |   +---Metal
    |   |   +---Noise
    |   |   |       T_Noise_1.png
    |   |   |       T_Noise_Clouds.tif
    |   |   |       T_Noise_Wind.tif
    |   |   |       
    |   |   +---Plastic
    |   |   \---Soil
    |   +---Nature
    |   |   +---Foliage
    |   |   +---Stones
    |   |   \---Trees
    |   +---WhiteBox
    |   \---Terrain
    +---Maps
    |   \---Map_Tokyo
    +---Shaders
    |   +---Editor
    |   +---Graphs
    |   |       SF_Skin_1.shadergraph
    |   |       
    |   \---SubGraphs
    +---Movie
    |   +---Movie_Character
    |       +---TimelineLibrary(共用)
    |       +---Players
    |           +---M1
    |               +---Timeline
    |               \---Animations
    |           \---M5
    |   +---Movie_Map
    |   +---Movie_Playback
    |   +---Movie_UI
    \---UI
```

**文件目录使用分职能管理文件**

- 特效，Effects文件夹

- 地编，Maps文件夹

- 场景模型，Enviroments文件夹

- 角色模型，Characters文件夹

- 设计，UI文件夹

- 着色器（TA），Shaders文件夹



## 文件夹命名

### 文件夹命名约定

- 使用PascalCase大小写规范

 文件夹的命名需要遵守PascalCase规范，也就是所有单词的首字母大写，并且中间没有任何连接符。例如DesertEagle, RocketPistol, and ASeriesOfWords，参照大小写规范。

- 不要使用空格

 绝对不要在目录名中使用空格。空格会导致引擎以及其他命令行工具出现错误，同样，也不要把你的工程放在包含有空格的目录下面。

- 不要使用其他Unicode语言字符或奇怪的符号

 如果你游戏中的角色的名字叫做'Zoë'，那么文件夹要其名为Zoe。在目录名中使用这样的字符的后果甚至比使用空格还严重，因为某些引擎工具在设计时压根就没有考虑这种情况。

- 记住永远在目录名中只使用a-z, A-Z, 和 0-9这些安全的字符，如果你使用了类似于`@, -, _, ,, *, 或者 #`这样的字符，一些软件和工具会出问题。

### 文件夹类型表

#### 场景3D

| **场景元素类型** |                                      |
| ---------------- | ------------------------------------ |
| Building         | 建筑物                               |
| Indoor           | 室内（不与室外模型一体的室内、通道） |
| Prop             | 小物件                               |
| Child            | 挂件（只会挂靠在其他建筑上的物件）   |
| Road             | 道路（面数比较高）                   |
| Inside           | 破碎建筑物等物体的內构               |
| Tree             | 树                                   |
| Foliage          | 灌木丛，花草，蕨类植物               |
| Decal            | 场景贴花                             |
| Stone            | 石头，岩石，悬崖                     |
| Destruction      | 破碎体                               |
| Terrain          | 地形                                 |



## 目录使用

请不要将未使用的美术资源放到主干工程，可放在美术工程。

### 通用资源Library

如果项目使用主材质，layered materials，或任何形式的可重用材质或纹理，不属于资产的任何子集，这些资产应该位于这里。如下面文件夹

- 3D材质库（MaterialLibrary），放一些通用的材质球,Tilling材质可放在这里，命名中不用加Tilling。

- 3D贴图库（TextureLibrary）,放一些通用的贴图，和一些Noise贴图。
- 特效通用资源库（TextureLibrary）
- UI通用资源库（GUILibrary）

# 资源命名约定

对于资源的命名的规范应该像法律一样被遵守。一个项目如果有好的命名规范，那么在资源管理、查找、解析、维护时，都会有极大的便利性。

## 基本命名规则 `前缀_基础资产名称_变体_后缀`

（旧基本命名规则）元素类型_场景名称_美术自定义名字_排序

记住`前缀_基础资产名称_变体_后缀`模式并按照常识就可以保证良好的资产名称。以下是关于每个元素的一些详细规则。

**前缀和后缀**由资产类型通过下面的资产名称缩写表确定。后缀如果没有可为空

**基础资产名称**表示**相关资产的逻辑分组**，所有资产都应该有一个基础资产名称，**基础资产名称字段只能有一**个。这个逻辑组中的任何资产都应该遵循`前缀_基础资产名称_变体_后缀`。基础资产名称应该由与这组资产的上下文相关的简短且易于识别的名称确定。例如，如果有一个名为M1的机甲角色，那么M1的所有资产都将具有M1的基础资产名称。

**变体**是一个简短且易于识别的名称，对于资产的独特和特定变体，表示资产的逻辑分组，这些资产是**基本资产名称的子集**。对于资产的唯一但通用的变体，Variant是一个从1开始的数字。例如，如果生成一些难以描述的岩石，那么它们就会被命名为Rock_1、Rock_2、Rock_3等等。如果有超过100个资产，应该考虑使用不同的基名或使用多个变体名来组织它们。

根据资产变体的制作方式，您可以将变体名称链接在一起，**变体字段可以多个**。例如，如果正在创建地板资产，应该使用基本名称Flooring，并带有**连锁变体**，如Flooring_Marble_1， Flooring_Maple_1，Flooring_Tile_Squares_1，P_Building_Wall_1_Base，P_Building_Wall_2_Base，P_Building_Wall_1_A。T_Dirt_Blue_D,M_Dirt_Blue



变体名可用用阿拉伯数字来排序，**兄弟用A,B,C,D****（同一个妈生的）**。

**使用前缀的好处**

- List item添加前缀来区分资产类型，例如“P_”命名预制件，"Scn_"命名场景。当我们发现预制件和模型很容易混淆时，我们开始使用前缀。
- 当把材质球，预制件，模型，贴图放在一起时，命名带有前缀，可区分不同类型资源，因为旧规则不同类型资源会有重名。
- 这种方法的另一个优点是，在搜索字段中输入"P_Bear"而不是t:Prefab Bear，它更短。

## 资产名称缩写表

当给一个资源命名的时候，请参照以下表格来决定在基本资源名前所使用的前缀

### 全局

| **资产类型**            | **前缀** | **后缀**  | **备注**                                                     |
| ----------------------- | -------- | --------- | ------------------------------------------------------------ |
| Scene                   | *        |           | 例如 `Scenes/A4_C17_Parking_Garage.unity`                    |
| Scene (Lighting)        |          | _Lighting |                                                              |
| Scene (Geometry)        |          | _Geo      |                                                              |
| Scene (Gameplay)        |          | _Gameplay |                                                              |
| Prefab                  | P_       |           |                                                              |
| Probe (Reflection)      | RP_      |           |                                                              |
| Probe (Light)           | LP_      |           |                                                              |
| Volume                  | V_       |           |                                                              |
| Trigger Area            |          | _Trigger  |                                                              |
| Material                | M_       |           |                                                              |
| Physical Material       | PM_      |           | 物理材质球                                                   |
| Static Mesh             | SM_      |           |                                                              |
| Animation Mesh          | @        |           | @M5_Ascend1.fbx                                              |
| Skeletal Mesh           | SK_      |           |                                                              |
| Bone Constraint配置文件 | BC_      |           | Blender的骨骼约束文件，存放位置例如：M1/Configs/BC_M12_Arm_1_L |
| Slot插槽配置文件        | Slot_    |           | 特效或者机甲水贴插槽配置文件，M1/Configs/Slot_M12_1          |
| Destructible Mesh       | DM_      |           | 破碎模型                                                     |
| Mesh Collider模型       | SM_      | _Collider | 区别于原始模型专门做的                                       |
| Skeleton                | SKEL_    |           |                                                              |
| Rig                     | RIG_     |           |                                                              |
| Animation Clip          | A_       |           |                                                              |
| Animation Controller    | AC_      |           |                                                              |
| Avatar Mask             | AM_      |           |                                                              |
| Texture                 | T_       | _?        | 见贴图                                                       |
| Visual Effects          | VFX_     |           |                                                              |
| Particle System         | PS_      |           |                                                              |
| Light                   | L_       |           |                                                              |
| Camera (Cinemachine)    | CM_      |           | Virtual Camera                                               |



### 贴图

文件扩展名: `PNG`, `TIFF` or `HDR`

| **贴图名称**    | **贴图类别**                    | **前缀** | **后缀** | **备注**       |
| --------------- | ------------------------------- | -------- | -------- | -------------- |
| 颜色贴图        | Base Color : (tif 48位）        | T_       | _D       |                |
| 颜色贴图带Alpha | Base Color With Alpha/Opacity   | T_       | _A       |                |
| 混合贴图        | Texture (Packed) (tif 64位）    | T_       | _*       | *可看下面表    |
| 法线贴图        | Normal Map : (tif 48位）        | T_       | _N       |                |
| 自发光贴图      | Emission : (tif 48位）          | T_       | _E       |                |
| AO贴图          | Ambient Occlusion : (tif 48位） | T_       | _AO      |                |
| 曲率图          |                                 | T_       | _C       |                |
| 油污图          |                                 | T_       | _G       |                |
| 序列图          | 可有不同贴图类型                | TS_      | _*       | TS_X_D，TS_X_N |
| 遮罩            |                                 |          |          |                |
| 地形高度贴图    | Height :(tif 48位)              |          | _H       |                |
| Cubemap贴图     | Cubemap:(exr)                   | TC_      |          |                |
| Render Target   |                                 | RT_      |          |                |



不分二方连续或者四方连续贴图，由材质名称即可判定

#### 贴图合并

通常的做法是将多层纹理数据打包到一个纹理数据中。 这方面的一个例子是将金属度、环境遮蔽、细节遮罩、光滑度、分别打包为纹理的红、绿、蓝、Alpha通道。 要确定后缀，只需将上面给定的后缀字母堆叠在一起，例如_MADS。 图示如下：

![img](https://d7n9vj8ces.feishu.cn/space/api/box/stream/download/asynccode/?code=OTkzNjQ2M2ZhNzQxZTY4MGMxYmY2MDFjOTkzOWYxZmZfWVRQcGszR2FzM0p3RHF1N2lCMVVKRGFTWTNQOERzcHhfVG9rZW46Ym94Y245VThhMDVvWWc2alJoaDNJQ1dhZU5oXzE2NDE2MzQzMzc6MTY0MTYzNzkzN19WNA)

 注意当MADS贴图导入Unity请不要勾sRGB。

### LOD

| **模型文件等级** | **文件后缀** | **备注**                     |
| ---------------- | ------------ | ---------------------------- |
| HD               | _HD          | 展示型模型，不用于战斗场景中 |
| LOD 第0级        |              | 模型面数最多                 |
| LOD第一级        | _LOD1        |                              |
| LOD第二级        | _LOD2        |                              |
| LOD第三级        | _LOD3        | 模型面数最低，模型简模轮廓   |



### 关卡文件

无法复制加载中的内容

关卡分成多个加载场景，美术资源场景，灯光场景

### 场景3D

#### 文件命名中的变体字段

可能是下面这些，可新增

| **变体名称** | **英文名称** | **备注**         |
| ------------ | ------------ | ---------------- |
| 是否破碎     | Break        |                  |
| 是否动画     | Anim         |                  |
| 底座         | Base         |                  |
| 是否合组     | Group        | 对预制件打组生成 |

#### 物理文件

| **资产类型**      | **前缀** | **后缀** | **备注** |
| ----------------- | -------- | -------- | -------- |
| Physical Material | PM_      |          |          |
| Physics Asset     | PHYS_    |          | 破碎     |
| Destructible Mesh | DM_      |          |          |

#### 3D 模型 (3ds Max或者Blender)

3ds Max中的所有网格

| **资产类型**  | **前缀** | **后缀**   | **备注**                     |
| ------------- | -------- | ---------- | ---------------------------- |
| Mesh          |          | Mesh_LOD1* | 如果模型使用LOD,使用后缀lod* |
| Mesh Collider |          | _Collider  |                              |

#### 

例：

场景建筑物

| **资产类型** | **资产名字**       |
| ------------ | ------------------ |
| 预制件       | P_Flooring_Marble  |
| 模型         | SM_Flooring_Marble |
| 材质         | M_Flooring_Marble  |
| 贴图         | T_Flooring_Marble  |

岩石

| **资产类型**           | **资产名字** |
| ---------------------- | ------------ |
| Static Mesh (1)        | S_Rock_1     |
| Static Mesh (2)        | S_Rock_2     |
| Static Mesh (3)        | S_Rock_3     |
| Material               | M_Rock       |
| Material Variant(Snow) | M_Rock_Snow  |

| **资产类型**   | **资产名字**    |
| -------------- | --------------- |
| 底座残骸预制件 | P_Building_Base |

#### Unity HDRP Decal Projector

| **资产类型** | **资产名字**  |
| ------------ | ------------- |
| 预制件       | P_Decal_Stain |
| 材质         | M_Decal_Stain |
| 贴图         | T_Decal_Stain |

#### 



### 角色3D

| **大类** | **共同命名（X）**                                        | **FBX**                         | **带骨骼绑定FBX** | **预制件** | **材质** | 贴图         | 动画                                     | 共同命名例子                                            |
| -------- | -------------------------------------------------------- | ------------------------------- | ----------------- | ---------- | -------- | ------------ | ---------------------------------------- | ------------------------------------------------------- |
| 机身     | 机甲编号_机身部位_机身部位编号                           | SM_X                            | SK_X              | P_X        | M_X      | T_X_贴图类别 | @机甲编号_机身部位_机身部位编号_动画名字 | M1_Head_1                                               |
|          | 手臂和腿要分左右<br/>机甲编号_机身部位_机身部位编号_左右 |                                 |                   |            |          |              |                                          | M1_Arm_1_L<br/>M1_Arm_1_R<br/>M1_Leg_1_L<br/>M1_Leg_1_R |
|          | 装备（含武器）                                           | 机甲编号_装备类型_装备编号_左右 | SM_X              | SK_X       | M_X      | T_X_贴图类别 | @机机甲编号_装备类型_装备编号_动画名字   | M1_WeaponBHL_1                                          |



#### 机甲编号

机甲编号

| **机甲编号**   | **ID（序号累加）** | **名称**       | **英文名称** |
| -------------- | ------------------ | -------------- | ------------ |
| M              | 1                  | 小白           | M1           |
| **驾驶员编号** | **ID**             | **名称**       | **英文名称** |
| C              | 1                  | 驾驶员         | C1           |
| **NPC编号**    | **ID**             | **名称**       | **英文名称** |
| NRA            | 1                  | NPC机甲0.3强度 | NRA1         |
| NRB            | 1                  | NPC机甲0.5强度 | NRB1         |
| NV             | 1                  | NPC载具        | NV1          |
| NT             | 1                  | 防御塔单位     | NT1          |
| NB             | 1                  | Boss类单位     | NB1          |

#### **角色驾驶员**

编号：C加序号

**模型命名**

前缀_驾驶员编号_部位_序号

例：

SM_C1_Body_1     

硬表面部位，前缀_驾驶员编号_TrimSheet_序号

例：

SM_C1_TrimSheet_1

**材质球命名**

 前缀_驾驶员编号_部位_序号

例：

M_C1_Body_1

硬表面部位，前缀_驾驶员编号_颜色_序号

例：

M_C1_Black_1 

#### 武器、装备命名

| 武器装备前加挂载点名称 |           |          | 相同                                                         |
| ---------------------- | --------- | -------- | ------------------------------------------------------------ |
| 挂载点                 | 命名      |          | + 后缀L  R  BH  DH  SH                                       |
| Hand         手        | HandX     | 手持     | 例：HandX_1_BH          两把武器，双持                           _DHL         一把武器左手拿右手扶                   _DHR        一把武器右手拿左手扶                   _SHL         一把武器左手拿                   _SHR        一把武器右手拿    HandX_1_L               左臂挂载武器    HandX_1_R              右臂挂载武器 + 后缀L  R  BH  DH  SH  区分左右，不加则不分左右 |
| Arm           手臂     | ArmX      | 手臂挂载 |                                                              |
| shoulder    肩         | shoulderX | 肩部挂载 |                                                              |
| Back          背部     | BackX     | 背部挂载 |                                                              |
| Leg            腿部    | LegX      | 腿部挂载 |                                                              |



| 武器装备命名(X)                   |              |
| --------------------------------- | ------------ |
| Rifle                             | 步枪         |
| Pistol                            | 手枪         |
| Cannon                            | 加农炮       |
| Grenade                           | 投弹炮       |
| Funnel                            | 浮游炮       |
| Electromagnetism                  | 电磁炮       |
| Axe                               | 斧头         |
| Hooklock                          | 勾爪         |
| Shield                            | 盾牌         |
| Spear                             | 长矛         |
| Hammer                            | 长锤子       |
| Sword                             | 长\短剑      |
| RobotArmKnife                     | 机械臂刀类   |
| RobotArmGun                       | 机械臂枪炮类 |
| launcher                          | 发射装置     |
| Scanner                           | 扫描装置     |
| Cloaking                          | 隐身装置     |
| Energy+武器名称                   |              |
| EnergyWeapon                      | 能量武器     |
| 装备名称+ L  R   不加代表不分左右 |              |
| Bag                               | 背包         |
| Missile                           | 导弹舱       |
| MissileL                          | 导弹舱 左    |
| MissileR                          | 导弹舱 右    |
| Uav                               | 无人机       |



#### 机身部位

| **机身部位** | **名称** | **范围描述**        | **图示颜色** |
| ------------ | -------- | ------------------- | ------------ |
| 躯干         | Torso    | 躯干,胸，腹，驾驶舱 | 绿色         |
| 头           | Head     | 天线，头，脖子      | 黄色         |
| 手           | Arm      | 肩，手臂，手掌      | 紫色         |
| 腿           | Leg      | 大腿，小腿，脚掌    | 红色         |



如图：不同颜色代表不同部位换装（图示仅参考）

![img](https://d7n9vj8ces.feishu.cn/space/api/box/stream/download/asynccode/?code=YzA3ZDA3MzY4MjBkYWE4OWE3Njc3Yzk5MDU2MDI4YzBfTGZXVHNoZVBUMnM0QklqajZpT25WbW9ZWk8waVZiUjdfVG9rZW46Ym94Y256YU1GZG12cm12WWdvWTlDeUp1ZFFlXzE2NDE2MzQzMzg6MTY0MTYzNzkzOF9WNA)



动画名字是不确定命名字段。

如果是临时模型，需加后缀字段_Temp。临时模型不会对文件进行规则检查。

例：SK_M2_Torso_1_Temp



例

机甲M1相关资源命名

| **资产类型**             | **资产名字**  |
| ------------------------ | ------------- |
| Skeletal Mesh            | SK_M1_Torso_1 |
| Material                 | M_M1_Torso_1  |
| Texture (Diffuse/Albedo) | T_M1_Torso_D  |
| Texture (Normal)         | T_M1_Torso_N  |
| Texture (Body Diffuse)   | T_M1_Torso_D  |

#### **材质球**

##### **基础材质**

前缀_机体编号_部件颜色（自定义）_序号(从数字1开始）

例：M_M1_Red_1

  M_M1_Yellow_1

##### **自发光材质**

前缀_机体编号_部件颜色_序号_E

例：M_M1_Yellow_1_E

##### **功能灯光材质**

前缀_机甲编号_灯光功能\部件_序号_E

例：M_M1_Propeller_1_E  喷口灯光

| 灯光功能    |            |
| ----------- | ---------- |
| Propeller   | 喷口       |
| Polishing   | 系统提示   |
| Ultimate    | 大招提示   |
| Ultimate_CD | 大招CD提示 |
| EIC         | EIC能量    |
| Braking     | 推进器     |



### Decalmachine资产文件

| **资产类型**         | **基础资产名称** | 备注                         |
| -------------------- | ---------------- | ---------------------------- |
| 刻线类贴花或者裁剪片 | PanelAtlas       |                              |
| 凹凸细节贴花         | NormalAtlas      | 合并SimpleAtlas和SubsetAtlas |
| 裁剪片               | TrimSheets       |                              |
| 水贴                 | InfoAtlas        |                              |

适用贴图命名

|                                                     | 前缀 | 后缀  | PanelAtlas        | NormalAtlas        | TrimSheets        | InfoAtlas     |
| --------------------------------------------------- | ---- | ----- | ----------------- | ------------------ | ----------------- | ------------- |
| 颜色贴图带Alpha                                     | T_   | _A    |                   |                    |                   | T_InfoAtlas_A |
| (R)Ao (G)Curvature (B)Height (A)SubsetMask 遮罩贴图 | T_   | _ACHS | T_PanelAtlas_ACHS | T_NormalAtlas_ACHS | T_TrimSheets_ACHS |               |
| 法线贴图                                            | T_   | _N    | T_PanelAtlas_N    | T_NormalAtlas_N    | T_TrimSheets_N    |               |
| 自发光贴图                                          | T_   | _E    |                   | T_NormalAtlas_E    | T_TrimSheets_E    |               |



### UI

| **资产类型**     | **前缀** | **后缀** | **备注** |
| ---------------- | -------- | -------- | -------- |
| Font             | Font_    |          |          |
| Texture (Sprite) | T_       | _GUI     |          |



| 前缀 | 基础资产名称 | 变体1 | 变体2  | 变体3    | 后缀 |
| ---- | ------------ | ----- | ------ | -------- | ---- |
|      | 系统         | 模块  | 子系统 | 元件序号 |      |



## 

#### 

### Shader命名规则

根据Shader的功能来分类文件夹。命名中前缀可用SG_（Shadergraph编写）,

 如特效通用Shader:SG_StandardEffect



### Movie影音组命名

| 类别            | Timeline命名                              |                                                              |
| --------------- | ----------------------------------------- | ------------------------------------------------------------ |
| Movie_Map       | TL_场景名称（_子场景名称）_美术资源名称_1 | Map_Factory/TL_Zhengbeicang_ChangePlayer_1.playable，P_Zhengbeicang_ChangePlayer_1.prefab |
| Movie_Character | TL_M1_Out_1 TL_M1_Skill_1                 |                                                              |
| Movie_UI        |                                           |                                                              |
| Movie_Playback  |                                           |                                                              |





# 角色3D要求

### 面数

| 级别 | 模型面数（三角面） | 备注       |
| ---- | ------------------ | ---------- |
| LOD0 | 十万以内           | 不包含倒角 |

### 材质球数量

十个以内（包含十个）

# 场景层级结构

一个关卡可含多个场景

```
美术资源场景
    Architecture
    Nature
    Terrain
    Decals
    Effect

美术灯光及后期场景
    Sun
    Lights
    Sky and Fog Volume
    PostProcessing
    
逻辑场景（策划和程序管理）
    Cameras
    _Dynamic
       Actors
       Items
       ...
```

### 设置要求

- 所有空的对象应该定位在0,0,0，使用默认的旋转和缩放。
