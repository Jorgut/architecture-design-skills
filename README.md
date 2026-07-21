# Architecture Design Skills

面向建筑师、规划师和空间设计师的 Agent Skills 集合。

## Skills

| Skill | 用途 |
| --- | --- |
| `space-program` | 计算与审查规划指标、面积配比、停车和容量估算 |
| `arch-prompt` | 为建筑、室内和景观可视化生成可执行的图像提示词 |

两个技能保持独立，以确保自动触发准确，并避免加载无关上下文。

## Install

将需要的技能目录复制到 Agent 技能目录：

```bash
cp -R skills/space-program ~/.agents/skills/
cp -R skills/arch-prompt ~/.agents/skills/
```

也可以使用支持 Agent Skills 规范的安装器，选择 `skills/` 下的对应目录。

## Safety

`space-program` 提供计算方法和非规范性经验值，不替代当地现行规划、消防、日照、停车或无障碍法规。正式项目必须核验适用地区、版本和主管部门要求。

## License

MIT
