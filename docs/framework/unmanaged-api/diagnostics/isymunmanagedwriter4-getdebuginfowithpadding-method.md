---
description: '詳細について: ISymUnmanagedWriter4:: GetDebugInfoWithPadding メソッド'
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: f5a2026a4ddf12b741b670097e31260e68f33c7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761708"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="0c776-103">ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="0c776-103">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="0c776-104">関数は [GetDebugInfo メソッド](isymunmanagedwriter-getdebuginfo-method.md) と同じですが、文字列データを固定サイズにするために、終端の null 文字の後にパス文字列がゼロで埋め込まれる点が異なり `MAX_PATH` ます。</span><span class="sxs-lookup"><span data-stu-id="0c776-104">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="0c776-105">埋め込みは、パス文字列の長さがより小さい場合にのみ指定 `MAX_PATH` します。</span><span class="sxs-lookup"><span data-stu-id="0c776-105">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="0c776-106">これにより、PE ファイルを区別するツールを簡単に記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c776-106">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c776-107">構文</span><span class="sxs-lookup"><span data-stu-id="0c776-107">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c776-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c776-108">Parameters</span></span>  
  
|<span data-ttu-id="0c776-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c776-109">Parameter</span></span>|<span data-ttu-id="0c776-110">説明</span><span class="sxs-lookup"><span data-stu-id="0c776-110">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="0c776-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0c776-111">Return Value</span></span>  

 <span data-ttu-id="0c776-112">`HRESULT` が返されます。</span><span class="sxs-lookup"><span data-stu-id="0c776-112">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c776-113">要件</span><span class="sxs-lookup"><span data-stu-id="0c776-113">Requirements</span></span>  

 <span data-ttu-id="0c776-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0c776-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c776-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c776-115">See also</span></span>

- [<span data-ttu-id="0c776-116">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c776-116">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
