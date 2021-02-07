---
description: '詳細情報: ISymUnmanagedWriter:: SetUserEntryPoint メソッド'
title: ISymUnmanagedWriter::SetUserEntryPoint メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
ms.openlocfilehash: a01d23a0462fabd7a2fc259722dcdf2a1c8e0a4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761981"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="8544f-103">ISymUnmanagedWriter::SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="8544f-103">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>

<span data-ttu-id="8544f-104">このモジュールのエントリポイントであるユーザー定義メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="8544f-104">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="8544f-105">たとえば、このエントリポイントは、main の前にコンパイラで生成されたスタブではなく、ユーザーのメインメソッドである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8544f-105">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8544f-106">構文</span><span class="sxs-lookup"><span data-stu-id="8544f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8544f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8544f-107">Parameters</span></span>  

 `entryMethod`  
 <span data-ttu-id="8544f-108">からユーザーエントリポイントであるメソッドのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="8544f-108">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8544f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8544f-109">Return Value</span></span>  

 <span data-ttu-id="8544f-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="8544f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8544f-111">要件</span><span class="sxs-lookup"><span data-stu-id="8544f-111">Requirements</span></span>  

 <span data-ttu-id="8544f-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="8544f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8544f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8544f-113">See also</span></span>

- [<span data-ttu-id="8544f-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8544f-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
