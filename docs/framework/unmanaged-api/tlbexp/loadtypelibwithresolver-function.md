---
description: '詳細情報: LoadTypeLibWithResolver 関数'
title: LoadTypeLibWithResolver 関数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
ms.openlocfilehash: 6747199364a549d922ad73bfac3e93b329d1172a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646219"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="098f8-103">LoadTypeLibWithResolver 関数</span><span class="sxs-lookup"><span data-stu-id="098f8-103">LoadTypeLibWithResolver Function</span></span>

<span data-ttu-id="098f8-104">タイプライブラリを読み込み、指定された [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) を使用して、内部で参照されているタイプライブラリを解決します。</span><span class="sxs-lookup"><span data-stu-id="098f8-104">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098f8-105">構文</span><span class="sxs-lookup"><span data-stu-id="098f8-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="098f8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="098f8-106">Parameters</span></span>  

 `szFile`  
 <span data-ttu-id="098f8-107">からタイプライブラリのファイルパス。</span><span class="sxs-lookup"><span data-stu-id="098f8-107">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="098f8-108">からタイプライブラリの登録方法を制御する [Regkind 列挙](/windows/win32/api/oleauto/ne-oleauto-regkind) フラグ。</span><span class="sxs-lookup"><span data-stu-id="098f8-108">[in] A [REGKIND enumeration](/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="098f8-109">指定できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="098f8-109">Its possible values are:</span></span>  
  
- <span data-ttu-id="098f8-110">`REGKIND_DEFAULT`: 既定の登録動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="098f8-110">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="098f8-111">`REGKIND_REGISTER`: このタイプライブラリを登録します。</span><span class="sxs-lookup"><span data-stu-id="098f8-111">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="098f8-112">`REGKIND_NONE`: このタイプライブラリを登録しません。</span><span class="sxs-lookup"><span data-stu-id="098f8-112">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="098f8-113">から [ITypeLibResolver インターフェイス](itypelibresolver-interface.md)の実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="098f8-113">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="098f8-114">入出力読み込まれているタイプライブラリへの参照。</span><span class="sxs-lookup"><span data-stu-id="098f8-114">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="098f8-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="098f8-115">Return Value</span></span>  

 <span data-ttu-id="098f8-116">次の表に示す HRESULT 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="098f8-116">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="098f8-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="098f8-117">Return value</span></span>|<span data-ttu-id="098f8-118">説明</span><span class="sxs-lookup"><span data-stu-id="098f8-118">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="098f8-119">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="098f8-119">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="098f8-120">メモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="098f8-120">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="098f8-121">1つ以上のポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="098f8-121">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="098f8-122">1 つ以上の引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="098f8-122">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="098f8-123">関数はファイルに書き込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="098f8-123">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="098f8-124">システム登録データベースを開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="098f8-124">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="098f8-125">タイプライブラリを開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="098f8-125">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="098f8-126">タイプライブラリまたは DLL を読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="098f8-126">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="098f8-127">解説</span><span class="sxs-lookup"><span data-stu-id="098f8-127">Remarks</span></span>  

 <span data-ttu-id="098f8-128">[Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)は、 `LoadTypeLibWithResolver` アセンブリからタイプライブラリへの変換プロセス中に関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="098f8-128">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="098f8-129">この関数は、レジストリへの最小限のアクセスで、指定されたタイプライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="098f8-129">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="098f8-130">次に、関数は、内部的に参照されるタイプライブラリのタイプライブラリを調べます。このタイプライブラリはそれぞれ、親タイプライブラリに読み込まれ、追加される必要があります。</span><span class="sxs-lookup"><span data-stu-id="098f8-130">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="098f8-131">参照されるタイプライブラリを読み込む前に、その参照ファイルのパスを完全なファイルパスに解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="098f8-131">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="098f8-132">これは、パラメーターで渡される[ITypeLibResolver インターフェイス](itypelibresolver-interface.md)によって提供される[resolvetypelib メソッド](resolvetypelib-method.md)を使用して実現され `pTlbResolver` ます。</span><span class="sxs-lookup"><span data-stu-id="098f8-132">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="098f8-133">参照されているタイプライブラリの完全なファイルパスがわかっている場合、この関数は参照されている `LoadTypeLibWithResolver` タイプライブラリを読み込んで親タイプライブラリに追加し、結合されたマスタータイプライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="098f8-133">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="098f8-134">関数は、内部的に参照されるすべてのタイプライブラリを解決して読み込み、パラメーター内のマスター解決済みタイプライブラリへの参照を返し `pptlib` ます。</span><span class="sxs-lookup"><span data-stu-id="098f8-134">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="098f8-135">関数は、 `LoadTypeLibWithResolver` 通常、 [Tlbexp.exe (タイプライブラリエクスポーター)](../../tools/tlbexp-exe-type-library-exporter.md)によって呼び出されます。この関数は、パラメーターに独自の内部 [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) 実装を提供し `pTlbResolver` ます。</span><span class="sxs-lookup"><span data-stu-id="098f8-135">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="098f8-136">を直接呼び出す場合は `LoadTypeLibWithResolver` 、独自の [ITypeLibResolver インターフェイス](itypelibresolver-interface.md) 実装を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="098f8-136">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="098f8-137">要件</span><span class="sxs-lookup"><span data-stu-id="098f8-137">Requirements</span></span>  

 <span data-ttu-id="098f8-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="098f8-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="098f8-139">**ヘッダー:** Tlf .h</span><span class="sxs-lookup"><span data-stu-id="098f8-139">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="098f8-140">**ライブラリ:** Tlf .lib</span><span class="sxs-lookup"><span data-stu-id="098f8-140">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="098f8-141">**.NET Framework バージョン:** 3.5、3.0、2.0</span><span class="sxs-lookup"><span data-stu-id="098f8-141">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098f8-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="098f8-142">See also</span></span>

- [<span data-ttu-id="098f8-143">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="098f8-143">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="098f8-144">LoadTypeLibEx 関数</span><span class="sxs-lookup"><span data-stu-id="098f8-144">LoadTypeLibEx Function</span></span>](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
