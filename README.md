# tokover

**按权重把提示词的 token 预算超限的额度分配到各项。**

`tokover` —— 按给定权重把总额度分配到各项，报告超分配项与利用率

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`tokover.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install xsmatis-tokover
```

装完直接用命令名调用：

```bash
tokover --help
```

也可以不用安装，直接把 `tokover.py` 拷走用——它只依赖标准库。

## 为什么需要它

超分配要显式报出来，而不是让分配结果静默超过总额度

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 提示词的 token 预算超限 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python tokover.py --file input.txt
python tokover.py --text "示例内容"
python tokover.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 预算是静态比例分配，不考虑实际执行顺序。
- 不接真实队列，只做分配表。

## 跑测试

```bash
python test_tokover.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/xsmatis/tokover>

---

## 关于作者

xsmatis 做提示词的 token 预算超限相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://xsmatis.github.io>
- 仓库：<https://github.com/xsmatis/tokover>

## 许可

MIT，见 [LICENSE](LICENSE)。
