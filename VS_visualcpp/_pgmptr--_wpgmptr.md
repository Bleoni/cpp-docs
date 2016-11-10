---
title: "_pgmptr, _wpgmptr"
ms.custom: na
ms.date: 10/03/2016
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
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
caps.latest.revision: 14
manager: ghogen
translation.priority.ht: 
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
# _pgmptr, _wpgmptr
The path of the executable file. Deprecated; use [_get_pgmptr](../VS_visualcpp/_get_pgmptr.md) and [_get_wpgmptr](../VS_visualcpp/_get_wpgmptr.md).  
  
## Syntax  
  
```  
extern char *_pgmptr;  
extern wchar_t *_wpgmptr;  
```  
  
## Remarks  
 When a program is run from the command interpreter (Cmd.exe), `_pgmptr` is automatically initialized to the full path of the executable file. For example, if Hello.exe is in C:\BIN and C:\BIN is in the path, `_pgmptr` is set to C:\BIN\Hello.exe when you execute:  
  
```  
C> hello   
```  
  
 When a program is not run from the command line, `_pgmptr` might be initialized to the program name (the file's base name without the file name extension) or to a file name, relative path, or full path.  
  
 `_wpgmptr` is the wide-character counterpart of `_pgmptr` for use with programs that use `wmain`.  
  
### Generic-Text Routine Mappings  
  
|Tchar.h routine|_UNICODE and _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## Requirements  
  
|Variable|Required header|  
|--------------|---------------------|  
|`_pgmptr`, `_wpgmptr`|<stdlib.h>|  
  
## Example  
 The following program demonstrates the use of `_pgmptr`.  
  
```  
// crt_pgmptr.c  
// compile with: /W3  
// The following program demonstrates the use of _pgmptr.  
//  
#include <stdio.h>  
#include <stdlib.h>  
int main( void )  
{  
   printf("The full path of the executing program is : %Fs\n",   
     _pgmptr); // C4996  
   // Note: _pgmptr is deprecated; use _get_pgmptr instead  
}  
```  
  
 You could use `_wpgmptr` by changing `%Fs` to `%S` and `main` to `wmain`.  
  
## See Also  
 [Global Variables](../VS_visualcpp/Global-Variables.md)