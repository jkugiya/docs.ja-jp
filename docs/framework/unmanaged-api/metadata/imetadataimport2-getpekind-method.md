---
description: '詳細について: IMetaDataImport2:: GetPEKind メソッド'
title: IMetaDataImport2::GetPEKind メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
ms.openlocfilehash: 3cd003f4b1a56f59b9e8c89bf1c4f8f2f8c7fea1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688586"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="96467-103">IMetaDataImport2::GetPEKind メソッド</span><span class="sxs-lookup"><span data-stu-id="96467-103">IMetaDataImport2::GetPEKind Method</span></span>

<span data-ttu-id="96467-104">現在のメタデータスコープで定義されている、ポータブル実行可能 (PE) ファイル (通常は DLL または EXE ファイル) 内のコードの性質を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="96467-104">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96467-105">構文</span><span class="sxs-lookup"><span data-stu-id="96467-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96467-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96467-106">Parameters</span></span>  

 `pdwPEKind`  
 <span data-ttu-id="96467-107">入出力PE ファイルを記述する [Corpekind](corpekind-enumeration.md) 列挙型の値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="96467-107">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="96467-108">入出力コンピューターのアーキテクチャを識別する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="96467-108">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="96467-109">使用可能な値については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="96467-109">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96467-110">解説</span><span class="sxs-lookup"><span data-stu-id="96467-110">Remarks</span></span>  

 <span data-ttu-id="96467-111">パラメーターによって参照される値には、 `pdwMachine` 次のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="96467-111">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="96467-112">値</span><span class="sxs-lookup"><span data-stu-id="96467-112">Value</span></span>|<span data-ttu-id="96467-113">コンピューターのアーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="96467-113">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="96467-114">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="96467-114">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="96467-115">0x014C</span><span class="sxs-lookup"><span data-stu-id="96467-115">0x014C</span></span>|<span data-ttu-id="96467-116">x86</span><span class="sxs-lookup"><span data-stu-id="96467-116">x86</span></span>|  
|<span data-ttu-id="96467-117">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="96467-117">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="96467-118">0x0200</span><span class="sxs-lookup"><span data-stu-id="96467-118">0x0200</span></span>|<span data-ttu-id="96467-119">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="96467-119">Intel IPF</span></span>|  
|<span data-ttu-id="96467-120">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="96467-120">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="96467-121">0x8664</span><span class="sxs-lookup"><span data-stu-id="96467-121">0x8664</span></span>|<span data-ttu-id="96467-122">X64</span><span class="sxs-lookup"><span data-stu-id="96467-122">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96467-123">要件</span><span class="sxs-lookup"><span data-stu-id="96467-123">Requirements</span></span>  

 <span data-ttu-id="96467-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="96467-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96467-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="96467-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96467-126">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="96467-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96467-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96467-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96467-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="96467-128">See also</span></span>

- [<span data-ttu-id="96467-129">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96467-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="96467-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96467-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="96467-131">CorPEKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="96467-131">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
