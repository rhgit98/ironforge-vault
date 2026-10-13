---
title: Blender to Unity Pipeline Architecture Specification
aliases: [Pipeline Architecture, Tech Spec]
tags: [pipeline, tech, blender, unity, fbx]
created: 2026-10-12
updated: 2026-10-12
---

# ⚙️ Blender to Unity Pipeline Architecture Specification

> **Pipeline Version**: 1.1.0  
> **Source Engine**: Blender 5.x LTS  
> **Target Engine**: Unity 6 (URP 17.x)

---

## 1. Coordinate & Handedness Normalization

```text
       Blender Space                    Unity Space
       (Right-Handed)                  (Left-Handed)

            +Z (Up)                         +Y (Up)
              │                               │
              │                               │
              └─── +X (Right)                 └─── +X (Right)
             /                               /
            /                               /
          -Y (Forward)                    +Z (Forward)
```

### FBX Space Transform Rule
To prevent the common `-90°` pitch rotation on Root GameObjects in Unity:
* `axis_forward = '-Z'`
* `axis_up = 'Y'`
* `bake_space_transform = True`
* `apply_scale_options = 'FBX_SCALE_ALL'`

---

## 2. Unit Scale Mapping

| Parameter | Blender Value | Unity Value |
| :--- | :--- | :--- |
| **System** | Metric | Metric |
| **Unit Scale** | $1.0$ (Meters) | $1.0\text{ unit} = 1\text{ meter}$ |
| **Model Importer** | — | `useFileUnits = true`, `scaleFactor = 1.0` |

---

## 3. Humanoid Rig & Avatar Alignment

To ensure retargeting compatibility with third-party mocap libraries (such as the RPG Animations Pack Free):
1. **Rest Pose**: The model must be modeled and bound in a clean **horizontal T-Pose** (arms extending along the X axis, palms facing down, legs straight).
2. **Bone Naming Standards**:
   * Core: `Hips`, `Spine`, `Chest`, `Neck`, `Head`
   * Left Arm: `Left_Shoulder`, `Left_UpperArm`, `Left_LowerArm`, `Left_Hand`
   * Right Arm: `Right_Shoulder`, `Right_UpperArm`, `Right_LowerArm`, `Right_Hand`
   * Left Leg: `Left_UpperLeg`, `Left_LowerLeg`, `Left_Foot`
   * Right Leg: `Right_UpperLeg`, `Right_LowerLeg`, `Right_Foot`
3. **Unity Importer Setting**:
   * `animationType = 3` (`Humanoid`)
   * `avatarSetup = 1` (`CreateFromThisModel`)
