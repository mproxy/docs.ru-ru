---
title: "Метод ICLRStrongName::GetHashFromFileW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc7589e2a977502a3e75a95b8a065f45b8805072
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="d625e-102">Метод ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="d625e-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="d625e-103">Создает хэш содержимого файла, заданный строкой в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="d625e-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d625e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d625e-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d625e-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="d625e-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d625e-106">[in] Имя файла для хеширования Юникода.</span><span class="sxs-lookup"><span data-stu-id="d625e-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d625e-107">[in, out] Алгоритм, используемый при создании хеша.</span><span class="sxs-lookup"><span data-stu-id="d625e-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="d625e-108">Допустимыми являются алгоритмы, определенные интерфейсом CryptoAPI в Win32.</span><span class="sxs-lookup"><span data-stu-id="d625e-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="d625e-109">Если `piHashAlg` имеет значение 0, алгоритм по умолчанию используется CALG_SHA-1.</span><span class="sxs-lookup"><span data-stu-id="d625e-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d625e-110">[out] Массив байтов, содержащий созданный хеш.</span><span class="sxs-lookup"><span data-stu-id="d625e-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d625e-111">[in] Максимальный размер буфера, на который указывает `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d625e-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d625e-112">[out] Размер в байтах для `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d625e-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d625e-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d625e-113">Return Value</span></span>  
 <span data-ttu-id="d625e-114">`S_OK`Если метод успешно завершена; в противном случае — значение HRESULT, указывающее на сбой (в разделе [часто встречающихся значений HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) список).</span><span class="sxs-lookup"><span data-stu-id="d625e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d625e-115">Примечания</span><span class="sxs-lookup"><span data-stu-id="d625e-115">Remarks</span></span>  
 <span data-ttu-id="d625e-116">Этот метод является таким же, как [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , за исключением того, что спецификация имени файла является Юникода вместо ANSI.</span><span class="sxs-lookup"><span data-stu-id="d625e-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d625e-117">Требования</span><span class="sxs-lookup"><span data-stu-id="d625e-117">Requirements</span></span>  
 <span data-ttu-id="d625e-118">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d625e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d625e-119">**Заголовок:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d625e-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d625e-120">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d625e-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d625e-121">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d625e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d625e-122">См. также</span><span class="sxs-lookup"><span data-stu-id="d625e-122">See Also</span></span>  
 [<span data-ttu-id="d625e-123">Метод GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="d625e-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="d625e-124">Iclrstrongname-интерфейс</span><span class="sxs-lookup"><span data-stu-id="d625e-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)