---
description: '詳細について: IMetaDataDispenserEx:: GetCORSystemDirectory メソッド'
title: IMetaDataDispenserEx::GetCORSystemDirectory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: 3ceda653e50ba5ad7de5548b78781f48cda41624
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753563"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="7dd2c-103">IMetaDataDispenserEx::GetCORSystemDirectory メソッド</span><span class="sxs-lookup"><span data-stu-id="7dd2c-103">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>

<span data-ttu-id="7dd2c-104">現在の共通言語ランタイム (CLR) が格納されているディレクトリを取得します。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-104">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="7dd2c-105">このメソッドは、アウトプロセスデバッガーでの使用に対してのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-105">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="7dd2c-106">別のコンポーネントから呼び出された場合は、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-106">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd2c-107">構文</span><span class="sxs-lookup"><span data-stu-id="7dd2c-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7dd2c-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dd2c-108">Parameters</span></span>  

 `szBuffer`  
 <span data-ttu-id="7dd2c-109">入出力ディレクトリ名を受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-109">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7dd2c-110">からのサイズ (バイト単位) `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-110">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="7dd2c-111">入出力実際にで返されたバイト数 `szBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-111">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd2c-112">要件</span><span class="sxs-lookup"><span data-stu-id="7dd2c-112">Requirements</span></span>  

 <span data-ttu-id="7dd2c-113">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-113">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd2c-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="7dd2c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dd2c-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="7dd2c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7dd2c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd2c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd2c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dd2c-117">See also</span></span>

- [<span data-ttu-id="7dd2c-118">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd2c-118">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="7dd2c-119">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dd2c-119">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
