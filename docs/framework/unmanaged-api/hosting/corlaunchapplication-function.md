---
description: 詳細については、「CorLaunchApplication 関数」を参照してください。
title: CorLaunchApplication 関数
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
ms.openlocfilehash: 89f1f37ddde69fb5ecc24fd9dfd0d0c27d5fac40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716953"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="499e6-103">CorLaunchApplication 関数</span><span class="sxs-lookup"><span data-stu-id="499e6-103">CorLaunchApplication Function</span></span>

<span data-ttu-id="499e6-104">指定したネットワーク パスのアプリケーションを、指定したマニフェストとその他のアプリケーション データを使用して起動します。</span><span class="sxs-lookup"><span data-stu-id="499e6-104">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="499e6-105">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="499e6-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="499e6-106">構文</span><span class="sxs-lookup"><span data-stu-id="499e6-106">Syntax</span></span>  
  
```cpp  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="499e6-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="499e6-107">Parameters</span></span>  

 `dwClickOnceHost`  
 <span data-ttu-id="499e6-108">からアプリケーションを起動しているホストの種類を指定する [HOST_TYPE](host-type-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="499e6-108">[in] A value of the [HOST_TYPE](host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="499e6-109">から起動されるアプリケーションの完全な名前。</span><span class="sxs-lookup"><span data-stu-id="499e6-109">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="499e6-110">からアプリケーションのマニフェストパスの数。</span><span class="sxs-lookup"><span data-stu-id="499e6-110">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="499e6-111">から文字列の配列。それぞれが、起動されるアプリケーションのマニフェストへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="499e6-111">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="499e6-112">から起動されるアプリケーションのアクティブ化データ項目の数。</span><span class="sxs-lookup"><span data-stu-id="499e6-112">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="499e6-113">から文字列の配列。各文字列は、起動されるアプリケーションのアクティベーションデータ項目です。</span><span class="sxs-lookup"><span data-stu-id="499e6-113">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="499e6-114">入出力アプリケーションが読み込まれたプロセスに関する情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="499e6-114">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="499e6-115">要件</span><span class="sxs-lookup"><span data-stu-id="499e6-115">Requirements</span></span>  

 <span data-ttu-id="499e6-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="499e6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="499e6-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="499e6-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="499e6-118">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="499e6-118">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="499e6-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="499e6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499e6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="499e6-120">See also</span></span>

- [<span data-ttu-id="499e6-121">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="499e6-121">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
