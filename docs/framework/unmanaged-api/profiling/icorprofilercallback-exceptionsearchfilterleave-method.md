---
title: "Метод ICorProfilerCallback::ExceptionSearchFilterLeave"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFilterLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 41d4d9e9eca19356109afe38c2a28f1b5da2f682
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="8baf4-102">Метод ICorProfilerCallback::ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="8baf4-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="8baf4-103">Уведомляет профилировщик о том, что фильтр пользователей завершении выполнения.</span><span class="sxs-lookup"><span data-stu-id="8baf4-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8baf4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8baf4-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8baf4-105">Требования</span><span class="sxs-lookup"><span data-stu-id="8baf4-105">Requirements</span></span>  
 <span data-ttu-id="8baf4-106">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8baf4-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8baf4-107">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8baf4-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8baf4-108">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8baf4-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8baf4-109">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8baf4-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8baf4-110">См. также</span><span class="sxs-lookup"><span data-stu-id="8baf4-110">See Also</span></span>  
 [<span data-ttu-id="8baf4-111">Интерфейс ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="8baf4-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="8baf4-112">Метод ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="8baf4-112">ExceptionSearchFilterEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)