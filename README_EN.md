# mmkc-tiktok-capcut-skill
> MMKC project description: Create new CapCut drafts from existing templates, extract template styles, validate draft structure, and inspect or repair AI-video artifacts.
> MMKC 项目描述：基于现有 CapCut 草稿模板生成新草稿，提取模板样式、验证草稿结构，并检查或修复 AI 视频痕迹。


[中文](./README.md) | English

`mmkc-tiktok-capcut-skill` is a Codex skill for creating editable CapCut drafts, extracting template styles, validating draft structure, and checking AI-video artifacts. It turns a local AI video plus an existing CapCut template draft into a new draft that CapCut can index and open.

## Features

- Create a new CapCut draft from an existing template draft.
- Extract caption styles, transitions, animations, and effects.
- Validate root indexes, nested timelines, and media paths.
- Sample frames from a video or draft and create contact sheets for review.
- Plan artifact repair windows from a review JSON file.
- Run local RIFE interpolation for high-quality frame filling.

## Install

```bash
mkdir -p ~/.codex/skills
cp -R mmkc-tiktok-capcut-skill ~/.codex/skills/
```

The default CapCut draft root is:

```bash
$HOME/Movies/CapCut/User Data/Projects/com.lveditor.draft
```

Override it when needed:

```bash
export CAPCUT_DRAFT_ROOT="/path/to/com.lveditor.draft"
```

## Usage

Create a draft:

```bash
node mmkc-tiktok-capcut-skill/scripts/create-capcut-draft.mjs \
  --template "template-draft-name" \
  --video "/path/to/ai-video.mp4" \
  --name "new-draft-name" \
  --captions "Hook\nProof\nCTA"
```

Validate a draft:

```bash
node mmkc-tiktok-capcut-skill/scripts/validate-capcut-draft.mjs --draft "new-draft-name"
```

Sample frames for review:

```bash
node mmkc-tiktok-capcut-skill/scripts/extract-ai-artifact-frames.mjs \
  --video "/path/to/ai-video.mp4" \
  --output-root mmkc-tiktok-capcut-skill/projects/ai-artifact-qa
```

## Safety

Do not commit CapCut drafts, videos, screenshots, interpolation intermediates, or review outputs. Keep run artifacts under `projects/` or another local work directory.
