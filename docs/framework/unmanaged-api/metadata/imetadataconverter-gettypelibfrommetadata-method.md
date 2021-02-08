---
description: '詳細について: IMetaDataConverter:: GetTypeLibFromMetaData メソッド'
title: IMetaDataConverter::GetTypeLibFromMetaData メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: 5eecc87f938740366b7938d6ec3d1460ebcfb7eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789269"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="8aa01-103">IMetaDataConverter::GetTypeLibFromMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="8aa01-103">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>

<span data-ttu-id="8aa01-104">指定した `ITypeLib` ライブラリ名とモジュール名を持つタイプライブラリを表すインスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8aa01-104">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa01-105">構文</span><span class="sxs-lookup"><span data-stu-id="8aa01-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aa01-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8aa01-106">Parameters</span></span>  

 `strModule`  
 <span data-ttu-id="8aa01-107">からタイプライブラリのモジュールの名前。</span><span class="sxs-lookup"><span data-stu-id="8aa01-107">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="8aa01-108">からタイプライブラリの名前。</span><span class="sxs-lookup"><span data-stu-id="8aa01-108">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="8aa01-109">入出力タイプライブラリを表すインスタンスのアドレスを受け取る場所へのポインター `ITypeLib` 。</span><span class="sxs-lookup"><span data-stu-id="8aa01-109">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa01-110">要件</span><span class="sxs-lookup"><span data-stu-id="8aa01-110">Requirements</span></span>  

 <span data-ttu-id="8aa01-111">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aa01-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa01-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8aa01-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8aa01-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8aa01-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8aa01-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa01-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa01-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aa01-115">See also</span></span>

- [<span data-ttu-id="8aa01-116">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8aa01-116">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
