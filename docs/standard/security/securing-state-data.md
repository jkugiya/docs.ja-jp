---
title: 状態データの保護
description: 状態データをプライベート変数または内部変数として宣言して、そのデータへのアクセスを制限します。 そのようなデータにも、リフレクション、シリアル化、デバッグでは引き続きアクセスできます。
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: 849ed993befaceda1b04becbb7fb2530c5c62a77
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824162"
---
# <a name="securing-state-data"></a>状態データの保護

機密データの処理または任意の種類のセキュリティ決定を行うアプリケーションは、そのデータを自らの制御下に置き、潜在的に悪意がある他のコードがそのデータに直接アクセスできないようにします。 メモリ内でデータを保護する最善の方法は、そのデータをプライベート変数または内部変数 (同じアセンブリにスコープが限定されている) として宣言することです。 ただし、このようなデータでさえも、次のように注意が必要なアクセスの対象となります。  
  
- リフレクション メカニズムを使用すると、オブジェクトを参照できる信頼性の高いコードはプライベート メンバーを取得および設定できます。  
  
- シリアル化を使用すると、信頼性の高いコードがプライベート メンバーを効率よく取得および設定できます (シリアル化された形式のオブジェクトにおいて対応するデータにアクセスできる場合)。  
  
- デバッギング中にはこのデータを読み取ることができます。  
  
 自分のメソッドやプロパティがこれらの値を意図せずに公開することのないようにしてください。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](secure-coding-guidelines.md)
- [ASP.NET Core のセキュリティ](/aspnet/core/security/)
