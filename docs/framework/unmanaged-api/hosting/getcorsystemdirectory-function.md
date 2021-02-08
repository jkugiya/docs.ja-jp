---
description: '詳細情報: GetCORSystemDirectory 関数'
title: GetCORSystemDirectory 関数
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 267736c2f8cdea03fbd9f77108a3d88193830ab4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785342"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="c56fd-103">GetCORSystemDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="c56fd-103">GetCORSystemDirectory Function</span></span>

<span data-ttu-id="c56fd-104">プロセスに読み込まれる共通言語ランタイム (CLR) のインストールディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="c56fd-104">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="c56fd-105">インストールディレクトリは完全に修飾されています。たとえば、"c:\windows\microsoft.net\framework\v1.0.3705" のようになります。</span><span class="sxs-lookup"><span data-stu-id="c56fd-105">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="c56fd-106">この関数の使用は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="c56fd-106">This function is deprecated.</span></span> <span data-ttu-id="c56fd-107">.NET Framework 4 で提供される [ICLRRuntimeInfo:: GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) メソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="c56fd-107">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56fd-108">構文</span><span class="sxs-lookup"><span data-stu-id="c56fd-108">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c56fd-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c56fd-109">Parameters</span></span>  

 `pbuffer`  
 <span data-ttu-id="c56fd-110">入出力プロセスに読み込まれたランタイムのインストールディレクトリの完全修飾名が含まれた文字列をランタイムが返すバッファー。</span><span class="sxs-lookup"><span data-stu-id="c56fd-110">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="c56fd-111">ランタイムがまだプロセスに読み込まれていない場合、関数はコンピューターにインストールされている最新バージョンのランタイムの適切なディレクトリ情報を返します。</span><span class="sxs-lookup"><span data-stu-id="c56fd-111">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c56fd-112">からのサイズ (バイト単位) `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="c56fd-112">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c56fd-113">入出力で返された文字数 `pbuffer` 。</span><span class="sxs-lookup"><span data-stu-id="c56fd-113">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c56fd-114">解説</span><span class="sxs-lookup"><span data-stu-id="c56fd-114">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c56fd-115">CLR のバージョン4を実行しているプロセスでは、この関数を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="c56fd-115">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="c56fd-116">コンピューターに以前のバージョンの CLR がインストールされている場合、この関数はそのバージョンのインストールディレクトリを返します。</span><span class="sxs-lookup"><span data-stu-id="c56fd-116">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c56fd-117">要件</span><span class="sxs-lookup"><span data-stu-id="c56fd-117">Requirements</span></span>  

 <span data-ttu-id="c56fd-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c56fd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c56fd-119">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c56fd-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c56fd-120">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c56fd-120">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c56fd-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c56fd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c56fd-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c56fd-122">See also</span></span>

- [<span data-ttu-id="c56fd-123">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="c56fd-123">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
