---
description: 詳細については、「ISymUnmanagedVariable インターフェイス」を参照してください。
title: ISymUnmanagedVariable インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable
helpviewer_keywords:
- ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type:
- apiref
ms.openlocfilehash: 15b6c7018f92ad4c82abb9e5b4e52bf428b3f54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762696"
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="00332-103">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00332-103">ISymUnmanagedVariable Interface</span></span>

<span data-ttu-id="00332-104">パラメーター、ローカル変数、またはフィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="00332-104">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00332-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-105">Methods</span></span>  
  
|<span data-ttu-id="00332-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-106">Method</span></span>|<span data-ttu-id="00332-107">説明</span><span class="sxs-lookup"><span data-stu-id="00332-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00332-108">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-108">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="00332-109">この変数の最初のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-109">Gets the first address field for this variable.</span></span> <span data-ttu-id="00332-110">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="00332-110">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="00332-111">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-111">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="00332-112">この変数の2番目のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-112">Gets the second address field for this variable.</span></span> <span data-ttu-id="00332-113">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="00332-113">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="00332-114">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-114">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="00332-115">この変数の3番目のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-115">Gets the third address field for this variable.</span></span> <span data-ttu-id="00332-116">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="00332-116">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="00332-117">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="00332-118">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-118">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="00332-119">GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-119">GetAttributes Method</span></span>](isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="00332-120">この変数の属性フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-120">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="00332-121">GetEndOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-121">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="00332-122">親内のこの変数の終了オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-122">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="00332-123">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-123">GetName Method</span></span>](isymunmanagedvariable-getname-method.md)|<span data-ttu-id="00332-124">この変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-124">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="00332-125">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-125">GetSignature Method</span></span>](isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="00332-126">この変数のシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-126">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="00332-127">GetStartOffSet メソッド</span><span class="sxs-lookup"><span data-stu-id="00332-127">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="00332-128">親内のこの変数の開始オフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="00332-128">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00332-129">要件</span><span class="sxs-lookup"><span data-stu-id="00332-129">Requirements</span></span>  

 <span data-ttu-id="00332-130">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="00332-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00332-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="00332-131">See also</span></span>

- [<span data-ttu-id="00332-132">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00332-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
