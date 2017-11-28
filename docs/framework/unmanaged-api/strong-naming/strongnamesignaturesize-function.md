---
title: "Функция StrongNameSignatureSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureSize
helpviewer_keywords: StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7944763f1c1379228e715b18b563e7aa776fedac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="adc98-102">Функция StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="adc98-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="adc98-103">Возвращает размер подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="adc98-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="adc98-104">`StrongNameSignatureSize`обычно используется компиляторами, чтобы определить, сколько места для резервирования в файле, при создании сборки с отложенной подписью.</span><span class="sxs-lookup"><span data-stu-id="adc98-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="adc98-105">Эта функция устарела.</span><span class="sxs-lookup"><span data-stu-id="adc98-105">This function has been deprecated.</span></span> <span data-ttu-id="adc98-106">Используйте [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) метод вместо него.</span><span class="sxs-lookup"><span data-stu-id="adc98-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc98-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="adc98-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="adc98-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="adc98-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="adc98-109">[in] Структура типа [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) , содержащая открытую часть пары ключей, используемой для создания подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="adc98-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="adc98-110">[in] Размер в байтах для `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="adc98-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="adc98-111">[in] Число байтов, необходимое для хранения подписи строгого имени.</span><span class="sxs-lookup"><span data-stu-id="adc98-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adc98-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="adc98-112">Return Value</span></span>  
 <span data-ttu-id="adc98-113">`true`При успешном завершении; в противном случае `false`.</span><span class="sxs-lookup"><span data-stu-id="adc98-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adc98-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="adc98-114">Remarks</span></span>  
 <span data-ttu-id="adc98-115">Если `StrongNameSignatureSize` функция не завершена, вызовите [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) функции для получения последнего формируемой ошибки.</span><span class="sxs-lookup"><span data-stu-id="adc98-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adc98-116">Требования</span><span class="sxs-lookup"><span data-stu-id="adc98-116">Requirements</span></span>  
 <span data-ttu-id="adc98-117">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adc98-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adc98-118">**Заголовок:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="adc98-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="adc98-119">**Библиотека:** включена как ресурс в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adc98-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adc98-120">**Версии платформы .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adc98-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc98-121">См. также</span><span class="sxs-lookup"><span data-stu-id="adc98-121">See Also</span></span>  
 [<span data-ttu-id="adc98-122">Метод StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="adc98-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [<span data-ttu-id="adc98-123">Iclrstrongname-интерфейс</span><span class="sxs-lookup"><span data-stu-id="adc98-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)