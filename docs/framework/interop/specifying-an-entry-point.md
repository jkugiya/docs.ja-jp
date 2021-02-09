---
title: エントリ ポイントの指定
description: DLL で関数の場所を特定するエントリ ポイントを指定する方法について説明します。 エントリ ポイントを別の名前にマッピングすることで関数の名前を変更できます。
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: a8a45513469c5ee1ec24aae12b02877c9a431513
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99426945"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="9e8f0-104">エントリ ポイントの指定</span><span class="sxs-lookup"><span data-stu-id="9e8f0-104">Specifying an Entry Point</span></span>

<span data-ttu-id="9e8f0-105">エントリ ポイントは、DLL 内の関数の位置を識別します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="9e8f0-106">マネージド プロジェクト内では、対象となる関数の元の名前または序数エントリ ポイントによって、その関数が相互運用の境界にまたがって識別されます。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="9e8f0-107">また、エントリ ポイントを別の名前に割り当てて、関数の名前を事実上変更できます。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="9e8f0-108">DLL 関数の名前を変更する理由を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="9e8f0-109">大文字と小文字が区別される API 関数名を使わないようにするため</span><span class="sxs-lookup"><span data-stu-id="9e8f0-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="9e8f0-110">既存の名前付け標準に合わせるため</span><span class="sxs-lookup"><span data-stu-id="9e8f0-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="9e8f0-111">異なるデータ型を受け取る複数の関数を共存させるため (同じ DLL 関数の複数のバージョンを宣言することによって)</span><span class="sxs-lookup"><span data-stu-id="9e8f0-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="9e8f0-112">ANSI バージョンと Unicode バージョンを持つ API の使用を簡単にするため</span><span class="sxs-lookup"><span data-stu-id="9e8f0-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="9e8f0-113">このトピックでは、マネージド コード内の DLL 関数の名前を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="9e8f0-114">Visual Basic での関数名の変更</span><span class="sxs-lookup"><span data-stu-id="9e8f0-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="9e8f0-115">Visual Basic で <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> フィールドを設定するには、**Declare** ステートメントで **Function** キーワードを使います。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="9e8f0-116">基本的な宣言を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="9e8f0-117">定義に **Alias** キーワードを含めることで、**MessageBox** エントリ ポイントを **MsgBox** に置き換えることができます。その例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="9e8f0-118">どちらの例でも、**Auto** キーワードを使って、エントリ ポイントの文字セットのバージョンを指定する手間を省いています。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="9e8f0-119">文字セットの選択の詳細については、「[文字セットの指定](specifying-a-character-set.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="9e8f0-120">C# および C++ での関数名の変更</span><span class="sxs-lookup"><span data-stu-id="9e8f0-120">Renaming a Function in C# and C++</span></span>  

 <span data-ttu-id="9e8f0-121">DLL 関数を名前または序数で指定するには、<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> フィールドを使います。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="9e8f0-122">メソッド定義内の関数の名前が DLL 内のエントリ ポイントと同じである場合は、その関数を **EntryPoint** フィールドで明示的に識別する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="9e8f0-123">同じでない場合は、次のいずれかの属性書式を使って、名前または序数を指示します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="9e8f0-124">序数の前にシャープ記号 (#) を付ける必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="9e8f0-125">**EntryPoint** フィールドを使ってコード内の **MessageBoxA** を **MsgBox** に置き換える方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9e8f0-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MsgBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="9e8f0-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e8f0-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="9e8f0-127">マネージド コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="9e8f0-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="9e8f0-128">プラットフォーム呼び出しの例</span><span class="sxs-lookup"><span data-stu-id="9e8f0-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="9e8f0-129">プラットフォーム呼び出しによるデータのマーシャリング</span><span class="sxs-lookup"><span data-stu-id="9e8f0-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
