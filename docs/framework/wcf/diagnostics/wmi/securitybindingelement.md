---
description: '詳細情報: 説明'
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: bc9a519978a9cccccd80a58abb8d109fa9bc9337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743812"
---
# <a name="securitybindingelement"></a><span data-ttu-id="cba6f-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="cba6f-103">SecurityBindingElement</span></span>

<span data-ttu-id="cba6f-104">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="cba6f-104">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cba6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="cba6f-105">Syntax</span></span>  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cba6f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="cba6f-106">Methods</span></span>  

 <span data-ttu-id="cba6f-107">SecurityBindingElement クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="cba6f-107">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cba6f-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cba6f-108">Properties</span></span>  

 <span data-ttu-id="cba6f-109">SecurityBindingElement クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="cba6f-109">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="cba6f-110">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="cba6f-110">DefaultAlgorithmSuite</span></span>  

 <span data-ttu-id="cba6f-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="cba6f-111">Data type: string</span></span>  
  
 <span data-ttu-id="cba6f-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-113">バインディングで使用するアルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="cba6f-113">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="cba6f-114">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="cba6f-114">IncludeTimestamp</span></span>  

 <span data-ttu-id="cba6f-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="cba6f-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="cba6f-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-117">各メッセージにタイムスタンプが含まれるかどうかを指定するブール値です。</span><span class="sxs-lookup"><span data-stu-id="cba6f-117">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="cba6f-118">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="cba6f-118">KeyEntropyMode</span></span>  

 <span data-ttu-id="cba6f-119">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="cba6f-119">Data type: string</span></span>  
  
 <span data-ttu-id="cba6f-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-121">キーの作成に使用されるエントロピのソースです。</span><span class="sxs-lookup"><span data-stu-id="cba6f-121">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="cba6f-122">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cba6f-122">LocalServiceSecuritySettings</span></span>  

 <span data-ttu-id="cba6f-123">データ型 : LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cba6f-123">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="cba6f-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-125">ローカル サービスに対するバインディング固有のセキュリティ プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cba6f-125">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="cba6f-126">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="cba6f-126">MessageSecurityVersion</span></span>  

 <span data-ttu-id="cba6f-127">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="cba6f-127">Data type: string</span></span>  
  
 <span data-ttu-id="cba6f-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-129">メッセージ セキュリティで使用されるバージョンです。</span><span class="sxs-lookup"><span data-stu-id="cba6f-129">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="cba6f-130">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="cba6f-130">SecurityHeaderLayout</span></span>  

 <span data-ttu-id="cba6f-131">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="cba6f-131">Data type: string</span></span>  
  
 <span data-ttu-id="cba6f-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="cba6f-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cba6f-133">このバインディングのセキュリティ ヘッダー内の要素の順序です。</span><span class="sxs-lookup"><span data-stu-id="cba6f-133">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cba6f-134">要件</span><span class="sxs-lookup"><span data-stu-id="cba6f-134">Requirements</span></span>  
  
|<span data-ttu-id="cba6f-135">MOF</span><span class="sxs-lookup"><span data-stu-id="cba6f-135">MOF</span></span>|<span data-ttu-id="cba6f-136">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="cba6f-136">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cba6f-137">名前空間</span><span class="sxs-lookup"><span data-stu-id="cba6f-137">Namespace</span></span>|<span data-ttu-id="cba6f-138">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="cba6f-138">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cba6f-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="cba6f-139">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
