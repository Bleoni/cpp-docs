---
title: "div"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
apiname: 
  - "div"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "div"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "div function"
  - "quotients, computing"
  - "quotients"
  - "dividing integers"
  - "remainder computing"
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 13
ms.author: "corob"
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
# div
Computes the quotient and the remainder of two integer values.  
  
## Syntax  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### Parameters  
 `numer`  
 The numerator.  
  
 `denom`  
 The denominator.  
  
## Return Value  
 `div` called by using arguments of type `int` returns a structure of type `div_t`, which comprises the quotient and the remainder. The return value of the overload with arguments of type `long` is `ldiv_t`. Both `div_t` and `ldiv_t` are defined in STDLIB.H.  
  
## Remarks  
 The `div` function divides `numer` by `denom` and thereby computes the quotient and the remainder. The [div_t](../crt/standard-types.md) structure contains the quotient, `int``quot`, and the remainder, `int``rem`. The sign of the quotient is the same as that of the mathematical quotient. Its absolute value is the largest integer that is less than the absolute value of the mathematical quotient. If the denominator is 0, the program terminates with an error message.  
  
 The overloads that take arguments of type `long` or `long long` are only available to C++ code. The return type [ldiv_t](../crt/standard-types.md) contains the members `long``quot` and `long``rem`, and the return type [lldiv_t](../crt/standard-types.md) contains the members `long long quot` and `long long rem`, which have the same meanings as the members of `div_t`.  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`div`|\<stdlib.h>|  
  
 For additional compatibility information, see [Compatibility](../crt/compatibility.md).  
  
## Example  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
 **x is 876, y is 13**  
**The quotient is 67, and the remainder is 5**   
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## See Also  
 [Floating-Point Support](../crt/floating-point-support.md)   
 [ldiv, lldiv](../crt/ldiv--lldiv.md)   
 [imaxdiv](../crt/imaxdiv.md)