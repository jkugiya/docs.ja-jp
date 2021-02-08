---
description: '詳細情報: PeerSecuritySettings'
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: a8b5b8c88e71cb46110fa35186599c0f9c366d17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803010"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="c0628-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c0628-103">PeerSecuritySettings</span></span>

<span data-ttu-id="c0628-104">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c0628-104">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0628-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0628-105">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c0628-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c0628-106">Methods</span></span>  

 <span data-ttu-id="c0628-107">PeerSecuritySettings クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="c0628-107">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c0628-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c0628-108">Properties</span></span>  

 <span data-ttu-id="c0628-109">PeerSecuritySettings クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="c0628-109">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="c0628-110">モード</span><span class="sxs-lookup"><span data-stu-id="c0628-110">Mode</span></span>  

 <span data-ttu-id="c0628-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="c0628-111">Data type: string</span></span>  
  
 <span data-ttu-id="c0628-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c0628-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0628-113">このバインディングで構成されたエンドポイントによって、メッセージ レベルおよびトランスポート レベルのセキュリティが使用されているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c0628-113">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="c0628-114">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c0628-114">Transport</span></span>  

 <span data-ttu-id="c0628-115">データ型 : PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="c0628-115">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="c0628-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="c0628-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0628-117">トランスポートのセキュリティ設定です。</span><span class="sxs-lookup"><span data-stu-id="c0628-117">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0628-118">要件</span><span class="sxs-lookup"><span data-stu-id="c0628-118">Requirements</span></span>  
  
|<span data-ttu-id="c0628-119">MOF</span><span class="sxs-lookup"><span data-stu-id="c0628-119">MOF</span></span>|<span data-ttu-id="c0628-120">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="c0628-120">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c0628-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="c0628-121">Namespace</span></span>|<span data-ttu-id="c0628-122">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="c0628-122">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0628-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0628-123">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
