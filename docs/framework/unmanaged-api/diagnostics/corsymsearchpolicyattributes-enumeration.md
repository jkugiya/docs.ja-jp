---
description: 詳細については、「CorSymSearchPolicyAttributes 列挙型」を参照してください。
title: CorSymSearchPolicyAttributes 列挙体
ms.date: 03/30/2017
api_name:
- CorSymSearchPolicyAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymSearchPolicyAttributes
helpviewer_keywords:
- CorSymSearchPolicyAttributes enumeration [.NET Framework debugging]
ms.assetid: 03abde84-930a-49d3-bac3-23abb34a0184
topic_type:
- apiref
ms.openlocfilehash: a9af0e96809ec8eba5c03c2e372e818c74914baf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800475"
---
# <a name="corsymsearchpolicyattributes-enumeration"></a><span data-ttu-id="a1ce7-103">CorSymSearchPolicyAttributes 列挙体</span><span class="sxs-lookup"><span data-stu-id="a1ce7-103">CorSymSearchPolicyAttributes Enumeration</span></span>

<span data-ttu-id="a1ce7-104">シンボルリーダーの検索を実行するときに使用するポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-104">Specifies the policy to be used when doing a search for a symbol reader.</span></span> <span data-ttu-id="a1ce7-105">これらの定数は、 [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) メソッドと [ISymUnmanagedBinder3:: GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) メソッドによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-105">These constants are used by the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) and [ISymUnmanagedBinder3::GetReaderFromCallback](isymunmanagedbinder3-getreaderfromcallback-method.md) methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a1ce7-106">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ce7-107">構文</span><span class="sxs-lookup"><span data-stu-id="a1ce7-107">Syntax</span></span>  
  
```cpp  
typedef enum CorSymSearchPolicyAttributes  
{  
    AllowRegistryAccess      = 0x1,
    AllowSymbolServerAccess  = 0x2,  
    AllowOriginalPathAccess  = 0x4,     //
    AllowReferencePathAccess = 0x8  
} CorSymSearchPolicyAttributes;  
```  
  
## <a name="members"></a><span data-ttu-id="a1ce7-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1ce7-108">Members</span></span>  
  
|<span data-ttu-id="a1ce7-109">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1ce7-109">Member</span></span>|<span data-ttu-id="a1ce7-110">説明</span><span class="sxs-lookup"><span data-stu-id="a1ce7-110">Description</span></span>|  
|------------|-----------------|  
|`AllowRegistryAccess`|<span data-ttu-id="a1ce7-111">シンボル検索パスのレジストリを照会します。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-111">Queries the registry for symbol search paths.</span></span>|  
|`AllowSymbolServerAccess`|<span data-ttu-id="a1ce7-112">シンボルサーバーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-112">Accesses a symbol server.</span></span>|  
|`AllowOriginalPathAccess`|<span data-ttu-id="a1ce7-113">デバッグディレクトリに指定されているパスを検索します。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-113">Searches the path specified in the Debug directory.</span></span>|  
|`AllowReferencePathAccess`|<span data-ttu-id="a1ce7-114">.Exe ファイルがある場所で PDB を検索します。</span><span class="sxs-lookup"><span data-stu-id="a1ce7-114">Searches for the PDB in the place where the .exe file is.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1ce7-115">要件</span><span class="sxs-lookup"><span data-stu-id="a1ce7-115">Requirements</span></span>  

 <span data-ttu-id="a1ce7-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a1ce7-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ce7-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1ce7-117">See also</span></span>

- [<span data-ttu-id="a1ce7-118">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="a1ce7-118">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
