# Solidoc：属于你自己的文档

Solidoc定义了一种文档的存储标准，它将富文本以[链接数据](https://en.wikipedia.org/wiki/Linked_data)格式存储在[Pod](https://solid.inrupt.com/how-it-works)中，并且允许用户自主对文档进行权限管理（使用[WAC](http://solid.github.io/web-access-control-spec/)作为访问控制协议），也可以授权Solidoc服务器进行更细粒度的权限管理（例如Block级别）。


## 词汇表

```
@prefix sdoc: <http://www.solidoc.net/ontologies#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
```

### 集合

| Ontology    |   Subclass Of  | Has Property | Brief |
| --------   | ----- | ----  | --- |
| sdoc:Workspace |    |        |对应于Pod上的一个[LDP Basic Container](https://www.w3.org/TR/ldp/#ldpbc)
| sdoc:Page          |     |   dct:title, sdoc:firstChild, dct:creator, dct:created, dct:modified   | 对应于Pod上的一个[RDF Source](https://www.w3.org/TR/ldp/#ldprs)
| sdoc:Block         |     |  sdoc:nextBlock, sdoc:content  | 类似于文档中的段落
| sdoc:Heading1   | sdoc:Block |  | 大标题 |
| sdoc:Heading2   | sdoc:Block |  | 中标题 |
| sdoc:Heading3   | sdoc:Block |  | 小标题 |
| sdoc:Paragraph  | sdoc:Block |  | 文本段落 |
| sdoc:NumberedList   | sdoc:Block | sdoc:firstChild  | 有序列表 |
| sdoc:BulletedList   | sdoc:Block | sdoc:firstChild  | 无序列表 |
| sdoc:CheckList   | sdoc:Block | sdoc:firstChild  | 清单项目 |

### 属性

| Ontology    |   Domain  | Range | Brief |
| --------   | ----- | ----  | --- |
| sdoc:firstChild  |    |        | |
| sdoc:nextBlock |     |     | |
| sdoc:content    |  sdoc:Block   |  rdfs:Literal  | Block的内容 |
| sdoc:checked    |  sdoc:CheckList   | xsd:boolean  | 清单项目是否完成 |

