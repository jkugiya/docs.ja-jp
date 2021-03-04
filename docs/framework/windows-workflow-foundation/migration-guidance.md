---
title: 移行のガイドライン
description: '詳細情報: 移行ガイダンス'
ms.date: 03/30/2017
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
ms.openlocfilehash: 83c6af4d8eed396501aafc568de8e64d30ae7cfe
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104862"
---
# <a name="migration-guidance"></a>移行ガイダンス

.NET Framework 4 では、Microsoft は Windows Workflow Foundation (WF) の2番目のメジャーバージョンをリリースしました。 [!INCLUDE[wf1](../../../includes/wf1-md.md)] は WinFX でリリースされました (これには WF3 の型が含まれるようになり、現在はと呼ばれるようになりました \* )。また .NET Framework 3.5 でも強化されました。 WF3 も .NET Framework 4 に含まれていますが、新しいワークフローテクノロジ (WF4 と呼ばれる型) と共に存在し \* ます。 WF4 の導入時期を検討する場合は、最初にそのタイミングの管理を認識することが重要です。

- WF3 は .NET Framework 4 の完全にサポートされている部分です。

- WF3 アプリケーションは、変更せずに .NET Framework 4 で実行され、引き続き完全にサポートされます。

- 新しい WF3 アプリケーションを作成し、既存のアプリケーションを Visual Studio 2012 で編集し、完全にサポートすることができます。

したがって、WF4 (WF3) から () に移動するかどうかは、.NET Framework 4 を採用するかどうかの決定から分離され \* \* ます。 このトピックでは、WF の移行のガイドラインへのリンクを提供し、WF3 および WF4 での作業に関する情報を提供します。

## <a name="wf-migration-white-papers-and-cookbooks"></a>WF の移行に関するホワイトペーパーと料理

 [WF の移行の概要](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Overview.docx)\
 WF3 と WF4 の関係、および .NET Framework 4 のワークフローテクノロジのユーザーまたは潜在的なユーザーとしての選択肢について説明します。

 [WF の移行: WF3 開発のベストプラクティス](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Best%20Practices.docx)\
 より簡単に WF4 に移行できるように、WF3 の成果物を設計する方法について説明します。

 [WF のガイダンス: ルール](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20Rules%20Guidance.docx)\
 .NET Framework 4 つのソリューションにルール関連の投資を進める方法について説明します。

 [WF のガイダンス: ステートマシン](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20State%20Machine%20Guidance.doc) State-Machine アクティビティが存在しない場合の WF4 制御フローのモデリングについて説明します。 このガイダンスは .NET Framework 4 を対象とするワークフロープロジェクトにのみ適用されます。 ステートマシンのワークフローは、Platform Update 1 のリリースで .NET Framework 4.0.1 に追加され、.NET Framework 4.5 の一部として含まれていました。 .NET Framework 4.0.1-4.0.3 と .NET Framework 4.5 のステートマシンワークフローの詳細については、「 [Update 4.0.1 for Microsoft .NET Framework 4 Features](/previous-versions/dotnet/netframework-4.0/hh290669(v=vs.100)) And [state machine ワークフロー](state-machine-workflows.md)」を参照してください。

 [WF の移行のクックブック: カスタムアクティビティ](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Custom%20Activities.docx)\
 WF3 のカスタム アクティビティを WF4 で再設計する場合のサンプルと手順について説明します。

 [WF の移行のクックブック: 高度なカスタムアクティビティ](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Advanced%20Custom%20Activities.docx)\
 WF3 キューを使用して子アクティビティを WF4 カスタム アクティビティとしてスケジュールする高度な WF3 カスタム アクティビティを再設計するための指針を示します。
%20 [WF 移行クックブック: ワークフロー](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflows.docx)\
 WF3 のワークフローを WF4 で再設計する場合のサンプルと手順について説明します。

 [WF の移行のクックブック: ワークフローホスティング](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflow%20Hosting.docx)\
 WF3 ホスティング コードを WF4 ホスティング コードとして再設計するための指針を示します。 この目的は、WF3 と WF4 のワークフロー ホスティングの主な違いを説明することです。

 [WF の移行のクックブック: ワークフロー追跡](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF%20Migration%20Cookbook%20Workflow%20Tracking.docx)\
 WF3 追跡コードを再設計するための指針と、同等の WF4 追跡コードと構成を使用した構成を示します。

 [WF のガイダンス: ワークフローサービス](https://download.microsoft.com/download/5/9/9/599CF8A9-5FE2-426A-A536-A83F84D38BF9/WF4%20Workflow%20Services%20Guidance.docx)\
 事前定義アクティビティの一般的なシナリオ向けに、WF3 で作成した Windows Communication Foundation (WCF) Web サービス (一般にワークフロー サービスと呼ばれます) を実装するワークフローを WF4 を使用するように再設計するための詳細な手順を例を中心として示します。

## <a name="see-also"></a>関連項目

- <xref:System.Activities.Statements.Interop>
