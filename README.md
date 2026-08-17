# Niu Lai Translator / 牛来低模转译器

将用户提供的图像重建为一种“制作能力明显不足”的原始低模 3D 场景：不是精致的低模艺术，也不是模糊、像素化或滤镜处理，而是让低质量真正来自建模、比例、绑定、碰撞、材质、资产、灯光和渲染能力的全面不足。

## 核心效果

- 极低面数：使用少量大块几何体，不以密集小三角面伪装成低模。
- 比例失真：主动改变人物与动物的头身比、肢体长度、躯干宽度和关节大小。
- 僵硬绑定：保留动作含义，但让肩、肘、腕、膝和重心显得机械、不自然。
- 局部穿模：在袖口、肩部、肘部、服装、毛发或道具接触处加入少量可读的碰撞失败。
- 贫乏材质：以低分辨率 diffuse/base color 为主，弱化或移除完整 PBR、法线、置换、皮肤、织物和毛发模型。
- 重复资产：明显复用少量树木、木桩、岩石、建筑、贴图和角色部件。
- 拙劣灯光：使用简单单光源、硬阴影、曝光不均和较弱的接触关系。

## 目录结构

```text
NiuLai-Skill/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── prompt-blueprint.md
    ├── quality-and-recovery.md
    └── style-system.md
```

## 安装

将整个 `NiuLai-Skill` 文件夹放入支持 Skills 的工具所使用的 Skills 目录中。不要只上传 `SKILL.md`，因为主文件会按需读取 `references/` 中的风格、提示词和质量检查规则。

如果通过 GitHub 使用，可直接克隆或下载仓库，并将仓库目录作为一个完整 Skill 安装。

## 调用方式

```text
/niu-lai-translator
启用牛来低模转译器
把这张图重制成制作能力很差的早期 3D 动画截图
```

提供原图后，如果没有额外参数，Skill 会默认直接执行 `primitive_folk_cgi` 预设。也可以要求先给方案、降低劣化强度、提高身份相似度或指定输出比例。

## 默认参数

```yaml
skill: niu-lai-translator
preset: primitive_folk_cgi
reconstruction_strength: extreme
anchor_lock: strict
identity_lock: medium
detail_budget: very_low
geometry: primitive_low_poly
polygon_budget: extremely_low
proportion_fidelity: deliberately_broken
pose_lock: semantic_action_only
pose_quality: stiff_failed_rig
collision_quality: visible_clipping
clipping_count: 1_to_3
texture_resolution: very_low
material_model: diffuse_only_mismatched
asset_reuse: heavy
lighting: naive_single_light
ratio: source_ratio
```

## 设计原则

Skill 只严格保留主体数量与类型、画面布局、动作含义、镜头、场景类型、主要道具和大色块。具体姿态、轮廓、身体比例、关节角度、服装贴合与网格分离可以被主动破坏。

低质量应来自完整的生产流程限制。若结果仍然具有正确比例、自然姿态、干净碰撞、完整 PBR 材质、丰富背景或电影级灯光，即使画面具有低模外观，也应视为失败并重试。

## 文件说明

- `SKILL.md`：触发条件、默认工作流、核心约束与输出规则。
- `references/style-system.md`：风格支柱、预设和不同原图类型的处理策略。
- `references/prompt-blueprint.md`：参数体系、完整提示词模板与负面约束。
- `references/quality-and-recovery.md`：反向质量门槛、评分方法与失败恢复提示。
- `agents/openai.yaml`：ChatGPT/Codex 中显示名称、简述和默认调用提示。

## 边界

- 不通过恐怖、血腥、肢体缺失或身体暴露制造“穿模”。
- 不随意增加人物、动物、牛角、字幕、标志、界面或原图不存在的道具。
- 不把 VHS、马赛克、JPEG 损坏、重度噪点或黑暗调色当作主要劣化手段。
- 对真实人物保持年龄、族裔、身体类别及人物关系不变。

---

**保留大关系，主动放弃精致还原；让低质量来自整套生产能力，而不是后期滤镜。**
