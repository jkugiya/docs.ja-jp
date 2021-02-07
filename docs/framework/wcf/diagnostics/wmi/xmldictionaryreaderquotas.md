---
description: '詳細情報: XmlDictionaryReaderQuotas'
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: d1450051e7107e9b92f848d26e6b182bfd2f2340
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756865"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="02e6f-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="02e6f-103">XmlDictionaryReaderQuotas</span></span>

<span data-ttu-id="02e6f-104">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="02e6f-104">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e6f-105">構文</span><span class="sxs-lookup"><span data-stu-id="02e6f-105">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="02e6f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="02e6f-106">Methods</span></span>  

 <span data-ttu-id="02e6f-107">XmlDictionaryReaderQuotas クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="02e6f-107">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="02e6f-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="02e6f-108">Properties</span></span>  

 <span data-ttu-id="02e6f-109">XmlDictionaryReaderQuotas クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="02e6f-109">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="02e6f-110">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="02e6f-110">MaxArrayLength</span></span>  

 <span data-ttu-id="02e6f-111">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02e6f-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="02e6f-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02e6f-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02e6f-113">許される最大配列長。</span><span class="sxs-lookup"><span data-stu-id="02e6f-113">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="02e6f-114">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="02e6f-114">MaxBytesPerRead</span></span>  

 <span data-ttu-id="02e6f-115">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02e6f-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="02e6f-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02e6f-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02e6f-117">1 回の読み取りで返すことができる最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="02e6f-117">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="02e6f-118">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="02e6f-118">MaxDepth</span></span>  

 <span data-ttu-id="02e6f-119">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02e6f-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="02e6f-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02e6f-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02e6f-121">1 回の読み取りでの最大ネスト ノード深度。</span><span class="sxs-lookup"><span data-stu-id="02e6f-121">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="02e6f-122">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="02e6f-122">MaxNameTableCharCount</span></span>  

 <span data-ttu-id="02e6f-123">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02e6f-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="02e6f-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02e6f-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02e6f-125">テーブル名の最大文字数。</span><span class="sxs-lookup"><span data-stu-id="02e6f-125">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="02e6f-126">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="02e6f-126">MaxStringContentLength</span></span>  

 <span data-ttu-id="02e6f-127">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="02e6f-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="02e6f-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="02e6f-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="02e6f-129">XML 要素のコンテンツで許可される最大文字数。</span><span class="sxs-lookup"><span data-stu-id="02e6f-129">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e6f-130">要件</span><span class="sxs-lookup"><span data-stu-id="02e6f-130">Requirements</span></span>  
  
|<span data-ttu-id="02e6f-131">MOF</span><span class="sxs-lookup"><span data-stu-id="02e6f-131">MOF</span></span>|<span data-ttu-id="02e6f-132">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="02e6f-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="02e6f-133">名前空間</span><span class="sxs-lookup"><span data-stu-id="02e6f-133">Namespace</span></span>|<span data-ttu-id="02e6f-134">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="02e6f-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="02e6f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="02e6f-135">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
