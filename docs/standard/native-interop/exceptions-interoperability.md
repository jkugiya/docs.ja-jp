---
description: '詳細情報: アンマネージド コードでの相互運用例外の処理'
title: 例外の相互運用性
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 3062aea2632771605c5a3c942c8471309e043f60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713196"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="2e41a-103">アンマネージド コードでの相互運用例外の処理</span><span class="sxs-lookup"><span data-stu-id="2e41a-103">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="2e41a-104">アンマネージド コードの例外の相互運用は、Windows プラットフォームでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2e41a-104">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="2e41a-105">Windows 以外のプラットフォームでは移植性の問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="2e41a-105">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="2e41a-106">Unix ABI には例外処理の定義がないため、マネージド コードでは、内部での例外メカニズムのしくみが認識されません。</span><span class="sxs-lookup"><span data-stu-id="2e41a-106">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="2e41a-107">そのため、例外が発生すると、予期しない動作やクラッシュが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e41a-107">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="2e41a-108">Setjmp と Longjmp の動作</span><span class="sxs-lookup"><span data-stu-id="2e41a-108">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="2e41a-109">`setjmp` および `longjmp` C 関数との相互運用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2e41a-109">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="2e41a-110">`longjmp` を使用して、マネージド フレームをスキップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2e41a-110">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="2e41a-111">詳しくは、[longjmp のドキュメント](/cpp/c-runtime-library/reference/longjmp)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e41a-111">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="2e41a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e41a-112">See also</span></span>

- [<span data-ttu-id="2e41a-113">例外</span><span class="sxs-lookup"><span data-stu-id="2e41a-113">Exceptions</span></span>](index.md)
- [<span data-ttu-id="2e41a-114">ネイティブ ライブラリとの相互運用</span><span class="sxs-lookup"><span data-stu-id="2e41a-114">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
