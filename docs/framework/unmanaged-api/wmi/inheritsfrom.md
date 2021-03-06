---
title: "Функция раскрывшемся списке (Справочник по неуправляемым API)"
description: "Функция раскрывшемся списке определяет, является ли класс или экземпляр является производным от определенного родительского класса."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0dce964829399e6761152a8ff424671b47cc6eb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="inheritsfrom-function"></a>Функция раскрывшемся списке
Определяет, является ли текущего класса или экземпляра является производным от класса-родителя указанного.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Синтаксис  
  
```
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>Параметры

`vFunc`  
[in] Этот параметр не используется.

`ptr`  
[in] Указатель на [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) экземпляра.

`wszAncestor`  
[in] Имя класса. `wszAncestor`должен указывать на допустимый `LPCWSTR`.

## <a name="return-value"></a>Возвращаемое значение

Следующие значения, возвращаемые этой функцией, определяются в *WbemCli.h* файла заголовка, или их можно определить как константы в коде:

|Константа  |Значение  |Описание  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Наследует текущий объект `wszAncestor`.  |
| `WBEM_S_FALSE` | 1 | Текущий объект не является производным от `wszAncestor`. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Свойство `wszAncestor` имеет значение `null`. |
  
## <a name="remarks"></a>Примечания

Эта функция создает оболочку для вызова [IWbemClassObject::InheritsFrom](https://msdn.microsoft.com/library/aa391452(v=vs.85).aspx) метод.

## <a name="requirements"></a>Требования  
 **Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Заголовок:** WMINet_Utils.idl  
  
 **Версии платформы .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>См. также  
[WMI и счетчиков производительности (Справочник по неуправляемым API)](index.md)
