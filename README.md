# Architecture Design Skills

面向建筑师、规划师和空间设计师的 Agent Skills 集合。仓库级名称代表技能目录；每个目录都是可独立安装、独立触发的 Skill。

## Skills

| Skill | 用途 |
| --- | --- |
| `architectural-design-workflow` | 建筑与室内项目的统一入口：梳理任务、选择设计阶段、协调图纸/分析图/模型并检查交付一致性。 |
| `space-program` | 计算与审查规划指标、面积配比、停车和容量估算。 |
| `arch-prompt` | 为建筑、室内和景观概念可视化生成可执行的图像提示词。 |

`architectural-design-workflow` 是协调入口，`space-program` 与 `arch-prompt` 保持为并列专项技能，避免自动触发失准或无关上下文加载。安装三个目录后，入口可将专项任务交给对应技能；只安装所需技能也可以。

## Install

选择需要的目录复制到 Agent 技能目录：

```bash
cp -R skills/architectural-design-workflow ~/.agents/skills/
cp -R skills/space-program ~/.agents/skills/
cp -R skills/arch-prompt ~/.agents/skills/
```

也可以使用支持 Agent Skills 规范的安装器，分别选择 `skills/` 下的技能目录。

## Safety

`space-program` 提供计算方法和非规范性经验值，不替代当地现行规划、消防、日照、停车或无障碍法规。正式项目必须核验适用地区、版本和主管部门要求。

`arch-prompt` 可支持景观概念图像表达；它不替代完整的景观设计、地形/水文工程、种植施工或规范审查流程。

## License

MIT
