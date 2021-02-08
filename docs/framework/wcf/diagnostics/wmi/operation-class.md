---
description: '詳細: Operation クラス'
title: Operation class
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 035c02bc05b7a64c5d15538001dbdcf2ec0b135b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803075"
---
# <a name="operation-class"></a><span data-ttu-id="d4358-103">Operation class</span><span class="sxs-lookup"><span data-stu-id="d4358-103">Operation class</span></span>

<span data-ttu-id="d4358-104">Operation</span><span class="sxs-lookup"><span data-stu-id="d4358-104">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4358-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4358-105">Syntax</span></span>  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d4358-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4358-106">Methods</span></span>  

 <span data-ttu-id="d4358-107">Operation クラスで定義されているメソッドはありせん。</span><span class="sxs-lookup"><span data-stu-id="d4358-107">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d4358-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d4358-108">Properties</span></span>  

 <span data-ttu-id="d4358-109">Operation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="d4358-109">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="d4358-110">操作</span><span class="sxs-lookup"><span data-stu-id="d4358-110">Action</span></span>  

 <span data-ttu-id="d4358-111">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="d4358-111">Data type: string</span></span>  
  
 <span data-ttu-id="d4358-112">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-113">要求メッセージの WS-Addressing 操作。</span><span class="sxs-lookup"><span data-stu-id="d4358-113">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="d4358-114">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="d4358-114">AsyncPattern</span></span>  

 <span data-ttu-id="d4358-115">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="d4358-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4358-116">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-117">`Begin`サービスコントラクトで [開始/終了山かっこ] と `End` [開始/終了山かっこ] の組み合わせを使用して、操作が非同期的に実装されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d4358-117">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="d4358-118">動作</span><span class="sxs-lookup"><span data-stu-id="d4358-118">Behaviors</span></span>  

 <span data-ttu-id="d4358-119">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="d4358-119">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="d4358-120">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-121">この操作に関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="d4358-121">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="d4358-122">IsCallback</span><span class="sxs-lookup"><span data-stu-id="d4358-122">IsCallback</span></span>  

 <span data-ttu-id="d4358-123">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="d4358-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4358-124">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-125">この操作がコールバック操作の場合、True。</span><span class="sxs-lookup"><span data-stu-id="d4358-125">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="d4358-126">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="d4358-126">IsInitiating</span></span>  

 <span data-ttu-id="d4358-127">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="d4358-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4358-128">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-129">メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4358-129">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="d4358-130">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="d4358-130">IsOneWay</span></span>  

 <span data-ttu-id="d4358-131">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="d4358-131">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4358-132">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-133">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4358-133">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="d4358-134">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="d4358-134">IsTerminating</span></span>  

 <span data-ttu-id="d4358-135">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="d4358-135">Data type: boolean</span></span>  
  
 <span data-ttu-id="d4358-136">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-137">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4358-137">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="d4358-138">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="d4358-138">MethodSignature</span></span>  

 <span data-ttu-id="d4358-139">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="d4358-139">Data type: string</span></span>  
  
 <span data-ttu-id="d4358-140">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-141">操作のメソッド署名。</span><span class="sxs-lookup"><span data-stu-id="d4358-141">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d4358-142">名前</span><span class="sxs-lookup"><span data-stu-id="d4358-142">Name</span></span>  

 <span data-ttu-id="d4358-143">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="d4358-143">Data type: string</span></span>  
  
 <span data-ttu-id="d4358-144">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-145">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="d4358-145">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="d4358-146">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="d4358-146">ParameterTypes</span></span>  

 <span data-ttu-id="d4358-147">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="d4358-147">Data type: string array</span></span>  
  
 <span data-ttu-id="d4358-148">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-149">操作のパラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="d4358-149">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="d4358-150">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="d4358-150">ReplyAction</span></span>  

 <span data-ttu-id="d4358-151">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="d4358-151">Data type: string</span></span>  
  
 <span data-ttu-id="d4358-152">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-153">操作の応答メッセージの SOAP アクションの値。</span><span class="sxs-lookup"><span data-stu-id="d4358-153">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="d4358-154">ReturnType</span><span class="sxs-lookup"><span data-stu-id="d4358-154">ReturnType</span></span>  

 <span data-ttu-id="d4358-155">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="d4358-155">Data type: string</span></span>  
  
 <span data-ttu-id="d4358-156">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="d4358-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d4358-157">操作の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="d4358-157">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4358-158">要件</span><span class="sxs-lookup"><span data-stu-id="d4358-158">Requirements</span></span>  
  
|<span data-ttu-id="d4358-159">MOF</span><span class="sxs-lookup"><span data-stu-id="d4358-159">MOF</span></span>|<span data-ttu-id="d4358-160">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="d4358-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d4358-161">名前空間</span><span class="sxs-lookup"><span data-stu-id="d4358-161">Namespace</span></span>|<span data-ttu-id="d4358-162">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="d4358-162">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4358-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4358-163">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
