---
title: File di risposta MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a1ce11edac37368b9c4993a87a8c2b3e734b7862
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189372"
---
# <a name="msbuild-response-files"></a>File di risposta MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I file di risposta (RSP) sono file di testo che contengono opzioni della riga di comando di MSBuild.exe. Ogni opzione può essere su una riga separata oppure tutte le opzioni possono essere sulla stessa riga. Le righe di commento sono precedute da un **#** simbolo. L' **@** opzione viene usata per passare un altro file di risposta a MSBuild.exe.  
  
 Il file di risposta automatica è un file RSP speciale che MSBuild.exe usa automaticamente quando si compila un progetto. Questo file, MSBuild.rsp, deve essere nella stessa directory di MSBuild.exe, in caso contrario non viene rilevato. È possibile modificare questo file per specificare opzioni predefinite della riga di comando per MSBuild.exe. Se, ad esempio, si utilizza lo stesso logger ogni volta che si compila un progetto, è possibile aggiungere l'opzione **/logger** a MSBuild. rsp e MSBuild.exe utilizzerà il logger ogni volta che viene compilato un progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)
