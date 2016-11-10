---
title: "sscanf, _sscanf_l, swscanf, _swscanf_l"
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
apiname: 
  - swscanf
  - sscanf
  - _sscanf_l
  - _swscanf_l
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
apitype: DLLExport
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
caps.latest.revision: 24
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
# sscanf, _sscanf_l, swscanf, _swscanf_l
Read formatted data from a string. More secure versions of these functions are available; see [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](../VS_visualcpp/sscanf_s--_sscanf_s_l--swscanf_s--_swscanf_s_l.md).  
  
## Syntax  
  
```  
int sscanf(  
   const char *buffer,  
   const char *format [,  
   argument ] ...   
);  
int _sscanf_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...   
);  
int swscanf(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...   
);  
int _swscanf_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...   
);  
```  
  
#### Parameters  
 `buffer`  
 Stored data  
  
 `format`  
 Format-control string. For more information, see [Format Specifications](../VS_visualcpp/Format-Specification-Fields--scanf-and-wscanf-Functions.md).  
  
 `argument`  
 Optional arguments  
  
 `locale`  
 The locale to use  
  
## Return Value  
 Each of these functions returns the number of fields successfully converted and assigned; the return value does not include fields that were read but not assigned. A return value of 0 indicates that no fields were assigned. The return value is `EOF` for an error or if the end of the string is reached before the first conversion.  
  
 If `buffer` or `format` is a `NULL` pointer, the invalid parameter handler is invoked, as described in [Parameter Validation](../VS_visualcpp/Parameter-Validation.md). If execution is allowed to continue, these functions return -1 and set `errno` to `EINVAL`.  
  
 For information on these and other error codes, see [_doserrno, errno, _sys_errlist, and _sys_nerr](../VS_visualcpp/errno--_doserrno--_sys_errlist--and-_sys_nerr.md).  
  
## Remarks  
 The `sscanf` function reads data from `buffer` into the location given by each `argument`. Every `argument` must be a pointer to a variable with a type that corresponds to a type specifier in `format`. The `format` argument controls the interpretation of the input fields and has the same form and function as the `format` argument for the `scanf` function. If copying takes place between strings that overlap, the behavior is undefined.  
  
> [!IMPORTANT]
>  When reading a string with `sscanf`, always specify a width for the `%s` format (for example, `"%32s"` instead of `"%s"`); otherwise, improperly formatted input can easily cause a buffer overrun.  
  
 `swscanf` is a wide-character version of `sscanf`; the arguments to `swscanf` are wide-character strings. `sscanf`does not handle multibyte hexadecimal characters. `swscanf` does not handle Unicode full-width hexadecimal or "compatibility zone" characters. Otherwise, `swscanf` and `sscanf` behave identically.  
  
 The versions of these functions with the `_l` suffix are identical except that they use the locale parameter passed in instead of the current thread locale.  
  
### Generic-Text Routine Mappings  
  
|TCHAR.H routine|_UNICODE & _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stscanf`|`sscanf`|`sscanf`|`swscanf`|  
|`_stscanf_l`|`_sscanf_l`|`_sscanf_l`|`_swscanf_l`|  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`sscanf`, `_sscanf_l`|<stdio.h>|  
|`swscanf`, `_swscanf_l`|<stdio.h> or <wchar.h>|  
  
 For additional compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md) in the Introduction.  
  
## Example  
  
```  
// crt_sscanf.c  
// compile with: /W3  
// This program uses sscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string:  
   sscanf( tokenstring, "%80s", s ); // C4996  
   sscanf( tokenstring, "%c", &c );  // C4996  
   sscanf( tokenstring, "%d", &i );  // C4996  
   sscanf( tokenstring, "%f", &fp ); // C4996  
   // Note: sscanf is deprecated; consider using sscanf_s instead  
  
   // Output the data read  
   printf( "String    = %s\n", s );  
   printf( "Character = %c\n", c );  
   printf( "Integer:  = %d\n", i );  
   printf( "Real:     = %f\n", fp );  
}  
```  
  
 **String    = 15**  
**Character = 1**  
**Integer:  = 15**  
**Real:     = 15.000000**   
## .NET Framework Equivalent  
 See `Parse` methods, such as [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## See Also  
 [Stream I/O](../VS_visualcpp/Stream-I-O.md)   
 [fscanf, _fscanf_l, fwscanf, _fwscanf_l](../VS_visualcpp/fscanf--_fscanf_l--fwscanf--_fwscanf_l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../VS_visualcpp/scanf--_scanf_l--wscanf--_wscanf_l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../VS_visualcpp/sprintf--_sprintf_l--swprintf--_swprintf_l--__swprintf_l.md)   
 [snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](../VS_visualcpp/snprintf--_snprintf--_snprintf_l--_snwprintf--_snwprintf_l.md)