---
description: '詳細については、次を参照してください: ICeeGen:: GetSectionCreate メソッド'
title: ICeeGen::GetSectionCreate メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 2839d11c927dbf573f213d3ebaa9e6e6d8d5015d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706865"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="c733f-103">ICeeGen::GetSectionCreate メソッド</span><span class="sxs-lookup"><span data-stu-id="c733f-103">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="c733f-104">指定された名前とフラグ値を使用して、コードセクションを生成して取得します。</span><span class="sxs-lookup"><span data-stu-id="c733f-104">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="c733f-105">このメソッドは互換性のために残されています。使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c733f-105">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c733f-106">構文</span><span class="sxs-lookup"><span data-stu-id="c733f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c733f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c733f-107">Parameters</span></span>  

 `name`  
 <span data-ttu-id="c733f-108">から作成するセクションの名前を指定する文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c733f-108">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="c733f-109">からオプションを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="c733f-109">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="c733f-110">入出力新しく作成されたコードセクションへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c733f-110">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c733f-111">解説</span><span class="sxs-lookup"><span data-stu-id="c733f-111">Remarks</span></span>  

 <span data-ttu-id="c733f-112">`GetSectionCreate`他のメソッドによって処理されない特殊なセクション要件がある場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c733f-112">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c733f-113">要件</span><span class="sxs-lookup"><span data-stu-id="c733f-113">Requirements</span></span>  

 <span data-ttu-id="c733f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c733f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c733f-115">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c733f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c733f-116">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c733f-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c733f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c733f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c733f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c733f-118">See also</span></span>

- [<span data-ttu-id="c733f-119">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c733f-119">ICeeGen Interface</span></span>](iceegen-interface.md)
