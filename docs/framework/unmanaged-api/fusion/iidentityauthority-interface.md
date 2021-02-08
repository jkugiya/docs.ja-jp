---
description: '詳細情報: Iidentity Authority インターフェイス'
title: IIdentityAuthority インターフェイス
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3064a3d95ebe9a098a7cac0766f18654c6fab8b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800137"
---
# <a name="iidentityauthority-interface"></a><span data-ttu-id="32e0b-103">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32e0b-103">IIdentityAuthority Interface</span></span>

<span data-ttu-id="32e0b-104">コードオブジェクトの id キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-104">Manages identity keys for code objects.</span></span>

## <a name="methods"></a><span data-ttu-id="32e0b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="32e0b-105">Methods</span></span>

|<span data-ttu-id="32e0b-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="32e0b-106">Method</span></span>|<span data-ttu-id="32e0b-107">説明</span><span class="sxs-lookup"><span data-stu-id="32e0b-107">Description</span></span>|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|<span data-ttu-id="32e0b-108">指定した2つの [IDefinitionIdentity](idefinitionidentity-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-108">Gets a value that indicates whether the two specified [IDefinitionIdentity](idefinitionidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreReferencesEqual`|<span data-ttu-id="32e0b-109">指定した2つの [IReferenceIdentity](ireferenceidentity-interface.md) インスタンスが等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-109">Gets a value that indicates whether the two specified [IReferenceIdentity](ireferenceidentity-interface.md) instances are equal.</span></span>|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="32e0b-110">指定した2つの文字列定義 id 表現が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-110">Gets a value that indicates whether the two specified string definition identity representations are equal.</span></span>|
|`IIdentityAuthority::AreTextualReferencesEqual`|<span data-ttu-id="32e0b-111">指定した2つの文字列参照 id 表現が等しいかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-111">Gets a value that indicates whether the two specified string reference identity representations are equal.</span></span>|
|`IIdentityAuthority::CreateDefinition`|<span data-ttu-id="32e0b-112">現在のスコープ内のコードオブジェクトを表す新しいインスタンスへのポインターを取得し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-112">Gets a pointer to a new `IDefinitionIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::CreateReference`|<span data-ttu-id="32e0b-113">現在のスコープ内のコードオブジェクトを表す新しいインスタンスへのポインターを取得し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-113">Gets a pointer to a new `IReferenceIdentity` instance that represents the code object in the current scope.</span></span>|
|`IIdentityAuthority::DefinitionToText`|<span data-ttu-id="32e0b-114">指定したの書式設定された文字列バージョンを取得し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-114">Gets a formatted string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DefinitionToTextBuffer`|<span data-ttu-id="32e0b-115">指定したワイド文字バッファーに、指定したの文字列バージョンを格納し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-115">Fills the specified wide character buffer with a string version of the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="32e0b-116">指定した `IDefinitionIdentity` と `IReferenceIdentity` インスタンスが同じコードオブジェクトを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-116">Gets a value that indicates whether the specified `IDefinitionIdentity` and `IReferenceIdentity` instances refer to the same code object.</span></span>|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="32e0b-117">指定した文字列が同じコードオブジェクトを参照しているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-117">Gets a value that indicates whether the specified strings refer to the same code object.</span></span>|
|`IIdentityAuthority::GenerateDefinitionKey`|<span data-ttu-id="32e0b-118">指定したに対して新しく作成された文字列キーへのポインターを取得し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-118">Gets a pointer to a newly created string key for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::GenerateReferenceKey`|<span data-ttu-id="32e0b-119">指定したに対して新しく作成された文字列キーへのポインターを取得し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-119">Gets a pointer to a newly created string key for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::HashDefinition`|<span data-ttu-id="32e0b-120">指定したのハッシュ値を取得し `IDefinitionIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-120">Gets a hash value for the specified `IDefinitionIdentity`.</span></span>|
|`IIdentityAuthority::HashReference`|<span data-ttu-id="32e0b-121">指定したのハッシュ値を取得し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-121">Gets a hash value for the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToText`|<span data-ttu-id="32e0b-122">指定したの書式設定された文字列バージョンを取得し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-122">Gets a formatted string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::ReferenceToTextBuffer`|<span data-ttu-id="32e0b-123">指定したワイド文字バッファーに、指定したの文字列バージョンを格納し `IReferenceIdentity` ます。</span><span class="sxs-lookup"><span data-stu-id="32e0b-123">Fills the specified wide character buffer with a string version of the specified `IReferenceIdentity`.</span></span>|
|`IIdentityAuthority::TextToDefinition`|<span data-ttu-id="32e0b-124">`IDefinitionIdentity`指定した書式設定された文字列から生成されたインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-124">Gets an interface pointer to an `IDefinitionIdentity` instance generated from the specified formatted string.</span></span>|
|`IIdentityAuthority::TextToReference`|<span data-ttu-id="32e0b-125">`IReferenceIdentity`指定した書式設定された文字列から生成されたインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="32e0b-125">Gets an interface pointer to an `IReferenceIdentity` instance generated from the specified formatted string.</span></span>|

## <a name="requirements"></a><span data-ttu-id="32e0b-126">要件</span><span class="sxs-lookup"><span data-stu-id="32e0b-126">Requirements</span></span>

<span data-ttu-id="32e0b-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32e0b-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="32e0b-128">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="32e0b-128">**Header:** Isolation.h</span></span>

<span data-ttu-id="32e0b-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32e0b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="32e0b-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="32e0b-130">See also</span></span>

- [<span data-ttu-id="32e0b-131">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32e0b-131">Fusion Interfaces</span></span>](fusion-interfaces.md)
