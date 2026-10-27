# concflock

**检测多个智能体操作同一资源时的冲突。**

`concflock` —— 在并发访问序列中找出会互相覆盖的写操作，标出冲突窗口

- 零依赖，Python 3.10+ 标准库即可运行
- 单文件，`concflock.py` 拷走就能用
- 不联网、不写文件

<!-- ipos:install -->
## 安装

零依赖，Python 3.10+ 即可：

```bash
pip install woman1copy-concflock
```

装完直接用命令名调用：

```bash
concflock --help
```

也可以不用安装，直接把 `concflock.py` 拷走用——它只依赖标准库。

## 为什么需要它

冲突判定基于读写顺序，不是单纯看是否同一资源

它遵守下面几条自己定的规矩：

1. **只报告能定位到具体位置的结论**，不做语义猜测。
2. **规则表公开**，每条命中都能对应到 智能体并发冲突 领域的一条明示规则。
3. **输入为空或格式不对时明确报错**，不静默返回空结果。

## 用法

```bash
python concflock.py --file input.txt
python concflock.py --text "示例内容"
python concflock.py --file input.txt --json
```

加 `--json` 可以拿到机器可读的结果，便于接到流水线里。

## 已知局限

- 相似度按字符与词估算，不等于向量相似度。
- 不联网，不做语义检索。

## 跑测试

```bash
python test_concflock.py
```

测试用独立的断言与临时数据，不污染工作目录。

## 来源与参考

- Python 标准库文档：<https://docs.python.org/3/>
- GitHub 仓库：<https://github.com/woman1copy/concflock>

---

## 关于作者

woman1copy 做智能体并发冲突相关的问题。这个工具先替你回答一个具体问题，再谈别的。

- 个人主页：<https://woman1copy.github.io>
- 仓库：<https://github.com/woman1copy/concflock>

## 许可

MIT，见 [LICENSE](LICENSE)。
