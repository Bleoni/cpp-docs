---
title: "How to: Load Unmanaged Resources into a Byte Array"
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
ms.topic: get-started-article
ms.assetid: cdada6cd-6d42-437a-a90f-44a0b18d6a93
caps.latest.revision: 13
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
# How to: Load Unmanaged Resources into a Byte Array
This topic discusses several ways to load unmanaged resources into a <xref:System.Byte?qualifyHint=False> array.  
  
## Example  
 If you know the size of your unmanaged resource, you can preallocate a CLR array and then load the resource into the array using a pointer to the array block of the CLR array.  
  
```  
// load_unmanaged_resources_into_Byte_array.cpp  
// compile with: /clr  
using namespace System;  
void unmanaged_func( unsigned char * p ) {  
   for ( int i = 0; i < 10; i++ )  
      p[ i ] = i;  
}  
  
public ref class A {  
public:  
   void func() {  
      array<Byte> ^b = gcnew array<Byte>(10);  
      pin_ptr<Byte> p =  &b[ 0 ];  
      Byte * np = p;  
      unmanaged_func( np );   // pass pointer to the block of CLR array.  
      for ( int i = 0; i < 10; i++ )  
         Console::Write( b[ i ] );  
      Console::WriteLine();  
   }  
};  
  
int main() {  
   A^ g = gcnew A;  
   g->func();  
}  
```  
  
 **0123456789**   
## Example  
 This sample shows how to copy data from an unmanaged memory block to a managed array.  
  
```  
// load_unmanaged_resources_into_Byte_array_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
#include <string.h>  
int main() {  
   char buf[] = "Native String";  
   int len = strlen(buf);  
   array<Byte> ^byteArray = gcnew array<Byte>(len + 2);  
  
   // convert any native pointer to IntPtr by doing C-Style cast  
   Marshal::Copy( (IntPtr)buf, byteArray, 0, len );  
}  
```  
  
## See Also  
 [Using C++ Interop (Implicit PInvoke)](../VS_visualcpp/Using-C---Interop--Implicit-PInvoke-.md)