---
title: "_ismbbpunct, _ismbbpunct_l"
ms.custom: na
ms.date: 10/06/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - _ismbbpunct
  - _ismbbpunct_l
apilocation: 
  - msvcrt.dll
  - msvcr80.dll
  - msvcr90.dll
  - msvcr100.dll
  - msvcr100_clr0400.dll
  - msvcr110.dll
  - msvcr110_clr0400.dll
  - msvcr120.dll
  - msvcr120_clr0400.dll
  - ucrtbase.dll
  - api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
caps.latest.revision: 20
manager: ghogen
translation.priority.mt: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# _ismbbpunct, _ismbbpunct_l
Determines whether a particular character is a punctuation character.  
  
## Syntax  
  
```  
int _ismbbpunct(  
   unsigned int c   
);  
int _ismbbpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parameters  
 `c`  
 Integer to be tested.  
  
 `locale`  
 Locale to use.  
  
## Return Value  
 `_ismbbpunct` returns a nonzero value if the integer `c` is a non-ASCII punctuation symbol. `_ismbbpunct` uses the current locale for any locale-dependent character settings. `_ismbbpunct_l` is identical except that it uses the locale that's passed in. For more information, see [Locale](../VS_visualcpp/Locale.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_ismbbpunct`|<mbctype.h>|  
|`_ismbbpunct_l`|<mbctype.h>|  
  
 For more compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md).  
  
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## See Also  
 [Byte Classification](../VS_visualcpp/Byte-Classification.md)   
 [_ismbb Routines](../VS_visualcpp/_ismbb-Routines.md)