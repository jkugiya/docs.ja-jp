---
description: '詳細情報: Createhistory Reader 関数'
title: CreateHistoryReader 関数
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 0943f3d0f3322d34ed92c0a96b909e4d63ec5e7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761123"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="0d089-103">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="0d089-103">CreateHistoryReader Function</span></span>

<span data-ttu-id="0d089-104">指定されたファイルの履歴リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d089-104">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d089-105">構文</span><span class="sxs-lookup"><span data-stu-id="0d089-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d089-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0d089-106">Parameters</span></span>  

 `wzFilePath`  
 <span data-ttu-id="0d089-107">からファイルパス。</span><span class="sxs-lookup"><span data-stu-id="0d089-107">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="0d089-108">入出力正常に完了した場合は、履歴リーダーへのポインターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0d089-108">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d089-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0d089-109">Return Value</span></span>  

 <span data-ttu-id="0d089-110">このメソッドは、次の表で説明する値に加えて、Winerror.h で定義されている標準 COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="0d089-110">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="0d089-111">リターン コード</span><span class="sxs-lookup"><span data-stu-id="0d089-111">Return code</span></span>|<span data-ttu-id="0d089-112">説明</span><span class="sxs-lookup"><span data-stu-id="0d089-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="0d089-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d089-113">S_OK</span></span>|<span data-ttu-id="0d089-114">メソッドが正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="0d089-114">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="0d089-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0d089-115">E_INVALIDARG</span></span>|<span data-ttu-id="0d089-116">`wzFilePath`または `ppHistoryReader` が null 参照に設定されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0d089-116">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d089-117">要件</span><span class="sxs-lookup"><span data-stu-id="0d089-117">Requirements</span></span>  

 <span data-ttu-id="0d089-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d089-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d089-119">**ライブラリ:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="0d089-119">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="0d089-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d089-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d089-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d089-121">See also</span></span>

- [<span data-ttu-id="0d089-122">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="0d089-122">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
