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
# <a name="securing-state-data"></a><span data-ttu-id="bda36-104">状態データの保護</span><span class="sxs-lookup"><span data-stu-id="bda36-104">Securing State Data</span></span>

<span data-ttu-id="bda36-105">機密データの処理または任意の種類のセキュリティ決定を行うアプリケーションは、そのデータを自らの制御下に置き、潜在的に悪意がある他のコードがそのデータに直接アクセスできないようにします。</span><span class="sxs-lookup"><span data-stu-id="bda36-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="bda36-106">メモリ内でデータを保護する最善の方法は、そのデータをプライベート変数または内部変数 (同じアセンブリにスコープが限定されている) として宣言することです。</span><span class="sxs-lookup"><span data-stu-id="bda36-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="bda36-107">ただし、このようなデータでさえも、次のように注意が必要なアクセスの対象となります。</span><span class="sxs-lookup"><span data-stu-id="bda36-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="bda36-108">リフレクション メカニズムを使用すると、オブジェクトを参照できる信頼性の高いコードはプライベート メンバーを取得および設定できます。</span><span class="sxs-lookup"><span data-stu-id="bda36-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="bda36-109">シリアル化を使用すると、信頼性の高いコードがプライベート メンバーを効率よく取得および設定できます (シリアル化された形式のオブジェクトにおいて対応するデータにアクセスできる場合)。</span><span class="sxs-lookup"><span data-stu-id="bda36-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="bda36-110">デバッギング中にはこのデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="bda36-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="bda36-111">自分のメソッドやプロパティがこれらの値を意図せずに公開することのないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bda36-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bda36-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bda36-112">See also</span></span>

- [<span data-ttu-id="bda36-113">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="bda36-113">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="bda36-114">ASP.NET Core のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="bda36-114">ASP.NET Core Security</span></span>](/aspnet/core/security/)
