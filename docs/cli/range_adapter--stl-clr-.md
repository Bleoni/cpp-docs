---
title: "range_adapter (STL-CLR)"
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
  - "cliext::range_adapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "range_adapter class [STL/CLR]"
ms.assetid: 3fbe2a65-1216-46a0-a182-422816b80cfb
caps.latest.revision: 16
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
# range_adapter (STL/CLR)
A template class that wraps a pair of iterators that are used to implement several Base Class Library (BCL) interfaces. You use the range_adapter to manipulate an STL/CLR range as if it were a BCL collection.  
  
## Syntax  
  
```  
template<typename Iter>  
    ref class range_adapter  
        :   public  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<Value>,  
        System::Collections::Generic::ICollection<Value>  
    { ..... };  
```  
  
#### Parameters  
 Iter  
 The type associated with the wrapped iterators.  
  
## Members  
  
|Member Function|Description|  
|---------------------|-----------------|  
|[range_adapter::range_adapter (STL/CLR)](../cli/range_adapter--range_adapter--stl-clr-.md)|Constructs an adapter object.|  
  
|Operator|Description|  
|--------------|-----------------|  
|[range_adapter::operator= (STL/CLR)](../cli/range_adapter--operator=--stl-clr-.md)|Replaces the stored iterator pair.|  
  
## Interfaces  
  
|Interface|Description|  
|---------------|-----------------|  
|\<xref:System.Collections.IEnumerable>|Iterates through elements in the collection.|  
|\<xref:System.Collections.ICollection>|Maintains a group of elements.|  
|<xref:System.Collections.Generic.IEnumerable`1>|Iterates through typed elements in the collection..|  
|<xref:System.Collections.Generic.ICollection`1>|Maintains a group of typed elements.|  
  
## Remarks  
 The range_adapter stores a pair of iterators, which in turn delimit a sequence of elements. The object implements four BCL interfaces that let you iterate through the elements, in order. You use this template class to manipulate STL/CLR ranges much like BCL containers.  
  
## Requirements  
 **Header:** \<cliext/adapter>  
  
 **Namespace:** cliext  
  
## See Also  
 [collection_adapter (STL/CLR)](../cli/collection_adapter--stl-clr-.md)   
 [make_collection (STL/CLR)](../cli/make_collection--stl-clr-.md)