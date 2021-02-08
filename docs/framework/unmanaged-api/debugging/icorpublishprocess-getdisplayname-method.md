---
description: '詳細について: ICorPublishProcess:: GetDisplayName メソッド'
title: ICorPublishProcess::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
ms.openlocfilehash: 7aef55a40c24953766377f21e8291bceb1594480
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794586"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="3db8f-103">ICorPublishProcess::GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="3db8f-103">ICorPublishProcess::GetDisplayName Method</span></span>

<span data-ttu-id="3db8f-104">この [ICorPublishProcess](icorpublishprocess-interface.md)によって参照されるプロセスの実行可能ファイルの完全パスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3db8f-104">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3db8f-105">構文</span><span class="sxs-lookup"><span data-stu-id="3db8f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR                        *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3db8f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3db8f-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="3db8f-107">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="3db8f-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3db8f-108">入出力配列内で返されたワイド文字の数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="3db8f-108">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="3db8f-109">入出力実行可能ファイルの完全パスを含む、名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="3db8f-109">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="3db8f-110">名前が null で終了しています。</span><span class="sxs-lookup"><span data-stu-id="3db8f-110">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3db8f-111">要件</span><span class="sxs-lookup"><span data-stu-id="3db8f-111">Requirements</span></span>  

 <span data-ttu-id="3db8f-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3db8f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db8f-113">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="3db8f-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3db8f-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3db8f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3db8f-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db8f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db8f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3db8f-116">See also</span></span>

- [<span data-ttu-id="3db8f-117">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3db8f-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
