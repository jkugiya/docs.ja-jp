---
description: '詳細情報: IAppIdAuthority インターフェイス'
title: IAppIdAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: 238885c7f080571b414511c24f9772dbc19b4683
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761006"
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="9b529-103">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b529-103">IAppIdAuthority Interface</span></span>

<span data-ttu-id="9b529-104">アプリケーション id と参照のキーを生成して比較するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b529-104">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b529-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9b529-105">Methods</span></span>  
  
|<span data-ttu-id="9b529-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9b529-106">Method</span></span>|<span data-ttu-id="9b529-107">説明</span><span class="sxs-lookup"><span data-stu-id="9b529-107">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="9b529-108">指定した2つの [IDefinitionAppId](idefinitionappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-108">Gets a value that indicates whether the two specified [IDefinitionAppId](idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="9b529-109">フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="9b529-109">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="9b529-110">指定した2つの [IReferenceAppId](ireferenceappid-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-110">Gets a value that indicates whether the two specified [IReferenceAppId](ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="9b529-111">フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="9b529-111">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="9b529-112">指定した2つの文字列定義が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-112">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="9b529-113">フラグ値 IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="9b529-113">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="9b529-114">指定した2つの文字列参照が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-114">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="9b529-115">フラグ値 IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION を渡して、それぞれのバージョン情報を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="9b529-115">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="9b529-116">現在のスコープ内のアセンブリを表す、新しく生成されたインスタンスへのインターフェイスポインターを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-116">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="9b529-117">現在のスコープ内のアセンブリを表す、新しく作成されたへのインターフェイスポインターを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-117">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="9b529-118">指定した `IDefinitionAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-118">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="9b529-119">指定した `IDefinitionAppId` とが同じアセンブリを表しているかどうかを示す値を取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-119">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="9b529-120">指定した定義文字列と参照文字列が同じアセンブリを表しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-120">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="9b529-121">指定したインスタンスを表す文字列キーを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-121">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="9b529-122">指定したインスタンスを表す文字列キーを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-122">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="9b529-123">指定したインスタンスのハッシュキーを取得し `IDefinitionAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-123">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="9b529-124">指定したインスタンスのハッシュキーを取得し `IReferenceAppId` ます。</span><span class="sxs-lookup"><span data-stu-id="9b529-124">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="9b529-125">指定した `IReferenceAppId` フラグ値を使用して、指定したの文字列バージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-125">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="9b529-126">`IDefinitionAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-126">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="9b529-127">`IReferenceAppId`指定した文字列キーによって参照されるアセンブリを表すインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="9b529-127">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b529-128">要件</span><span class="sxs-lookup"><span data-stu-id="9b529-128">Requirements</span></span>  

 <span data-ttu-id="9b529-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b529-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b529-130">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="9b529-130">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="9b529-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b529-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b529-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b529-132">See also</span></span>

- [<span data-ttu-id="9b529-133">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b529-133">Fusion Interfaces</span></span>](fusion-interfaces.md)
