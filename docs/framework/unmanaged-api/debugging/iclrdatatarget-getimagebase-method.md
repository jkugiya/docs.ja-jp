---
description: '詳細について: ICLRDataTarget:: GetImageBase メソッド'
title: ICLRDataTarget::GetImageBase メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
ms.openlocfilehash: 34e8341b219aaa184b4894c631f854e0a31921d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794872"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="86052-103">ICLRDataTarget::GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="86052-103">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="86052-104">指定したイメージのベースメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="86052-104">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86052-105">構文</span><span class="sxs-lookup"><span data-stu-id="86052-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86052-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86052-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="86052-107">からパスを含む、イメージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="86052-107">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="86052-108">入出力イメージのベースアドレスを格納する CLRDATA_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="86052-108">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86052-109">解説</span><span class="sxs-lookup"><span data-stu-id="86052-109">Remarks</span></span>  

 <span data-ttu-id="86052-110">イメージファイル名には、パスを指定することも、パスを指定することもできません。</span><span class="sxs-lookup"><span data-stu-id="86052-110">The image file name may or may not have a path.</span></span> <span data-ttu-id="86052-111">パスが指定されている場合、パス全体で一致が行われます。それ以外の場合、一致はファイル名でのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="86052-111">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86052-112">要件</span><span class="sxs-lookup"><span data-stu-id="86052-112">Requirements</span></span>  

 <span data-ttu-id="86052-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86052-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86052-114">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="86052-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="86052-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86052-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86052-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86052-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86052-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="86052-117">See also</span></span>

- [<span data-ttu-id="86052-118">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86052-118">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
