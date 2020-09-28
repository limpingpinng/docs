---
title: Management Console にアクセスする
intro: '{{ site.data.variables.product.product_location }}のセットアップと設定、メンテナンスウィンドウのスケジューリング、問題のトラブルシューティング、ライセンスの管理には{{ site.data.variables.enterprise.management_console }}を使ってください。'
redirect_from:
  - /enterprise/admin/articles/about-the-management-console/
  - /enterprise/admin/articles/management-console-for-emergency-recovery/
  - /enterprise/admin/articles/web-based-management-console/
  - /enterprise/admin/categories/management-console/
  - /enterprise/admin/articles/accessing-the-management-console/
  - /enterprise/admin/guides/installation/web-based-management-console/
  - /enterprise/admin/installation/accessing-the-management-console
  - /enterprise/admin/configuration/accessing-the-management-console
versions:
  enterprise-server: '*'
---

### {{ site.data.variables.enterprise.management_console }}について

次の基本的な管理作業には {{ site.data.variables.enterprise.management_console }} を使用します。
- **初期セットアップ**: ブラウザで {{ site.data.variables.product.product_location_enterprise }} の IP アドレスにアクセスすることで {{ site.data.variables.product.product_location_enterprise }} を最初に起動したときに、初期セットアッププロセスを段階的に実行します。
- **インスタンスの基本設定**: [Settings] ページで、DNS、ホスト名、SSL、ユーザ認証、メール、モニタリングサービス、ログの転送を設定します。
- **スケジュールメンテナンスウィンドウ**: {{ site.data.variables.enterprise.management_console }} または管理シェルを使用してメンテナンスを実行する際に、{{ site.data.variables.product.product_location_enterprise }} をオフラインにします。
- **トラブルシューティング**: Support Bundle を生成するか、高レベルの診断情報を一覧表示します。
- **ライセンス管理**: {{ site.data.variables.product.prodname_enterprise }} ライセンスを一覧表示または更新します。

{{ site.data.variables.enterprise.management_console }}には、{{ site.data.variables.product.product_location_enterprise }}のIPアドレスからいつでもアクセスできます。インスタンスがメンテナンスモードになっていたり、致命的なアプリケーション障害やホスト名あるいはSSLの設定ミスがあってもアクセス可能です。

{{ site.data.variables.enterprise.management_console }}にアクセスするには、{{ site.data.variables.product.product_location_enterprise }}の初期セットアップ時に設定した管理者パスワードを使わなければなりません。 また、ポート8443で仮想マシンのホストに接続することもできます。 {{ site.data.variables.enterprise.management_console }}へのアクセスに問題があれば、中間のファイアウォールやセキュリティグループの設定を確認してください。

### サイト管理者としての{{ site.data.variables.enterprise.management_console }}へのアクセス

サイト管理者として初めて {{ site.data.variables.enterprise.management_console }} にアクセスするときは、アプリに認証するために {{ site.data.variables.product.prodname_enterprise }} ライセンスファイルをアップロードする必要があります。 詳しい情報については、「[{{ site.data.variables.product.prodname_enterprise}}ライセンスを管理する](/enterprise/{{ currentVersion }}/admin/guides/installation/managing-your-github-enterprise-license)」を参照してください。

{{ site.data.reusables.enterprise_site_admin_settings.access-settings }}
{{ site.data.reusables.enterprise_site_admin_settings.management-console }}
{{ site.data.reusables.enterprise_management_console.type-management-console-password }}

### 認証されていないユーザとしての{{ site.data.variables.enterprise.management_console }}へのアクセス

1. ブラウザで次の URL にアクセスします。`hostname` は実際の {{ site.data.variables.product.prodname_ghe_server }} ホスト名または IP アドレスに置き換えてください:
  ```shell
  http(s)://HOSTNAME/setup
  ```
{{ site.data.reusables.enterprise_management_console.type-management-console-password }}

### ログイン試行の失敗後の{{ site.data.variables.enterprise.management_console }}のアンロック

10 分以内にログインに 10 回失敗すると、{{ site.data.variables.enterprise.management_console }} はロックされます。 ログインを再度試みるには、ログイン画面が自動的にロック解除されるまで待つ必要があります。 直前の 10 分間に失敗したログイン試行が 10 回未満となると同時に、ログイン画面は自動的にロックが解除されます。 ログインが成功すると、カウンタはリセットされます。

{{ site.data.variables.enterprise.management_console }} をただちにロック解除するには、管理シェルから `ghe-reactivate-admin-login` コマンドを使用します。 詳細は「[コマンドラインユーティリティ](/enterprise/{{ currentVersion }}/admin/guides/installation/command-line-utilities#ghe-reactivate-admin-login)」および「[管理シェル (SSH) にアクセスする](/enterprise/{{ currentVersion }}/admin/guides/installation/accessing-the-administrative-shell-ssh/)」を参照してください。