---
title: "Compiler Error C2545"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "error-reference"
f1_keywords: 
  - "C2545"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2545"
ms.assetid: 51598eb9-0c57-4306-a0cd-3862980f3672
caps.latest.revision: 6
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
# Compiler Error C2545
'operator' : unable to find overloaded operator  
  
 The operator cannot be used with the operands provided. You must supply an overloaded operator with the required operands.  
  
 This error can be caused if operands have incorrect type.  
  
 This error may be fixed if you define a conversion operator or constructor that takes a single parameter.