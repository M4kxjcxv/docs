---
title: ワークフローをキャンセルする
intro: '進行中のワークフロー実行をキャンセルできます。 ワークフロー実行をキャンセルすると、{% data variables.product.prodname_dotcom %} はそのワークフローの一部であるすべてのジョブとステップをキャンセルします。'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
ms.openlocfilehash: f8bf0d06f5e0e37cb120b22a3bd6da39b51b78a9
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2022
ms.locfileid: '145088560'
---
{% data reusables.actions.enterprise-beta %} {% data reusables.actions.enterprise-github-hosted-runners %}

{% data reusables.repositories.permissions-statement-write %}

## ワークフローの実行をキャンセルする

{% data reusables.repositories.navigate-to-repo %} {% data reusables.repositories.actions-tab %} {% data reusables.repositories.navigate-to-workflow %}
1. ワークフロー実行一覧から、キャンセルする `queued` または `in progress` 実行の名前をクリックします。
![ワークフロー実行の名前](/assets/images/help/repository/in-progress-run.png)
1. ワークフローの右上にある **[Cancel workflow]\(ワークフローのキャンセル\)** をクリックします。
![チェック スイートのキャンセル ボタン](/assets/images/help/repository/cancel-check-suite-updated.png)

## ワークフロー実行をキャンセルするために {% data variables.product.prodname_dotcom %} が実行するステップ

ワークフローの実行をキャンセルする場合、ワークフローの実行に関連するリソースを使用する他のソフトウェアを実行している可能性があります。 ワークフロー実行に関連するリソースを解放するため、{% data variables.product.prodname_dotcom %} がワークフロー実行をキャンセルする際のステップを知っておくと役立つ場合があります。

1. ワークフロー実行をキャンセルするために、サーバーは現在実行中のすべてのジョブに対して `if` 条件を再評価します。 条件が `true` に評価された場合、ジョブはキャンセルされません。 たとえば、`if: always()` は true に評価され、ジョブの実行は継続されます。 条件がない場合は条件 `if: success()` と同じなので、前のステップが正常に終了した場合にのみ実行されます。
2. キャンセルする必要があるジョブについては、サーバーは、キャンセルする必要があるジョブを持つすべてのランナー マシンにキャンセル メッセージを送信します。
3. 実行を継続するジョブの場合、サーバーは未完了のステップの `if` 条件を再評価します。 条件が `true` に評価された場合、ステップは引き続き実行されます。
4. キャンセルする必要があるステップの場合、ランナー マシンはステップのエントリ プロセス (javascript アクションの場合は `node`、コンテナー アクションの場合は `docker`、ステップで `run` を使っている場合は `bash/cmd/pwd`) に `SIGINT/Ctrl-C` を送信します。 プロセスが 7500 ms 以内に終了しない場合、ランナーは `SIGTERM/Ctrl-Break` をプロセスに送信し、プロセスが終了するまで2500 ms 待ちます。 プロセスがそれでも実行中のままなら、ランナーはプロセスツリーを強制終了します。
5. 5 分間のキャンセル タイムアウト期間が経過すると、サーバーは、実行を完了しないか、キャンセルプロセスを完了できなかったすべてのジョブとステップを強制的に終了します。
