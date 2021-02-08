---
description: '詳細について: ICLRMetadataLocator:: GetMetadata メソッド'
title: ICLRMetadataLocator::GetMetadata メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
ms.openlocfilehash: 4a7e8b906b66c4295dd24800d260790526114701
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772613"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="23d26-103">ICLRMetadataLocator::GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="23d26-103">ICLRMetadataLocator::GetMetadata Method</span></span>

<span data-ttu-id="23d26-104">イメージのメタデータを取得するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="23d26-104">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23d26-105">構文</span><span class="sxs-lookup"><span data-stu-id="23d26-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23d26-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23d26-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="23d26-107">からイメージファイルのパスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="23d26-107">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="23d26-108">からイメージファイルのタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="23d26-108">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="23d26-109">からイメージファイルのサイズ。</span><span class="sxs-lookup"><span data-stu-id="23d26-109">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="23d26-110">からイメージのグローバル一意識別子。</span><span class="sxs-lookup"><span data-stu-id="23d26-110">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="23d26-111">からメタデータの相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="23d26-111">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="23d26-112">アドレスは、イメージのベースアドレスを基準としています。</span><span class="sxs-lookup"><span data-stu-id="23d26-112">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="23d26-113">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="23d26-113">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="23d26-114">からメタデータを格納するバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="23d26-114">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="23d26-115">入出力メタデータを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="23d26-115">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="23d26-116">入出力返されるメタデータのサイズ。</span><span class="sxs-lookup"><span data-stu-id="23d26-116">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23d26-117">解説</span><span class="sxs-lookup"><span data-stu-id="23d26-117">Remarks</span></span>  

 <span data-ttu-id="23d26-118">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="23d26-118">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d26-119">要件</span><span class="sxs-lookup"><span data-stu-id="23d26-119">Requirements</span></span>  

 <span data-ttu-id="23d26-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23d26-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23d26-121">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="23d26-121">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="23d26-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23d26-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23d26-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23d26-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d26-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="23d26-124">See also</span></span>

- [<span data-ttu-id="23d26-125">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23d26-125">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
