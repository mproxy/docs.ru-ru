---
title: "Интерфейс IHostIoCompletionManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cbb4b87b57d4f5e11a9dab04d20dfb73170bb4a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanager-interface"></a>Интерфейс IHostIoCompletionManager
Предоставляет методы, позволяющие общеязыковой среды выполнения (CLR) для взаимодействия с порты завершения ввода-вывода, предоставленный средой размещения.  
  
## <a name="methods"></a>Методы  
  
|Метод|Описание:|  
|------------|-----------------|  
|[Метод Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Привязывает дескриптор к порту завершения ввода-вывода.|  
|[Метод CloseIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Закрывает порт, который был создан при помощи предыдущими вызовами метода `CreateIoCompletionPort`.|  
|[Метод CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Запросы на создание нового порта завершения ввода-вывода.|  
|[Метод GetAvailableThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Возвращает число потоков завершения ввода-вывода, которые в настоящий момент не обрабатывает запросы.|  
|[Метод GetHostOverlappedSize](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Получает размер любых пользовательских данных, которые должен узла для добавления запросов ввода-вывода.|  
|[Метод GetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Возвращает максимальное число потоков, которые основное приложение может выделить для обслуживания запросов ввода-вывода.|  
|[Метод GetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Получает минимальное количество потоков, предоставляемых основным приложением для обслуживания запросов ввода-вывода.|  
|[Метод InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Предоставляет основному приложению возможность инициализировать любые пользовательские данные о запроса ввода-вывода.|  
|[Метод SetCLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Предоставляет основному указатель интерфейса [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) экземпляра, реализуемых средой CLR.|  
|[Метод SetMaxThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Задает максимальное число потоков, выделяемых основным приложением для обслуживания запросов ввода-вывода.|  
|[Метод SetMinThreads](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Задает минимальное количество потоков, которые основное приложение должно выделить для завершения ввода-вывода.|  
  
## <a name="remarks"></a>Примечания  
 `IHostIoCompletionManager`соответствует `ICLRIoCompletionManager` интерфейс, реализованный средой CLR. Среда CLR вызывает методы `IHostIoCompletionManager` для привязки портов, которые предоставляет узел и узел вызывает методы дескрипторы `ICLRIoCompletionManager` для сообщения о завершении запросов ввода-вывода.  
  
## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** MSCorEE.h  
  
 **Библиотека:** включена как ресурс в MSCorEE.dll  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы размещения](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
