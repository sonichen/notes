## **敏感信息泄露扫描工具**

sensleak 0.1.0是在我在参考gitleaks功能特点的基础上，用rust编写的敏感信息扫描工具，用于扫描Git仓库中的敏感数据，特别是针对嵌入在代码中的密码、API密钥、证书和私钥等敏感信息。基于命令行进行交互，提供REST API。

GitHub链接：

sensleak 0.1.0: https://github.com/sonichen/sensleak-rs 

sensleak最新版本: https://github.com/open-rust-initiative/sensleak-rs

## **背景** 

许多开发人员将敏感信息（如密钥和证书）存储在其代码中，这会带来安全风险。因此，有商业服务（如GitGuardian扫描GitHub和GitLab）以及开源组件（如truffleHog和Gitleaks）提供类似的功能。

## **特点**

1. 增强安全性：使用Rust开发工具，以确保改进的安全性和内存安全性。
2. 命令行界面：创建一个用户友好的命令行工具，生成综合的测试报告。
3. 带访问控制的REST API：使工具能够作为服务运行，并通过REST API提供访问控制，使用Swagger生成API文档。
4. 并发扫描：利用线程池控制敏感信息并发扫描，从而提高整体效率。
5. 批处理处理：实现文件的批处理处理，进一步优化扫描过程，提高效率。

## **技术**

- 开发语言：Rust
- 命令行交互：clap.rs
- Git仓库操作：git2
- Web框架：axum
- 自动生成的OpenAPI文档：utoipa

## **用法** 

## **命令行界面（CLI）用法** 

在命令行界面（CLI）中运行工具以执行敏感数据检查。

```
 
cargo run --bin scan -- -help
```

### **API文档** 

运行以下代码以查看项目文档。

```
 
cargo run --bin api
```

API文档位于http://localhost:7000/swagger-ui/#/

## **项目文档** 

运行以下代码以查看项目文档。

```
 cargo doc --document-private-items --open
```

## **配置** 

使用此项目中的gitleaks配置。不同之处在于，在此项目中，路径需要以“/”开头。

```
# Title for the gitleaks configuration file.
title = "Gitleaks title"

# Extend the base (this) configuration. When you extend a configuration
# the base rules take precedence over the extended rules. I.e., if there are
# duplicate rules in both the base configuration and the extended configuration
# the base rules will override the extended rules.
# Another thing to know with extending configurations is you can chain together
# multiple configuration files to a depth of 2. Allowlist arrays are appended
# and can contain duplicates.
# useDefault and path can NOT be used at the same time. Choose one.
[extend]
# useDefault will extend the base configuration with the default gitleaks config:
# https://github.com/zricethezav/gitleaks/blob/master/config/gitleaks.toml
useDefault = true
# or you can supply a path to a configuration. Path is relative to where gitleaks
# was invoked, not the location of the base config.
path = "common_config.toml"

# An array of tables that contain information that define instructions
# on how to detect secrets
[[rules]]

# Unique identifier for this rule
id = "awesome-rule-1"

# Short human readable description of the rule.
description = "awesome rule 1"

# Golang regular expression used to detect secrets. Note Golang's regex engine
# does not support lookaheads.
regex = '''one-go-style-regex-for-this-rule'''

# Golang regular expression used to match paths. This can be used as a standalone rule or it can be used
# in conjunction with a valid `regex` entry.
path = '''a-file-path-regex'''

# Array of strings used for metadata and reporting purposes.
tags = ["tag","another tag"]

# Int used to extract secret from regex match and used as the group that will have
# its entropy checked if `entropy` is set.
secretGroup = 3

# Float representing the minimum shannon entropy a regex group must have to be considered a secret.
entropy = 3.5

# Keywords are used for pre-regex check filtering. Rules that contain
# keywords will perform a quick string compare check to make sure the
# keyword(s) are in the content being scanned. Ideally these values should
# either be part of the idenitifer or unique strings specific to the rule's regex
# (introduced in v8.6.0)
keywords = [
  "auth",
  "password",
  "token",
]

# You can include an allowlist table for a single rule to reduce false positives or ignore commits
# with known/rotated secrets
[rules.allowlist]
description = "ignore commit A"
commits = [ "commit-A", "commit-B"]
paths = [
  '''\go\.mod''',
  '''\go\.sum'''
]
# note: (rule) regexTarget defaults to check the _Secret_ in the finding.
# if regexTarget is not specified then _Secret_ will be used.
# Acceptable values for regexTarget are "match" and "line"
regexTarget = "match"
regexes = [
  '''process''',
  '''getenv''',
]
# note: stopwords targets the extracted secret, not the entire regex match
# like 'regexes' does. (stopwords introduced in 8.8.0)
stopwords = [
  '''client''',
  '''endpoint''',
]


# This is a global allowlist which has a higher order of precedence than rule-specific allowlists.
# If a commit listed in the `commits` field below is encountered then that commit will be skipped and no
# secrets will be detected for said commit. The same logic applies for regexes and paths.
[allowlist]
description = "global allow list"
commits = [ "commit-A", "commit-B", "commit-C"]
paths = [
  '''gitleaks\.toml''',
  '''(.*?)(jpg|gif|doc)'''
]

# note: (global) regexTarget defaults to check the _Secret_ in the finding.
# if regexTarget is not specified then _Secret_ will be used.
# Acceptable values for regexTarget are "match" and "line"
regexTarget = "match"

regexes = [
  '''219-09-9999''',
  '''078-05-1120''',
  '''(9[0-9]{2}|666)-\d{2}-\d{4}''',
]
# note: stopwords targets the extracted secret, not the entire regex match
# like 'regexes' does. (stopwords introduced in 8.8.0)
stopwords = [
  '''client''',
  '''endpoint''',
]
```

