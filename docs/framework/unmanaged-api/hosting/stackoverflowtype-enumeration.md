---
title: "Перечисление StackOverflowType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowType
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowType
helpviewer_keywords: StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 64312398c95a33c2bbe136b1c4d03c06cb09aeef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="a410e-102">Перечисление StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="a410e-102">StackOverflowType Enumeration</span></span>
<span data-ttu-id="a410e-103">Содержит значения, которые указывают на основную причину события переполнения стека.</span><span class="sxs-lookup"><span data-stu-id="a410e-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a410e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a410e-104">Syntax</span></span>  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="a410e-105">Члены</span><span class="sxs-lookup"><span data-stu-id="a410e-105">Members</span></span>  
  
|<span data-ttu-id="a410e-106">Член</span><span class="sxs-lookup"><span data-stu-id="a410e-106">Member</span></span>|<span data-ttu-id="a410e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="a410e-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="a410e-108">Переполнение стека было вызвано подсистемой выполнения.</span><span class="sxs-lookup"><span data-stu-id="a410e-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="a410e-109">Переполнение стека было вызвано управляемого кода.</span><span class="sxs-lookup"><span data-stu-id="a410e-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="a410e-110">Переполнение стека было вызвано неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="a410e-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a410e-111">Примечания</span><span class="sxs-lookup"><span data-stu-id="a410e-111">Remarks</span></span>  
 <span data-ttu-id="a410e-112">Эти сведения передаются в узел посредством вызова [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="a410e-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a410e-113">Требования</span><span class="sxs-lookup"><span data-stu-id="a410e-113">Requirements</span></span>  
 <span data-ttu-id="a410e-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a410e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a410e-115">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a410e-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a410e-116">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a410e-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a410e-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a410e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a410e-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a410e-118">See Also</span></span>  
 [<span data-ttu-id="a410e-119">Перечисления размещения</span><span class="sxs-lookup"><span data-stu-id="a410e-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)