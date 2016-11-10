---
title: "CComAllocator Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComAllocator"
  - "ATL::CComAllocator"
  - "CComAllocator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComAllocator class"
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 14
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# CComAllocator Class
This class provides methods for managing memory using COM memory routines.  
  
## Syntax  
  
```
class CComAllocator
```  
  
## Members  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[CComAllocator::Allocate](../Topic/CComAllocator::Allocate.md)|Call this static method to allocate memory.|  
|[CComAllocator::Free](../Topic/CComAllocator::Free.md)|Call this static method to free allocated memory.|  
|[CComAllocator::Reallocate](../Topic/CComAllocator::Reallocate.md)|Call this static method to reallocate memory.|  
  
## Remarks  
 This class is used by [CComHeapPtr](../atl/ccomheapptr-class.md) to provide the COM memory allocation routines. The counterpart class, [CCRTAllocator](../atl/ccrtallocator-class.md), provides the same methods using CRT routines.  
  
## Requirements  
 **Header:** atlbase.h  
  
##  <a name="ccomallocator__allocate"></a>  CComAllocator::Allocate  
 Call this static function to allocate memory.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### Parameters  
 `nBytes`  
 The number of bytes to allocate.  
  
### Return Value  
 Returns a void pointer to the allocated space, or NULL if there is insufficient memory available.  
  
### Remarks  
 Allocates memory. See [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) for more details.  
  
##  <a name="ccomallocator__free"></a>  CComAllocator::Free  
 Call this static function to free allocated memory.  
  
```
static void Free(void* p) throw();
```  
  
### Parameters  
 `p`  
 Pointer to the allocated memory.  
  
### Remarks  
 Frees the allocated memory. See [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) for more details.  
  
##  <a name="ccomallocator__reallocate"></a>  CComAllocator::Reallocate  
 Call this static function to reallocate memory.  
  
```
static void* Reallocate(
    void*  p,  size_t nBytes) throw();
```  
  
### Parameters  
 `p`  
 Pointer to the allocated memory.  
  
 `nBytes`  
 The number of bytes to reallocate.  
  
### Return Value  
 Returns a void pointer to the allocated space, or NULL if there is insufficient memory  
  
### Remarks  
 Resizes the amount of allocated memory. See [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) for more details.  
  
## See Also  
 [CComHeapPtr Class](../atl/ccomheapptr-class.md)   
 [CCRTAllocator Class](../atl/ccrtallocator-class.md)   
 [Class Overview](../atl/atl-class-overview.md)
