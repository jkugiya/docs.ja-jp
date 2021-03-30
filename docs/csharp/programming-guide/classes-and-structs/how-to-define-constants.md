---
title: C# で定数を定義する方法
description: C# で定数を定義する方法について説明します。この定数はフィールドであり、コンパイル時にその値が設定されます。 定数を使用して、特殊な値にわかりやすい名前を提供します。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 54b8a335279c8bb81bc75d182ec653e434ab45a0
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636858"
---
# <a name="how-to-define-constants-in-c"></a>C\# で定数を定義する方法

定数とは、値がコンパイル時に設定され、変更できないフィールドです。 定数を使用して、特殊な値の数値リテラル ("マジック ナンバー") の代わりにわかりやすい名前を提供します。  
  
> [!NOTE]
> C# では、C と C++ で通常使用される方法で、[#define](../../language-reference/preprocessor-directives.md#defining-symbols) プリプロセッサ ディレクティブを使用して定数を定義することはできません。  
  
 整数型 (`int`、`byte` など) の定数値を定義するには、列挙型を使用します。 詳細については、「[enum](../../language-reference/builtin-types/enum.md)」を参照してください。  
  
 整数型以外の定数を定義する 1 つの方法は、`Constants` という名前の 1 つの静的クラスにそれらをグループ化することです。 これを行うには、次の例に示すように、クラス名の前に定数へのすべての参照を付ける必要があります。  
  
## <a name="example"></a>例  

 [!code-csharp[constants](snippets/how-to-define-constants/Program.cs)]  
  
 クラス名修飾子を使用すると、定数を使用するユーザーは、それが定数であり、変更できないことがわかります。  
  
## <a name="see-also"></a>関連項目

- [クラスと構造体](./index.md)
