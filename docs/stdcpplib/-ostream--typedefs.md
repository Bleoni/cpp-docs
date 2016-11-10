---
title: "&lt;ostream&gt; typedefs"
ms.custom: na
ms.date: "10/14/2016"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 10
---
# &lt;ostream&gt; typedefs
|||  
|-|-|  
|[ostream](#ostream)|[wostream](#wostream)|  
  
##  <a name="ostream"></a>  ostream  
 Creates a type from basic_ostream that is specialized on `char` and `char_traits` specialized on `char`.  
  
```
typedef basic_ostream<char, char_traits<char>> ostream;
```  
  
### Remarks  
 The type is a synonym for template class [basic_ostream](../stdcpplib/basic_ostream-class.md), specialized for elements of type `char` with default character traits.  
  
##  <a name="wostream"></a>  wostream  
 Creates a type from basic_ostream that is specialized on `wchar_t` and `char_traits` specialized on `wchar_t`.  
  
```
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```  
  
### Remarks  
 The type is a synonym for template class [basic_ostream](../stdcpplib/basic_ostream-class.md), specialized for elements of type `wchar_t` with default character traits.  
  
## See Also  
 [\<ostream>](../stdcpplib/-ostream-.md)
