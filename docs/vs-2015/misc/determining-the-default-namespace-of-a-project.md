---
title: Stabilire il Namespace predefinito di un progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: douge
ms.openlocfilehash: a456b9b48ce9ba0817070fb5f04b5c9f80ffb149
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223327"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinazione dello spazio dei nomi predefinito di un progetto
Per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], se il `CustomToolNamespace` viene impostata nel file di input, il valore di `CustomToolNamespace` diventa il valore del parametro dello spazio dei nomi predefinito passato per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> (metodo). In caso contrario, il `wszDefaultNamespace` passato al parametro `Generate` è sempre uguale allo spazio dei nomi radice. Per altre informazioni sugli spazi dei nomi, vedere [parole chiave Namespace](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] Usa spazi dei nomi basati su cartelle. Ovvero lo spazio dei nomi comprende lo spazio dei nomi radice, e i nomi delle cartelle che contiene lo strumento personalizzato. Ogni nome di cartella viene convertito in un identificatore valido e periodi di separano i nomi di tutti. Ad esempio, se il file di input è FolderA\FolderB\FolderC\MyInput.txt e lo spazio dei nomi radice è CL9, lo spazio dei nomi predefinito calcolata sarà **CL9. FolderA.FolderB.FolderC**.  
  
 Un'eccezione a questa regola si verifica quando la catena della gerarchia contiene una cartella di riferimento Web. Ad esempio, se:  
  
-   Una cartella di riferimento Web è stata FolderC, lo spazio dei nomi sarebbe **CL9. FolderC**.  
  
-   Una cartella di riferimento Web è stata cartellaB, lo spazio dei nomi sarebbe **CL9. FolderB.FolderC**.  
  
 Vale a dire, lo spazio dei nomi viene utilizzato il formato seguente:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di generatori di File singoli](../extensibility/internals/implementing-single-file-generators.md)   
 [La registrazione di generatori di File singoli](../extensibility/internals/registering-single-file-generators.md)   
 [Esposizione di tipi nelle finestre di progettazione visiva](../extensibility/internals/exposing-types-to-visual-designers.md)