---
title: "CreateClassFactory Function"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
caps.latest.revision: 2
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# CreateClassFactory Function
Creates a factory that produces instances of the specified class.  
  
## Syntax  
  
```cpp  
  
template<typename Factory>  
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(  
   _In_ unsigned int *flags,   
   _In_ const CreatorMap* entry,   
   REFIID riid,   
   _Outptr_ IUnknown **ppFactory  
) throw();  
  
```  
  
#### Parameters  
 `flags`  
 A combination of one or more [RuntimeClassType](../VS_visualcpp/RuntimeClassType-Enumeration.md) enumeration values.  
  
 `entry`  
 Pointer to a [CreatorMap](../VS_visualcpp/CreatorMap-Structure.md) that contains initialization and registration information about parameter `riid`.  
  
 `riid`  
 Reference to an interface ID.  
  
 `ppFactory`  
 If this operation completes successfully, a pointer to a class factory.  
  
## Return Value  
 S_OK if successful; otherwise, an HRESULT that indicates the error.  
  
## Remarks  
 An assert error is emitted if template parameter `Factory` doesn't derive from interface IClassFactory.  
  
## Requirements  
 **Header:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## See Also  
 [Microsoft::WRL::Wrappers::Details Namespace](../VS_visualcpp/Microsoft--WRL--Wrappers--Details-Namespace.md)