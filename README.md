## parseAndCombineMyClashRules

### 简介

这是一个可以自动合并多个订阅的信息，到我们指定的基础 `clash` 配置文件库中的脚本。

可能上面这段话说的不容易理解，我们来举个例子，我们购买了不少服务，每个服务商都提供了一个代理订阅地址，我们不想切换配置文件，想把所有我们购买的服务都合并到一个配置文件，并且采用网络上面维护比较好的规则。



---
* [支持解析的代理规则](#支持解析的代理规则)
* [遇到无法解析](#遇到无法解析)
* [支持的基础规则](#支持的基础规则)
* [未来想要做的](#未来想要做的)
* [配置文件说明](#配置文件说明)
* [使用方法](#使用方法)
* [特别说明](#特别说明)
* [鸣谢](#鸣谢)

---

### 支持解析的规则

目前可以解析 clash 的 yaml 文件，base64 的配置文件（目前只支持解析了 v2ray 的，ss 由于我这边没有测试数据暂不支持）

---

### 遇到无法解析

提 issue

---

### 支持的基础规则
- [x] [Hackl0us](https://github.com/Hackl0us/SS-Rule-Snippet)
- [x] [ConnersHua](https://github.com/ConnersHua/Profiles) 这个目前只支持了 Pro 的规则，回国规则不想支持了，毕竟我想
- [ ] [lhie1](https://github.com/lhie1/Rules)

---

### 未来想要做的

- [ ] 上传生成后的配置文件到 cdn
- 支持更多基础规则
- 支持解析更多格式的代理文件

---

### 配置文件说明

文件太长，参考 [配置文件说明](.config.yaml)。另外需要多说一句，使用之前先看到自己的基础规则都支持啥，配置文件就是为了可以更多的自定义而已，不要一股脑的弄上去，弄坏了也不知道咋回事，多测试测试

---

### 使用方法

1. clone 或 下载可执行文件（后续提供）
2. 把 `.config.yaml` 改名为 `config.yaml` 在这里面配置你自己的信息。最关键的节点是 `pull-proxy-source` 这里面配置的就是你的服务 `订阅链接`。其他的配置其实可以不用改，如果要更改就做好详尽的测试，里面的每个节点在目前支持的基础规则我都保证测试可用，如果你用不了，那就自己好好查查。另外一个节点是 `Proxy` 这里面可以配置你自己搭建的，或者没有配置文件的节点。配置文件里面的内容最终都会合并到配置文件里面去。
3. 如果是 `clone` 下来的项目就在配置好 `go` 的环境以后，执行 `go run main.go BaseRuleName` 就可以了。（注意，如果报错了第一反应就是检查网络，别是网络不通。）`BaseRuleName` 这个名字就是在配置文件中 `base-rule` 节点下的 `name`，这个参数是可选的，如果不传入就会采用`base-rule` 节点下的第一个作为基础配置库。如果是下载的可执行文件，就在命令行下运行可执行文件 + 参数就ok了。
4. 不出意外，已经在你的运行目录下有了跟 你选择的配置文件中 `base-rule` 节点下的 `name` 同名的配置文件生成了。

---

### 特别说明

这一切都是在满足我的需求为第一前提下弄的，如果能够对你也有用，我深感荣幸。如果你想使用但是遇到了问题，请去提 `issue` 我会在我所知的情况下尽可能的回答。

配置文件中的 `base-rule` 节点不要修改，因为你改了代码也不支持，写到配置文件中，仅仅是为了防止他们的地址变动我不用再次编译了而已。 

---

### 鸣谢

- [Hackl0us](https://github.com/Hackl0us)
- [ConnersHua](https://github.com/ConnersHua)
- [lhie1](https://github.com/lhie1)

