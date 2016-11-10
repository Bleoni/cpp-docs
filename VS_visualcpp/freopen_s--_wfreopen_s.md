---
title: "freopen_s, _wfreopen_s"
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
  - _wfreopen_s
  - freopen_s
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
  - api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
caps.latest.revision: 25
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
# freopen_s, _wfreopen_s
Reassigns a file pointer. These versions of [freopen, _wfreopen](../VS_visualcpp/freopen--_wfreopen.md) have security enhancements, as described in [Security Features in the CRT](../VS_visualcpp/Security-Features-in-the-CRT.md).  
  
## Syntax  
  
```  
errno_t freopen(   
   FILE** pFile,  
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
errno_t _wfreopen(   
   FILE** pFile,  
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### Parameters  
 [out] `pFile`  
 A pointer to the file pointer to be provided by the call.  
  
 [in] `path`  
 Path of new file.  
  
 [in] `mode`  
 Type of access permitted.  
  
 [in] `stream`  
 Pointer to `FILE` structure.  
  
## Return Value  
 Each of these functions returns an error code. If an error occurs, the original file is closed.  
  
## Remarks  
 The `freopen_s` function closes the file currently associated with `stream` and reassigns `stream` to the file specified by `path.` `_wfreopen_s` is a wide-character version of `_freopen_s`; the `path` and `mode` arguments to `_wfreopen_s` are wide-character strings. `_wfreopen_s` and `_freopen_s` behave identically otherwise.  
  
 If any of `pFile`, `path`, `mode`, or `stream` are `NULL`, or if `path` is an empty string, these functions invoke the invalid parameter handler, as described in [Parameter Validation](../VS_visualcpp/Parameter-Validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL` and return `EINVAL`.  
  
### Generic-Text Routine Mappings  
  
|TCHAR.H routine|_UNICODE & _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen_s`|`freopen_s`|`freopen_s`|`_wfreopen_s`|  
  
 `freopen_s` is typically used to redirect the pre-opened files `stdin`, `stdout`, and `stderr` to files specified by the user. The new file associated with `stream` is opened with `mode`*,* which is a character string specifying the type of access requested for the file, as follows:  
  
 `"r"`  
 Opens for reading. If the file does not exist or cannot be found, the `freopen_s` call fails.  
  
 `"w"`  
 Opens an empty file for writing. If the given file exists, its contents are destroyed.  
  
 `"a"`  
 Opens for writing at the end of the file (appending) without removing the EOF marker before writing new data to the file; creates the file first if it does not exist.  
  
 `"r+"`  
 Opens for both reading and writing. (The file must exist.)  
  
 `"w+"`  
 Opens an empty file for both reading and writing. If the given file exists, its contents are destroyed.  
  
 `"a+"`  
 Opens for reading and appending; the appending operation includes the removal of the EOF marker before new data is written to the file and the EOF marker is restored after writing is complete; creates the file first if it does not exist.  
  
 Use the `"w"` and `"w+"` types with care, as they can destroy existing files.  
  
 When a file is opened with the `"a"` or `"a+"` access type, all write operations take place at the end of the file. Although the file pointer can be repositioned using `fseek` or `rewind`, the file pointer is always moved back to the end of the file before any write operation is carried out. Thus, existing data cannot be overwritten.  
  
 The `"a"` mode does not remove the EOF marker before appending to the file. After appending has occurred, the MS-DOS TYPE command only shows data up to the original EOF marker and not any data appended to the file. The `"a+"` mode does remove the EOF marker before appending to the file. After appending, the MS-DOS TYPE command shows all data in the file. The `"a+"` mode is required for appending to a stream file that is terminated with the CTRL+Z EOF marker.  
  
 When the `"r+",``"w+",` or `"a+"` access type is specified, both reading and writing are allowed (the file is said to be open for "update"). However, when you switch between reading and writing, there must be an intervening [fsetpos](../VS_visualcpp/fsetpos.md), [fseek](../VS_visualcpp/fseek--_fseeki64.md), or [rewind](../VS_visualcpp/rewind.md) operation. The current position can be specified for the `fsetpos` or `fseek` operation, if desired. In addition to the above values, one of the following characters may be included in the `mode` string to specify the translation mode for new lines.  
  
 `t`  
 Open in text (translated) mode; carriage return–linefeed (CR-LF) combinations are translated into single linefeed (LF) characters on input; LF characters are translated to CR-LF combinations on output. Also, CTRL+Z is interpreted as an end-of-file character on input. In files opened for reading or for writing and reading with `"a+"`, the run-time library checks for a CTRL+Z at the end of the file and removes it, if possible. This is done because using `fseek` and `ftell` to move within a file may cause `fseek` to behave improperly near the end of the file. The `t` option is a Microsoft extension that should not be used where ANSI portability is desired.  
  
 `b`  
 Open in binary (untranslated) mode; the above translations are suppressed.  
  
 If `t` or `b` is not given in `mode`, the default translation mode is defined by the global variable [_fmode](../VS_visualcpp/_fmode.md). If `t` or `b` is prefixed to the argument, the function fails and returns `NULL`.  
  
 For a discussion of text and binary modes, see [Text and Binary Mode File I/O](../VS_visualcpp/Text-and-Binary-Mode-File-I-O.md).  
  
## Requirements  
  
|Function|Required header|  
|--------------|---------------------|  
|`freopen_s`|<stdio.h>|  
|`_wfreopen_s`|<stdio.h> or <wchar.h>|  
  
 The console is not supported in Windows 8.x Store apps. The standard stream handles that are associated with the console—`stdin`, `stdout`, and `stderr`—must be redirected before C run-time functions can use them in Windows 8.x Store apps. For additional compatibility information, see [Compatibility](../VS_visualcpp/Compatibility.md).  
  
## Example  
  
```  
// crt_freopen_s.c  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   errno_t err;  
   // Reassign "stderr" to "freopen.out":   
   err = freopen_s( &stream, "freopen.out", "w", stderr );  
  
   if( err != 0 )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
 **successfully reassigned**  
**This will go to the file 'freopen.out'**   
## .NET Framework Equivalent  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.#ctor?qualifyHint=False>  
  
## See Also  
 [Stream I/O](../VS_visualcpp/Stream-I-O.md)   
 [freopen, _wfreopen](../VS_visualcpp/freopen--_wfreopen.md)   
 [fclose, _fcloseall](../VS_visualcpp/fclose--_fcloseall.md)   
 [_fdopen, _wfdopen](../VS_visualcpp/_fdopen--_wfdopen.md)   
 [_fileno](../VS_visualcpp/_fileno.md)   
 [fopen, _wfopen](../VS_visualcpp/fopen--_wfopen.md)   
 [_open, _wopen](../VS_visualcpp/_open--_wopen.md)   
 [_setmode](../VS_visualcpp/_setmode.md)