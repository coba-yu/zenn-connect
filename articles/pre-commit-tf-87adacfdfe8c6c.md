---
title: "terraform fmtをpre-commitで自動化"
emoji: "⚡"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: [terraform]
published: true
---

## 前提

以下のようなrepository構成を想定しています.

```
.
├── src  # python code等
├── terraform  # terraform code
│   ├── main.tf
│   ├── resource.tf
│   └── ...
└── .pre-commit-config.yaml
```

## 手順

### Terraform CLIのインストール

https://developer.hashicorp.com/terraform/install 

### .pre-commit-config.yamlの作成

`entry` と `files` で指定している `terraform/` はterraformのコードがあるディレクトリに適宜修正してください.

```yaml
-   repo: local
    hooks:
    -   id: terraform-fmt
        name: terraform-fmt
        entry: terraform fmt terraform/
        language: system
        files: ^terraform/.*
```

### pre-commitのインストール

https://pre-commit.com/index.html#install

installできたら `pre-commit-config.yaml` があるディレクトリで以下を実行してください.

```shell
pre-commit install
```

### git commit

自動で修正されるようになりました.

```shell
git add terraform/
git commit -m "terraform fmt test"
```

git diffで修正内容を確認できます.

例:

```terraform
resource "google_project_iam_member" "gcp_iam_member" {
   for_each = toset(var.gcp_iam_roles)
-  project  =  var.google_project
+  project  = var.google_project
   role     = each.value
   member   = "serviceAccount:${data.google_service_account.test_sa.email}"
 }
```
