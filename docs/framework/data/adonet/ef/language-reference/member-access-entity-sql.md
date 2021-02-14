---
description: '詳細情報: . (メンバー アクセス) (Entity SQL)'
title: . (メンバー アクセス) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 94833d3525c7d17cadaef15065b3dcbdb43a6ded
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739379"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="4d835-105">.</span><span class="sxs-lookup"><span data-stu-id="4d835-105">.</span></span> <span data-ttu-id="4d835-106">(メンバー アクセス) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4d835-106">(Member Access) (Entity SQL)</span></span>

<span data-ttu-id="4d835-107">ドット演算子 (.) は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のメンバー アクセス演算子です。</span><span class="sxs-lookup"><span data-stu-id="4d835-107">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="4d835-108">メンバー アクセス演算子を使用すると、構造型概念モデル型のインスタンスのプロパティ値またはフィールド値を生成できます。</span><span class="sxs-lookup"><span data-stu-id="4d835-108">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d835-109">構文</span><span class="sxs-lookup"><span data-stu-id="4d835-109">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d835-110">引数</span><span class="sxs-lookup"><span data-stu-id="4d835-110">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4d835-111">構造型概念モデル型のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="4d835-111">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="4d835-112">オブジェクト インスタンスに属するプロパティまたはフィールド。</span><span class="sxs-lookup"><span data-stu-id="4d835-112">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d835-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="4d835-113">Remarks</span></span>  

 <span data-ttu-id="4d835-114">ドット (.) 演算子は、複合型またはエンティティ型のプロパティの抽出と同様に、レコードからフィールドを抽出するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="4d835-114">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="4d835-115">たとえば、Name 型の n が Person 型のメンバーであり、p が Person 型のインスタンスである場合、p.n は有効なメンバー アクセス式として Name 型の値を生成します。</span><span class="sxs-lookup"><span data-stu-id="4d835-115">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="4d835-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d835-116">See also</span></span>

- [<span data-ttu-id="4d835-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="4d835-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
