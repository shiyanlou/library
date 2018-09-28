# 实验楼教程库

## 说明

[实验楼教程库](https://www.shiyanlou.com/library/)收录优秀的开源技术教程，教程内容通过[实验楼教程库仓库](https://github.com/shiyanlou/library)下的 YAML 文件配置，并定期与原作者的教程仓库进行同步。

如果你发现任何优秀的技术教程希望[实验楼教程库](https://www.shiyanlou.com/library/)收录，请[提交 issue](https://github.com/shiyanlou/library/issues/new)，我们会对教程质量进行审核，然后会去向作者申请授权。

所有配置文件统一使用 [YAML](http://yaml.org/spec/1.2/spec.html) 格式。所有文件 **必须** 使用 UTF-8 编码。

## 目录结构

目录结构如下：

```bash
├── README.md
├── books
│   ├── README.md
│   ├── external-book1-meta.yaml
│   ├── internal-book1-meta.yaml
│   └── internal-book2-meta.yaml
├── index_config.yaml
└── internal
    ├── README.md
    ├── book1
    │   ├── README.md
    │   ├── SUMMARY.md
    │   ├── chapter1.md
    │   └── chapter2.md
    └── book2
        ├── README.md
        └── SUMMARY.md
```

核心目录（文件）如下：

* [index_config.yaml](./index_config.yaml) 教程库首页配置示例；
* `books` 目录包含所有技术教程配置文件，每个教程对应一个 YAML 配置文件；
* `internal` 目录包含所有没有 Github 仓库的技术教程的内容，这部分教程的作者没有为教程设定 Github 仓库，在获得作者授权后我们将内容拷贝到该目录下，由实验楼进行手动维护和更新同步；

## 教程配置文件与内容

每一个教程包含：

* 配置文件，位于[实验楼教程库仓库](https://github.com/shiyanlou/library)的 `books` 目录下；
* 内容目录，位于教程作者的仓库中，或者在[实验楼教程库仓库](https://github.com/shiyanlou/library)的 `internal` 目录下；

所有技术教程都必须包含配置文件，且必须位于 `books` 目录下。教程库在同步技术教程时，会先从 `books` 目录读取技术教程配置文件，然后再从相应的 Git 仓库中同步技术教程具体内容。

没有配置文件的教程将不会进行同步。

[教程示例配置](examples/books/internal-book1-meta.yaml)。

## 没有 Github 仓库的教程

如果原作者没有为教程创建 Github 仓库，同时授权给实验楼维护教程内容，我们将存储在 `internal` 目录中，`internal` 目录的每一个子目录对应一个教程。

其中内容目录结构示例如下：

```bash
├── README.md
├── SUMMARY.md
├── chapter1.md 
└── chapter2.md
```

其中几个比较关键的文件：

* [README.md](examples/internal/book1/README.md) 可以包含一些介绍信息；
* [SUMMARY.md](examples/internal/book1/SUMMARY.md) 指定了教程同步到系统时，应包含的内容章节信息，[示例](examples/internal/book1/SUMMARY.md)；

系统从 Github 同步技术教程时，将自动从 `SUMMARY.md` 文件中解析出所有的章节文件，并读取其内容存储到数据库中。同时由于需要在技术教程详情页面展示教程的所有目录，系统在读取章节内容时也会从总解析出 H2 和 H3 菜单（H1 菜单是章节名称）。

## License

[实验楼教程库](https://www.shiyanlou.com/library/)收录的所有教程，都遵循原作者为教程设定的 License，收录的技术教程我们将一一与原作者获取授权。

