---
description: '詳細情報: 方法:オーバーロードされたプロシージャを呼び出す (Visual Basic)'
title: '方法: オーバーロードされたプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 6a67a598bd4a42964fd8fc01bc22b1b919f5e2a9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472593"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="521b0-103">方法: オーバーロードされたプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="521b0-103">How to: Call an Overloaded Procedure (Visual Basic)</span></span>

<span data-ttu-id="521b0-104">プロシージャをオーバーロードする利点は、呼び出しの柔軟性にあります。</span><span class="sxs-lookup"><span data-stu-id="521b0-104">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="521b0-105">呼び出し元のコードは、プロシージャに渡す必要がある情報を取得し、渡す引数に関係なく、1 つのプロシージャ名を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="521b0-105">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="521b0-106">複数のバージョンが定義されているプロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="521b0-106">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="521b0-107">呼び出し元のコードで、プロシージャに渡すデータを決定します。</span><span class="sxs-lookup"><span data-stu-id="521b0-107">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="521b0-108">引数リストにデータを提示して、通常の方法でプロシージャ呼び出しを記述します。</span><span class="sxs-lookup"><span data-stu-id="521b0-108">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="521b0-109">引数が、プロシージャに対して定義されているいずれかのバージョンのパラメーター リストと一致していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="521b0-109">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="521b0-110">呼び出すプロシージャのバージョンを決定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="521b0-110">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="521b0-111">Visual Basic によって、引数リストと一致するバージョンに制御が渡されます。</span><span class="sxs-lookup"><span data-stu-id="521b0-111">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="521b0-112">次の例では、`post` プロシージャを呼び出します。これは「[方法:プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)」で定義されています。</span><span class="sxs-lookup"><span data-stu-id="521b0-112">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="521b0-113">顧客 ID を取得し、それが `String` か `Integer` かを判断して、どちらの場合でも同じプロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="521b0-113">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="521b0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="521b0-114">See also</span></span>

- [<span data-ttu-id="521b0-115">手順</span><span class="sxs-lookup"><span data-stu-id="521b0-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="521b0-116">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="521b0-116">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="521b0-117">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="521b0-117">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="521b0-118">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="521b0-118">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="521b0-119">方法: プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="521b0-119">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="521b0-120">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="521b0-120">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="521b0-121">方法: 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="521b0-121">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="521b0-122">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="521b0-122">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="521b0-123">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="521b0-123">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="521b0-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="521b0-124">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
