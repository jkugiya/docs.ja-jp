---
description: '詳細について: IMetaDataImport2:: GetVersionString メソッド'
title: IMetaDataImport2::GetVersionString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 6f7e296607dc3167936c69d52a8baae4f5555b88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688560"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="caebc-103">IMetaDataImport2::GetVersionString メソッド</span><span class="sxs-lookup"><span data-stu-id="caebc-103">IMetaDataImport2::GetVersionString Method</span></span>

<span data-ttu-id="caebc-104">アセンブリのビルドに使用されたランタイムのバージョン番号を取得します。</span><span class="sxs-lookup"><span data-stu-id="caebc-104">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caebc-105">構文</span><span class="sxs-lookup"><span data-stu-id="caebc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caebc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="caebc-106">Parameters</span></span>  

 `pwzBuf`  
 <span data-ttu-id="caebc-107">入出力バージョンを指定する文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="caebc-107">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="caebc-108">から配列のサイズ (ワイド文字単位) `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="caebc-108">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="caebc-109">入出力配列内で返された、null 終端文字を含むワイド文字の数 `pwzBuf` 。</span><span class="sxs-lookup"><span data-stu-id="caebc-109">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="caebc-110">解説</span><span class="sxs-lookup"><span data-stu-id="caebc-110">Remarks</span></span>  

 <span data-ttu-id="caebc-111">メソッドは、 `GetVersionString` 現在のメタデータスコープの組み込みバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="caebc-111">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="caebc-112">スコープが一度も保存されていない場合は、ビルドされたバージョンがないため、空の文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="caebc-112">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caebc-113">要件</span><span class="sxs-lookup"><span data-stu-id="caebc-113">Requirements</span></span>  

 <span data-ttu-id="caebc-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caebc-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caebc-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="caebc-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="caebc-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="caebc-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caebc-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caebc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caebc-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="caebc-118">See also</span></span>

- [<span data-ttu-id="caebc-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caebc-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="caebc-120">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="caebc-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
