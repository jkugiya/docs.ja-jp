---
description: 詳細については、「CorDebugRegister 列挙型」を参照してください。
title: CorDebugRegister 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
ms.openlocfilehash: 7a5dc771a239a82448f898e2f518e920993ec35a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661871"
---
# <a name="cordebugregister-enumeration"></a><span data-ttu-id="28289-103">CorDebugRegister 列挙型</span><span class="sxs-lookup"><span data-stu-id="28289-103">CorDebugRegister Enumeration</span></span>

<span data-ttu-id="28289-104">指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="28289-104">Specifies the registers associated with a given processor architecture.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28289-105">構文</span><span class="sxs-lookup"><span data-stu-id="28289-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a><span data-ttu-id="28289-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="28289-106">Members</span></span>  
  
|<span data-ttu-id="28289-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="28289-107">Member</span></span>|<span data-ttu-id="28289-108">説明</span><span class="sxs-lookup"><span data-stu-id="28289-108">Description</span></span>|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|<span data-ttu-id="28289-109">すべてのプロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-109">An instruction pointer register on any processor.</span></span>|  
|`REGISTER_STACK_POINTER`|<span data-ttu-id="28289-110">すべてのプロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-110">A stack pointer register on any processor.</span></span>|  
|`REGISTER_FRAME_POINTER`|<span data-ttu-id="28289-111">すべてのプロセッサ上のフレーム ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-111">A frame pointer register on any processor.</span></span>|  
|`REGISTER_X86_EIP`|<span data-ttu-id="28289-112">x86 プロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-112">The instruction pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESP`|<span data-ttu-id="28289-113">x86 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-113">The stack pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBP`|<span data-ttu-id="28289-114">x86 プロセッサ上の基本ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-114">The base pointer register on the x86 processor.</span></span>|  
|`REGISTER_X86_EAX`|<span data-ttu-id="28289-115">x86 プロセッサ上の A データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-115">The A data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ECX`|<span data-ttu-id="28289-116">x86 プロセッサ上の C データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-116">The C data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDX`|<span data-ttu-id="28289-117">x86 プロセッサ上の D データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-117">The D data register on the x86 processor.</span></span>|  
|`REGISTER_X86_EBX`|<span data-ttu-id="28289-118">x86 プロセッサ上の B データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-118">The B data register on the x86 processor.</span></span>|  
|`REGISTER_X86_ESI`|<span data-ttu-id="28289-119">x86 プロセッサ上のソース インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-119">The source index register on the x86 processor.</span></span>|  
|`REGISTER_X86_EDI`|<span data-ttu-id="28289-120">x86 プロセッサ上のターゲット インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-120">The destination index register on the x86 processor.</span></span>|  
|`REGISTER_X86_FPSTACK_0`|<span data-ttu-id="28289-121">x86 浮動小数点 (FP) プロセッサ上のスタック レジスタ 0。</span><span class="sxs-lookup"><span data-stu-id="28289-121">The stack register 0 on the x86 floating-point (FP) processor.</span></span>|  
|`REGISTER_X86_FPSTACK_1`|<span data-ttu-id="28289-122">x86 FP プロセッサ上の #1 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-122">The #1 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_2`|<span data-ttu-id="28289-123">x86 FP プロセッサ上の #2 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-123">The #2 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_3`|<span data-ttu-id="28289-124">x86 FP プロセッサ上の #3 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-124">The #3 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_4`|<span data-ttu-id="28289-125">x86 FP プロセッサ上の #4 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-125">The #4 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_5`|<span data-ttu-id="28289-126">x86 FP プロセッサ上の #5 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-126">The #5 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_6`|<span data-ttu-id="28289-127">x86 FP プロセッサ上の #6 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-127">The #6 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_X86_FPSTACK_7`|<span data-ttu-id="28289-128">x86 FP プロセッサ上の #7 スタック レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-128">The #7 stack register on the x86 FP processor.</span></span>|  
|`REGISTER_AMD64_RIP`|<span data-ttu-id="28289-129">AMD64 プロセッサ上の命令ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-129">The instruction pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSP`|<span data-ttu-id="28289-130">AMD64 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-130">The stack pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBP`|<span data-ttu-id="28289-131">AMD64 プロセッサ上の基本ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-131">The base pointer register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RAX`|<span data-ttu-id="28289-132">AMD64 プロセッサ上の A データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-132">The A data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RCX`|<span data-ttu-id="28289-133">AMD64 プロセッサ上の C データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-133">The C data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDX`|<span data-ttu-id="28289-134">AMD64 プロセッサ上の D データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-134">The D data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RBX`|<span data-ttu-id="28289-135">AMD64 プロセッサ上の B データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-135">The B data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RSI`|<span data-ttu-id="28289-136">AMD64 プロセッサ上のソース インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-136">The source index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_RDI`|<span data-ttu-id="28289-137">AMD64 プロセッサ上のターゲット インデックス レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-137">The destination index register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R8`|<span data-ttu-id="28289-138">AMD64 プロセッサ上の #8 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-138">The #8 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R9`|<span data-ttu-id="28289-139">AMD64 プロセッサ上の #9 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-139">The #9 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R10`|<span data-ttu-id="28289-140">AMD64 プロセッサ上の #10 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-140">The #10 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R11`|<span data-ttu-id="28289-141">AMD64 プロセッサ上の #11 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-141">The #11 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R12`|<span data-ttu-id="28289-142">AMD64 プロセッサ上の #12 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-142">The #12 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R13`|<span data-ttu-id="28289-143">AMD64 プロセッサ上の #13 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-143">The #13 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R14`|<span data-ttu-id="28289-144">AMD64 プロセッサ上の #14 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-144">The #14 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_R15`|<span data-ttu-id="28289-145">AMD64 プロセッサ上の #15 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-145">The #15 data register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM0`|<span data-ttu-id="28289-146">AMD64 プロセッサ上の #0 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-146">The #0 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM1`|<span data-ttu-id="28289-147">AMD64 プロセッサ上の #1 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-147">The #1 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM2`|<span data-ttu-id="28289-148">AMD64 プロセッサ上の #2 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-148">The #2 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM3`|<span data-ttu-id="28289-149">AMD64 プロセッサ上の #3 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-149">The #3 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM4`|<span data-ttu-id="28289-150">AMD64 プロセッサ上の #4 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-150">The #4 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM5`|<span data-ttu-id="28289-151">AMD64 プロセッサ上の #5 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-151">The #5 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM6`|<span data-ttu-id="28289-152">AMD64 プロセッサ上の #6 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-152">The #6 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM7`|<span data-ttu-id="28289-153">AMD64 プロセッサ上の #7 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-153">The #7 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM8`|<span data-ttu-id="28289-154">AMD64 プロセッサ上の #8 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-154">The #8 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM9`|<span data-ttu-id="28289-155">AMD64 プロセッサ上の #9 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-155">The #9 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM10`|<span data-ttu-id="28289-156">AMD64 プロセッサ上の #10 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-156">The #10 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM11`|<span data-ttu-id="28289-157">AMD64 プロセッサ上の #11 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-157">The #11 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM12`|<span data-ttu-id="28289-158">AMD64 プロセッサ上の #12 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-158">The #12 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM13`|<span data-ttu-id="28289-159">AMD64 プロセッサ上の #13 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-159">The #13 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM14`|<span data-ttu-id="28289-160">AMD64 プロセッサ上の #14 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-160">The #14 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_AMD64_XMM15`|<span data-ttu-id="28289-161">AMD64 プロセッサ上の #15 マルチメディア レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-161">The #15 multimedia register on the AMD64 processor.</span></span>|  
|`REGISTER_IA64_BSP`|<span data-ttu-id="28289-162">IA-64 プロセッサ上のスタック ポインター レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-162">The stack pointer register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_R0`|<span data-ttu-id="28289-163">IA-64 プロセッサ上の #0 データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-163">The #0 data register on the IA-64 processor.</span></span>|  
|`REGISTER_IA64_F0`|<span data-ttu-id="28289-164">IA-64 プロセッサ上の #0 FP データ レジスタ。</span><span class="sxs-lookup"><span data-stu-id="28289-164">The #0 FP data register on the IA-64 processor.</span></span>|  
|`REGISTER_ARM_PC`|<span data-ttu-id="28289-165">ARM プロセッサ上のプログラム カウンター レジスタ (R15)。</span><span class="sxs-lookup"><span data-stu-id="28289-165">The program counter register (R15) on the ARM processor.</span></span>|  
|`REGISTER_ARM_SP`|<span data-ttu-id="28289-166">ARM プロセッサ上のスタック ポインター レジスタ (R13)。</span><span class="sxs-lookup"><span data-stu-id="28289-166">The stack pointer register (R13) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R0`|<span data-ttu-id="28289-167">ARM プロセッサ上のデータ レジスタ R0。</span><span class="sxs-lookup"><span data-stu-id="28289-167">Data register R0 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R1`|<span data-ttu-id="28289-168">ARM プロセッサ上のデータ レジスタ R1。</span><span class="sxs-lookup"><span data-stu-id="28289-168">Data register R1 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R2`|<span data-ttu-id="28289-169">ARM プロセッサ上のデータ レジスタ R2。</span><span class="sxs-lookup"><span data-stu-id="28289-169">Data register R2 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R3`|<span data-ttu-id="28289-170">ARM プロセッサ上のデータ レジスタ R3。</span><span class="sxs-lookup"><span data-stu-id="28289-170">Data register R3 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R4`|<span data-ttu-id="28289-171">ARM プロセッサ上のレジスタ R4。</span><span class="sxs-lookup"><span data-stu-id="28289-171">Register R4 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R5`|<span data-ttu-id="28289-172">ARM プロセッサ上のレジスタ R5。</span><span class="sxs-lookup"><span data-stu-id="28289-172">Register R5 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R6`|<span data-ttu-id="28289-173">ARM プロセッサ上のレジスタ R6。</span><span class="sxs-lookup"><span data-stu-id="28289-173">Register R6 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R7`|<span data-ttu-id="28289-174">ARM プロセッサ上のレジスタ R7 (THUMB フレーム ポインター)。</span><span class="sxs-lookup"><span data-stu-id="28289-174">Register R7 (the THUMB frame pointer) on the ARM processor.</span></span>|  
|`REGISTER_ARM_R8`|<span data-ttu-id="28289-175">ARM プロセッサ上のレジスタ R8。</span><span class="sxs-lookup"><span data-stu-id="28289-175">Register R8 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R9`|<span data-ttu-id="28289-176">ARM プロセッサ上のレジスタ R9。</span><span class="sxs-lookup"><span data-stu-id="28289-176">Register R9 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R10`|<span data-ttu-id="28289-177">ARM プロセッサ上のレジスタ R10。</span><span class="sxs-lookup"><span data-stu-id="28289-177">Register R10 on the ARM processor.</span></span>|  
|`REGISTER_ARM_R11`|<span data-ttu-id="28289-178">ARM プロセッサ上のフレーム ポインター。</span><span class="sxs-lookup"><span data-stu-id="28289-178">The frame pointer on the ARM processor.</span></span>|  
|`REGISTER_ARM_R12`|<span data-ttu-id="28289-179">ARM プロセッサ上のレジスタ R12。</span><span class="sxs-lookup"><span data-stu-id="28289-179">Register R12 on the ARM processor.</span></span>|  
|`REGISTER_ARM_LR`|<span data-ttu-id="28289-180">ARM プロセッサ上のリンク レジスタ (R14)。</span><span class="sxs-lookup"><span data-stu-id="28289-180">The link register (R14) on the ARM processor.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28289-181">解説</span><span class="sxs-lookup"><span data-stu-id="28289-181">Remarks</span></span>  

 <span data-ttu-id="28289-182">IA-64 プロセッサには、128 個の汎用データ レジスタおよび 128 個の浮動小数点データ レジスタがありますが、提供されているのは `REGISTER_IA64_R0` および `REGISTER_IA64_F0` の値のみです。</span><span class="sxs-lookup"><span data-stu-id="28289-182">There are 128 general-purpose data registers and 128 floating-point data registers on the IA-64 processor, but only values `REGISTER_IA64_R0` and `REGISTER_IA64_F0` are provided.</span></span> <span data-ttu-id="28289-183">その他の値は、次のように判断されます。</span><span class="sxs-lookup"><span data-stu-id="28289-183">The other values can be determined as follows:</span></span>  
  
- <span data-ttu-id="28289-184">IA-64 プロセッサ上の #1 データ レジスタから #127 データ レジスタに対応する、`REGISTER_IA64_R0` から `REGISTER_IA64_R1` までの値の `REGISTER_IA64_R127` にレジスタ番号を追加します。</span><span class="sxs-lookup"><span data-stu-id="28289-184">Add the register number to `REGISTER_IA64_R0` for values `REGISTER_IA64_R1` through `REGISTER_IA64_R127`, which correspond to the #1 data register through the #127 data register on the IA-64 processor.</span></span>  
  
- <span data-ttu-id="28289-185">IA-64 プロセッサ上の #1 FP データ レジスタから #127 FP データ レジスタに対応する、`REGISTER_IA64_F0` から `REGISTER_IA64_F1` までの値の `REGISTER_IA64_F127` にレジスタ番号を追加します。</span><span class="sxs-lookup"><span data-stu-id="28289-185">Add the register number to `REGISTER_IA64_F0` for values `REGISTER_IA64_F1` through `REGISTER_IA64_F127`, which correspond to the #1 FP data register through the #127 FP data register on the IA-64 processor.</span></span>  
  
 <span data-ttu-id="28289-186">たとえば、IA-64 プロセッサ上で #83 データ レジスタを指定する必要がある場合、`REGISTER_IA64_R0` + 83 を使用します。</span><span class="sxs-lookup"><span data-stu-id="28289-186">For example, if you need to specify the #83 data register on the IA-64 processor, use `REGISTER_IA64_R0` + 83.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28289-187">要件</span><span class="sxs-lookup"><span data-stu-id="28289-187">Requirements</span></span>  

 <span data-ttu-id="28289-188">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28289-188">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28289-189">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28289-189">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28289-190">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28289-190">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28289-191">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28289-191">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28289-192">関連項目</span><span class="sxs-lookup"><span data-stu-id="28289-192">See also</span></span>

- [<span data-ttu-id="28289-193">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="28289-193">Debugging Enumerations</span></span>](debugging-enumerations.md)
