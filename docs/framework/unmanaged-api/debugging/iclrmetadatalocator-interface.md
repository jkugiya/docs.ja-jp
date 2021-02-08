---
description: 詳細については、「ICLRMetadataLocator インターフェイス」を参照してください。
title: ICLRMetadataLocator インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator
helpviewer_keywords:
- ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type:
- apiref
ms.openlocfilehash: 6e7fd45197294563e12da020379d1bd54b088698
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772610"
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="7effa-103">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7effa-103">ICLRMetadataLocator Interface</span></span>

<span data-ttu-id="7effa-104">ターゲットプロセス内のアセンブリのメタデータを検索するために、データアクセスサービス層によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7effa-104">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7effa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7effa-105">Methods</span></span>  
  
|<span data-ttu-id="7effa-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7effa-106">Method</span></span>|<span data-ttu-id="7effa-107">説明</span><span class="sxs-lookup"><span data-stu-id="7effa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7effa-108">GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="7effa-108">GetMetadata Method</span></span>](iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="7effa-109">ターゲットプロセスからイメージのメタデータを取得します。</span><span class="sxs-lookup"><span data-stu-id="7effa-109">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7effa-110">解説</span><span class="sxs-lookup"><span data-stu-id="7effa-110">Remarks</span></span>  

 <span data-ttu-id="7effa-111">API クライアント (つまりデバッガー) は、特定のターゲット プロセスに応じてこのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7effa-111">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7effa-112">たとえば、ライブプロセスの実装は、メモリダンプの実装とは異なります。</span><span class="sxs-lookup"><span data-stu-id="7effa-112">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7effa-113">要件</span><span class="sxs-lookup"><span data-stu-id="7effa-113">Requirements</span></span>  

 <span data-ttu-id="7effa-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7effa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7effa-115">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="7effa-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7effa-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7effa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7effa-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7effa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7effa-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7effa-118">See also</span></span>

- [<span data-ttu-id="7effa-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7effa-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
