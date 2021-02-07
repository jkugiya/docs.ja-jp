---
description: 詳細については、「グローバル静的関数のデバッグ」を参照してください。
title: デバッグ グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: efee1bfb6eb61ae2311320a4c12bf08ec0f9534b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661455"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="b1404-103">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="b1404-103">Debugging Global Static Functions</span></span>

<span data-ttu-id="b1404-104">このセクションでは、デバッグ API が使用するアンマネージ グローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1404-104">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1404-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b1404-105">In This Section</span></span>  

 [<span data-ttu-id="b1404-106">_EFN_GetManagedExcepStack 関数</span><span class="sxs-lookup"><span data-stu-id="b1404-106">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="b1404-107">指定したマネージド例外オブジェクトのアドレスに応じて、中に含まれているスタック トレースの文字列バージョンを返します。</span><span class="sxs-lookup"><span data-stu-id="b1404-107">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="b1404-108">_EFN_GetManagedObjectFieldInfo 関数</span><span class="sxs-lookup"><span data-stu-id="b1404-108">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="b1404-109">指定したオブジェクト ポインターとフィールド名を使用して、オブジェクトの先頭からフィールドまでのオフセットとフィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1404-109">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="b1404-110">_EFN_GetManagedObjectName 関数</span><span class="sxs-lookup"><span data-stu-id="b1404-110">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="b1404-111">指定したマネージド オブジェクトのポインターを使用して、型の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1404-111">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="b1404-112">_EFN_StackTrace 関数</span><span class="sxs-lookup"><span data-stu-id="b1404-112">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="b1404-113">マネージド スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージド コードとマネージド コードの間の各移行につき 1 つ) を提供します。</span><span class="sxs-lookup"><span data-stu-id="b1404-113">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="b1404-114">CLRDataCreateInstance 関数</span><span class="sxs-lookup"><span data-stu-id="b1404-114">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="b1404-115">指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b1404-115">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="b1404-116">PFN_CLRDataCreateInstance 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="b1404-116">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="b1404-117">指定した対象プロセスの指定したインターフェイス オブジェクトを作成するために、CLR データ アクセス サービスによって呼び出される関数を指します。</span><span class="sxs-lookup"><span data-stu-id="b1404-117">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b1404-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1404-118">Related Sections</span></span>  

 [<span data-ttu-id="b1404-119">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="b1404-119">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="b1404-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b1404-120">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="b1404-121">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="b1404-121">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="b1404-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="b1404-122">Debugging Structures</span></span>](debugging-structures.md)
