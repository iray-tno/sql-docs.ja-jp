---
title: Linux 上の SQL Server 2017 のリリース ノート |Microsoft ドキュメント
description: ここでは、リリース ノートが含まれていて、Linux で実行されている SQL Server 2017 の機能をサポートします。 リリース ノートは、最新のリリースから以前のリリースをいくつか含まれます。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/24/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 07782a5b8290b41a5a11557c503fcbfd0736790b
ms.sourcegitcommit: a9da0abd3e17fbcd6339980d7331d0418cdada53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2018
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 のリリース ノート

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

次のリリース ノートは、Linux で実行されている SQL Server 2017 に適用されます。 この記事は、各リリースについてのセクションに分割されます。 GA リリースがサポートの詳細し、既知の問題が一覧表示します。 各累積更新プログラム (CU) リリースでは、CU 変更に加え、パッケージのダウンロード、Linux へのリンクを説明するサポートの記事にリンクがあります。

## <a name="supported-platforms"></a>サポートされているプラットフォーム

| プラットフォーム | [ファイル システム] | インストール ガイド |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3 または 7.4 ワークステーション、サーバー、およびデスクトップ | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS または EXT4 | [インストール ガイド](quickstart-install-connect-ubuntu.md) | 
| 1.8 以降、Mac、または Linux の Windows で docker エンジン | なし | [インストール ガイド](quickstart-install-connect-docker.md) | 

> [!TIP]
> 詳細については、確認、[システム要件](sql-server-linux-setup.md#system)Linux に SQL Server 用です。 SQL Server 2017 の最新のサポート ポリシーで、次を参照してください。、 [for Microsoft SQL Server の技術的なサポート ポリシー](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)です。

## <a name="tools"></a>ツール

SQL Server を対象とするほとんどの既存クライアント ツールは、Linux で実行されている SQL Server を対象にシームレスにできます。 一部のツールは、Linux で適切に動作するための特定のバージョン要件があります。 SQL Server ツールの一覧については、次を参照してください。 [SQL ツール、および SQL Server ユーティリティ](../tools/overview-sql-tools.md)です。

## <a name="release-history"></a>リリース履歴

次の表は、SQL Server 2017 のリリース履歴を示します。

| リリース | バージョン | リリース日 |
|-----|-----|-----|
| [CU7](#CU7) | 14.0.3026.27 | 5 2018 |
| [CU6](#CU6) | 14.0.3025.34 | 4 2018 |
| [CU5](#CU5) | 14.0.3023.8 | 3 2018 |
| [CU4](#CU4) | 14.0.3022.28 | 2 2018 |
| [CU3](#CU3) | 14.0.3015.40 | 1-2018 |
| [CU2](#CU2) | 14.0.3008.27 | 11-2017 |
| [CU1](#CU1) | 14.0.3006.16 | 10-2017 |
| [GA](#GA) | 14.0.1000.169 | 10-2017 |

## <a id="cuinstall"></a> 累積的更新プログラムをインストールする方法

構成した場合、累積的な更新リポジトリ、新規インストールを実行するときに SQL Server パッケージの最新の累積的な更新が発生します。 累積的な更新プログラムのリポジトリは、Linux 上の SQL Server のすべてのパッケージのインストールのアーティクルの既定値です。 リポジトリの構成の詳細については、次を参照してください。 [Linux に SQL Server 用のリポジトリを構成する](sql-server-linux-change-repo.md)です。

SQL Server の既存のパッケージを更新する場合は、最新の累積的な更新プログラムを取得するには、各パッケージの適切な更新プログラムのコマンドを実行します。 各パッケージの特定の更新手順については、次のインストール ガイドを参照してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md#upgrade)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)
- [SQL Server エージェントを有効にします。](sql-server-linux-setup-sql-agent.md)

## <a id="CU7"></a> CU7 (月 2018)

これは、SQL Server 2017 の累積的な更新プログラム 7 (CU7) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3026.27 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/en-us/help/4229789](https://support.microsoft.com/en-us/help/4229789)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3026.27-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3026.27-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3026.27-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (年 2018年 4 月)

これは、SQL Server 2017 の累積的な更新プログラム 6 (CU6) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3025.34 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/help/4101464](https://support.microsoft.com/help/4101464)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3025.34-3 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3025.34-3 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3025.34-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (年 2018年 3 月)

これは、SQL Server 2017 の累積的な更新プログラム 5 (CU5) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3023.8 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/help/4092643](https://support.microsoft.com/help/4092643)です。

### <a name="known-upgrade-issue"></a>アップグレードの既知の問題

CU5 に以前のリリースからアップグレードするときに SQL Server が次のエラーで起動に失敗します。

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

このエラーを解決するには、SQL Server エージェントを有効にし、次のコマンドで SQL Server を再起動します。

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3023.8-5 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3023.8-5 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3023.8-5 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> CU4 (February 2018)

これは、SQL Server 2017 の Cumulative Update 4 (CU4) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3022.28 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/en-us/help/4056498](https://support.microsoft.com/en-us/help/4056498)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

> [!NOTE]
> CU4、時点で別のパッケージとして、SQL Server エージェントはインストールされません。 エンジンはパッケージと共にインストールし、使用を有効にする必要があります。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3022.28-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3022.28-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3022.28-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU3"></a> CU3 (年 2018年 1 月)

これは、SQL Server 2017 の累積更新プログラム 3 (CU3) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3015.40 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/en-us/help/4052987](https://support.microsoft.com/en-us/help/4052987)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3015.40-1 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3015.40-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3015.40-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (2017 年 11 月)

これは、SQL Server 2017 の Cumulative Update 2 (CU2) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3008.27 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/help/4052574](https://support.microsoft.com/help/4052574)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3008.27-1 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3008.27-1 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3008.27-1 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (2017 年 10 月)

これは、SQL Server 2017 の Cumulative Update 1 (CU1) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.3006.16 です。 修正プログラムとこのリリースの機能強化については、次を参照してください。 [ https://support.microsoft.com/help/KB4053439](https://support.microsoft.com/help/4038634)です。

### <a name="package-details"></a>パッケージの詳細

手動またはオフラインのパッケージのインストールで、次の表の情報とパッケージの RPM と Debian パッケージをダウンロードできます。

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.3006.16-3 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.3006.16-3 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.3006.16-3 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> GA (2017 年 10 月)

これは、SQL Server 2017 の一般公開 (GA) リリースです。 このリリースの SQL Server エンジンのバージョンは、14.0.1000.169 です。

### <a name="package-details"></a>パッケージの詳細

パッケージの詳細と、RPM パッケージと Debian パッケージのダウンロード場所は、次の表に一覧表示されます。 次のインストール ガイドの手順を使用する場合に、これらのパッケージを直接ダウンロードする必要はありませんに注意してください。

- [SQL Server パッケージをインストールします。](sql-server-linux-setup.md)
- [フルテキスト検索のパッケージをインストールします。](sql-server-linux-setup-full-text-search.md)
- [SQL Server エージェント パッケージをインストールします。](sql-server-linux-setup-sql-agent.md)
- [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)

| [パッケージ] | パッケージ バージョン | ダウンロード |
|-----|-----|-----|
| Red Hat RPM パッケージ | 14.0.1000.169-2 | [エンジンは RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM パッケージ | 14.0.1000.169-2 | [mssql server エンジン RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[フルテキスト検索の 15,000 RPM パッケージ](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server エージェント RPM パッケージ](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian パッケージ | 14.0.1000.169-2 | [エンジン Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[高可用性 Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[フルテキスト検索の Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[SQL Server エージェントの Debian パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS パッケージ](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> サポートされていない機能とサービス

次の機能とサービスは GA リリースの時点では Linux で使用できません。 時間の経過と共に、これらの機能のサポートをしだいに有効なります。

| 領域 | サポートされていない機能またはサービス |
|-----|-----|
| **データベース エンジン** | トランザクション レプリケーション |
| &nbsp; | マージ レプリケーション |
| &nbsp; | Stretch DB |
| &nbsp; | PolyBase |
| &nbsp; | サード パーティ製の接続で分散クエリ |
| &nbsp; | システム拡張ストアド プロシージャ (XP_CMDSHELL など) |
| &nbsp; | Filetable は、FILESTREAM |
| &nbsp; | CLR アセンブリと EXTERNAL_ACCESS または UNSAFE 権限の設定します。 |
| &nbsp; | バッファー プール拡張 |
| **SQL Server エージェント** |  サブシステム: CmdExec、PowerShell、キュー リーダーは、SSIS、SSAS、SSRS |
| &nbsp; | 警告 |
| &nbsp; | ログ リーダー エージェント (Log Reader Agent) |
| &nbsp; | 変更データ キャプチャ |
| &nbsp; | 管理対象のバックアップ |
| **高可用性** | データベース ミラーリング  |
| **セキュリティ** | 拡張キー管理 |
| &nbsp; | リンク サーバーの AD の認証 | 
| &nbsp; | 可用性グループ (Ag) に対して AD の認証 | 
| &nbsp; | サード パーティ AD ツール (Centrify、いる Vintela、Powerbroker) | 
| **Services** | SQL Server Browser |
| &nbsp; | SQL Server R services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | [データベース エンジン サービス] |
| &nbsp; | マスター データ サービス |
| &nbsp; | 分散トランザクション コーディネーター (DTC) |

## <a name="known-issues"></a>既知の問題

以降のセクションでは、Linux 上の SQL Server 2017 の一般公開 (GA) リリースの既知の問題を記述します。

#### <a name="general"></a>全般

- SQL Server 2017 の GA リリースにアップグレードするには、CTP 2.1 からのみまたはそれ以降はサポートされてます。 

- SQL Server が 15 文字である要件がインストールされている以下のホスト名の長さ。 

    - **解像度**: 何か 15 文字以下にホスト名などの名前を変更します。

- システム時刻を時刻で旧バージョンと手動で設定を SQL Server を SQL Server の内部のシステム時刻が更新を停止するとなります。

    - **解像度**: SQL Server を再起動します。

- 1 つのインスタンスのインストールのみがサポートされています。

    - **解像度**: 指定されたホスト上で複数のインスタンスがある場合は、Vm の使用を検討または Docker コンテナーです。 

- SQL Server 構成マネージャーは、Linux 上の SQL Server に接続できません。

- 既定の言語、 **sa**ログインは英語です。

    - **解像度**: の言語を変更、 **sa**を使用してログイン、 **ALTER LOGIN**ステートメントです。

#### <a name="databases"></a>データベース

- Mssql conf ユーティリティでは、master データベースを移動できません。 Mssql 構成とその他のシステム データベースを移動することができます。

- SQL Server on Windows でバックアップされたデータベースを復元するときに行う必要があります、 **WITH MOVE** TRANSACT-SQL ステートメントの句。

- Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされていません。 DTC が含まれる場合を除き、リンク サーバーがサポートされる SQL Server を SQL Server。 詳細については、次を参照してください。 [Linux で実行されている SQL Server では、Microsoft 分散トランザクション コーディネーター サービスを必要とする分散トランザクションはサポートされません](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/)です。

- 特定のアルゴリズム (暗号スイート) トランスポート層セキュリティ (TLS) は、Linux に SQL Server では正しく機能しません。 これは、結果、SQL Server に接続するときに問題と同様に高可用性グループ レプリカ間の接続を確立する接続が失敗します。

   - **解像度**: 変更、 **mssql.conf**構成スクリプトを SQL Server on Linux は、次の手順を実行して問題のある暗号スイートを無効にします。

      1. 次の/var/opt/mssql/mssql.conf に追加します。

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. 次のコマンドでは、SQL Server を再起動します。

      ```bash
      sudo systemctl restart mssql-server
      ```

- インメモリ OLTP を使用して Windows 上の SQL Server 2014 データベースは、Linux 上の SQL Server 2017 に復元することはできません。 インメモリ OLTP を使用する SQL Server 2014 データベースを復元するに最初にデータベースをアップグレードを SQL Server 2016 または Windows 上の SQL Server 2017 移動の前に SQL server on Linux のバックアップ/復元またはデタッチとアタッチを使用して。

- ユーザーのアクセス許可**ADMINISTER BULK OPERATIONS**この時点で Linux でサポートされていません。

#### <a name="networking"></a>ネットワーク

次の両方の条件が満たされた場合、リンク サーバーまたは可用性グループなど、sqlservr プロセスからの発信 TCP 接続が関係する機能は機能しません可能性があります。

1. 対象サーバーは、ホスト名と IP アドレスではなくとして指定されます。

1. ソース インスタンスには、カーネルで無効になっている IPv6 があります。 かどうか、システムはをカーネル内で有効になっている IPv6 ことを確認するには、次のすべてのテストに合格する必要があります。

   - `cat /proc/cmdline` 現在のカーネルのブート cmdline が印刷されます。 出力にはする必要がありますが含まれていない`ipv6.disable=1`です。
   - Proc/sys/net ipv6/ディレクトリが存在する必要があります。
   - C プログラムを呼び出す`socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)`成功すべき - syscall、fd を返す必要があります! =-1 と EAFNOSUPPORT で異常終了しません。

正確なエラーは、この機能によって異なります。 リンク サーバーでは、ログイン タイムアウト エラーとして明らかにします。 可用性グループの場合、`ALTER AVAILABILITY GROUP JOIN`ダウンロード構成タイムアウト エラーで 5 分後に、セカンダリで DDL は失敗します。

この問題を回避するには、次のいずれかの操作を行います。

1. ホスト名ではなく ip アドレスを使用すると、TCP 接続のターゲットを指定します。

1. 削除することで、カーネルで IPv6 を有効にする`ipv6.disable=1`ブート cmdline からです。 これを行う方法は、Linux ディストリビューションとブートローダー、grub などによって異なります。 IPv6 を無効にする場合、ことができますも無効にする設定して`net.ipv6.conf.all.disable_ipv6 = 1`で、`sysctl`構成 (たとえば`/etc/sysctl.conf`)。 これもこのメッセージは、システムのネットワーク アダプターが、IPv6 アドレスを取得しないようにするが、sqlservr 機能が動作しましょう。

#### <a name="network-file-system-nfs"></a>Network File System (NFS)
使用する場合**Network File System (NFS)** 、実稼働環境でのリモートの共有は、次のサポート要件を注意してください。

- 使用して NFS version **4.2 以上**です。 NFS の古いバージョンでは、スパース ファイルの作成、最新のファイル システムに共通 fallocate など、必要な機能はできません。
- のみを検索、 **/var/opt/mssql** NFS マウント上のディレクトリ。 SQL Server システム バイナリなどその他のファイルはサポートされていません。
- NFS クライアントが、そのリモート共有をマウントするときに、'nolock' オプションを使用することを確認します。

#### <a name="localization"></a>ローカライズ

- ロケールが英語 (en_us) のセットアップ中にでない場合は、bash セッションとターミナルで utf-8 のエンコードを使用する必要があります。 ASCII エンコーディングを使用する場合は、次のようなエラーを参照してください可能性があります。

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   Utf-8 エンコードを使用できない場合は、MSSQL_LCID 環境変数を使用して、選択された言語を指定するセットアップを実行します。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- ときに mssql conf セットアップを実行して、拡張文字が、不適切な SQL Server の英語以外のインストールを実行するは、[SQL Server の構成]、ローカライズされたテキストの後に表示されます。 ラテン文字以外のベース インストールの場合、文が見つからないこと、または、完全にします。 不足している文は、次のローカライズされた文字列を表示する必要があります:"ライセンスの PID が正常に処理します。  新しいエディションは、[\<名前\>edition]"です。 情報用にのみ、この文字列を出力し、すべての言語に対処する次の SQL Server の累積的な更新します。 これは、任意の方法で SQL Server が正常にインストールには影響ありません。 

#### <a name="full-text-search"></a>フルテキスト検索

- すべてのフィルターは、Office ドキュメントのフィルターを含め、このリリースで使用できます。 サポートされているフィルターの一覧は、次を参照してください。 [Linux に SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md#filters)です。

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- **Mssql サーバーが**パッケージがこのリリースで SUSE でサポートされていません。 Ubuntu と Red Hat Enterprise Linux (RHEL) でサポートされています。

- Linux CTP 2.1 の更新以降、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 この機能は、SQL Server および MySQL の ODBC ドライバーでテスト済みですはまた、ODBC 仕様に従うすべての Unicode ODBC ドライバーを使用する必要があります。 、デザイン時に、ODBC データに接続する DSN または接続文字列を指定できますWindows 認証を使用することもできます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

- Linux で SSIS パッケージを実行すると、このリリースでは、次の機能はサポートされていません。
  - SSIS カタログ データベース
  - SQL エージェントがスケジュールされているパッケージの実行
  - [Windows 認証]
  - サード パーティのコンポーネント
  - 変更データ キャプチャ (CDC)
  - SSIS のスケール アウト
  - SSIS 用 azure Feature Pack
  - Hadoop と HDFS のサポート
  - Microsoft Connector for SAP BW

現在サポートされていない、または制限付きサポートされている組み込みの SSIS コンポーネントの一覧は、次を参照してください。[制限事項と既知の問題 Linux 上の SSIS](sql-server-linux-ssis-known-issues.md#components)です。

Linux 上の SSIS の詳細については、次の記事を参照してください。
-   [Linux の SSIS サポート ブログの投稿 announcing](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)です。
-   [Linux 上の SQL Server Integration Services (SSIS) のインストールします。](sql-server-linux-setup-ssis.md)
-   [抽出、変換、および SSIS Linux でのデータを読み込む](sql-server-linux-migrate-ssis.md)

#### <a name="-a-idssmsa-sql-server-management-studio-ssms"></a><、id ="ssms"></a> SQL Server Management Studio (SSMS)

次の制限事項は、Linux 上の SQL Server に接続されている Windows の SSMS に適用されます。

- メンテナンス プランはサポートされていません。

- 管理データ ウェアハウス (MDW) と SSMS で、データ コレクターはサポートされていません。 

- Windows 認証または Windows イベント ログのオプションを持つ SSMS UI コンポーネントは、Linux では機能しません。 SQL ログインなど、他のオプションと、これらの機能を引き続き使用できます。 

- 保持するログ ファイルの数を変更できません。

## <a name="next-steps"></a>次の手順

開始するには、次のクイック スタートを参照してください。

- [Red Hat Enterprise Linux にインストールします。](quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server にインストールします](quickstart-install-connect-suse.md)
- [Ubuntu にインストールします](quickstart-install-connect-ubuntu.md)
- [Docker で実行します。](quickstart-install-connect-ubuntu.md)
- [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)
- [実行と接続 - クラウド](quickstart-install-connect-clouds.md)

よく寄せられる質問に対する回答については、次を参照してください。、 [SQL Server on Linux に関する FAQ](sql-server-linux-faq.md)です。
