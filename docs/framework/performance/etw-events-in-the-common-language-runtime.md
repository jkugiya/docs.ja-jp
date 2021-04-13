---
title: 共通言語ランタイムの ETW イベント
description: 共通言語ランタイム (CLR) の Windows イベント トレーシング (ETW) イベントに関する概要とリンクをご覧ください。
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: 5bb9b6a2-7b57-4aea-8809-32b28bc73e88
ms.openlocfilehash: ab9cb7c53171ebf1dd0d48dec133464fe4042043
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263633"
---
# <a name="etw-events-in-the-common-language-runtime"></a>共通言語ランタイムの ETW イベント

共通言語ランタイム (CLR) は、さまざまなデバッグとプロファイリング イベントを通じて、有用な Windows イベント トレーシング (ETW) の診断情報を提供します。 CLR ETW イベントは、Windows ETW トレース システムを利用して、共通言語ランタイムによって提供される既存のプロファイリングとデバッグのサポートを拡張します。  
  
 ETW の詳細については、「[ETW によるデバッグとパフォーマンス チューニングの向上](/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)」の記事を参照してください。 Xperf に関する情報は、NTDebugging のブログ エントリ「[Windows Performance Toolkit - Xperf](/archive/blogs/ntdebugging/windows-performance-toolkit-xperf)」にあります。  
  
 イベント トピックに記載されているすべてのイベントには、.NET Framework 4 以降が必要です。 Windows Vista オペレーティング システムは、サポートされる最小のクライアントで、Windows Server 2008 は、サポートされる最小のサーバーです。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [.NET Framework のログ記録の制御](controlling-logging.md)  
 ETW イベントをキャプチャおよび表示するためのツールとコマンドについて説明します。  
  
 [CLR ETW プロバイダー](clr-etw-providers.md)  
 ランタイム プロバイダーとランダウン プロバイダーの情報、およびこれらを使用して ETW データを収集する方法を提供します。  
  
 [CLR ETW キーワードおよびレベル](clr-etw-keywords-and-levels.md)  
 イベントをカテゴリ別にフィルタ処理できるランタイム プロバイダーとランダウン プロバイダーのキーワードについて説明します。  
  
 [CLR ETW イベント](clr-etw-events.md)  
 CLR ETW イベント、キーワード、レベル、およびイベント データに関する詳細情報を提供します。  
  
## <a name="see-also"></a>関連項目

- [.NET Framework の ETW イベント](etw-events.md)
