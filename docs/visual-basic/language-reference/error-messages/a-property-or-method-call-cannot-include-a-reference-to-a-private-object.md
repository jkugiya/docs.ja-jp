---
description: '詳細情報: プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。'
title: プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 8fe570c9ed789a5bac36aafa9b1ec2f507a55d51
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797199"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="88cbc-103">プロパティまたはメソッドの呼び出しには、引数または戻り値としてプライベート オブジェクトへの参照を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="88cbc-103">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="88cbc-104">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="88cbc-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="88cbc-105">クライアントが、アウトプロセス コンポーネントのプロパティまたはメソッドを呼び出し、引数の 1 つとしてプライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="88cbc-105">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>

- <span data-ttu-id="88cbc-106">アウトプロセス コンポーネントがクライアントに対してコールバック メソッドを呼び出し、プライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="88cbc-106">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>

- <span data-ttu-id="88cbc-107">アウトプロセス コンポーネントが、それ自身が発生させているイベントの引数として、プライベート オブジェクトへの参照を渡そうとしました。</span><span class="sxs-lookup"><span data-stu-id="88cbc-107">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>

- <span data-ttu-id="88cbc-108">クライアントが、それ自身が処理しているイベントの `ByRef` 引数に、プライベート オブジェクト参照を代入しようとしました。</span><span class="sxs-lookup"><span data-stu-id="88cbc-108">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="88cbc-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="88cbc-109">To correct this error</span></span>

- <span data-ttu-id="88cbc-110">参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="88cbc-110">Remove the reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="88cbc-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="88cbc-111">See also</span></span>

- [<span data-ttu-id="88cbc-112">Private</span><span class="sxs-lookup"><span data-stu-id="88cbc-112">Private</span></span>](../modifiers/private.md)
