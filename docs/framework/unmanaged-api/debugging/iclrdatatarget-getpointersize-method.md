---
description: '詳細について: ICLRDataTarget:: Getポインター Size メソッド'
title: ICLRDataTarget::GetPointerSize メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
ms.openlocfilehash: 4c6e5ab9b919d1c5d2d6e2267a48d46a11cccc09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801333"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="e3acd-103">ICLRDataTarget::GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="e3acd-103">ICLRDataTarget::GetPointerSize Method</span></span>

<span data-ttu-id="e3acd-104">ターゲットプロセスが使用するポインター型のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="e3acd-104">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="e3acd-105">このメソッドは、共通言語ランタイムのデータアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e3acd-105">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3acd-106">構文</span><span class="sxs-lookup"><span data-stu-id="e3acd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3acd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3acd-107">Parameters</span></span>  

 `pointerSize`  
 <span data-ttu-id="e3acd-108">入出力ターゲットプロセスのポインターのサイズ (バイト単位) を指定する整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e3acd-108">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3acd-109">解説</span><span class="sxs-lookup"><span data-stu-id="e3acd-109">Remarks</span></span>  

 <span data-ttu-id="e3acd-110">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="e3acd-110">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3acd-111">要件</span><span class="sxs-lookup"><span data-stu-id="e3acd-111">Requirements</span></span>  

 <span data-ttu-id="e3acd-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3acd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3acd-113">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="e3acd-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e3acd-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3acd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3acd-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3acd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3acd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3acd-116">See also</span></span>

- [<span data-ttu-id="e3acd-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e3acd-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
