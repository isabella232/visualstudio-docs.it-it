---
title: Determinazione dello spazio dei nomi predefinito di un progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705777"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinazione dello spazio dei nomi predefinito di un progetto
Per [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , se la `CustomToolNamespace` proprietà è impostata sul file di input, il valore di `CustomToolNamespace` diventa il valore del parametro dello spazio dei nomi predefinito passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodo. In caso contrario, il `wszDefaultNamespace` parametro passato a `Generate` è sempre uguale allo spazio dei nomi radice. Per ulteriori informazioni sugli spazi dei nomi, vedere [parole chiave dello spazio dei nomi](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] USA gli spazi dei nomi basati su cartelle. Ovvero lo spazio dei nomi è costituito dallo spazio dei nomi radice, oltre ai nomi di tutte le cartelle che contengono lo strumento personalizzato. Ogni nome di cartella viene convertito in un identificatore valido e i punti separano tutti i nomi. Se, ad esempio, il file di input è FolderA\FolderB\FolderC\MyInput.txt e lo spazio dei nomi radice è CL9, lo spazio dei nomi predefinito calcolato sarà **CL9. Cartella a. FolderB. FolderC**.  
  
 Un'eccezione a questa regola si verifica quando la catena della gerarchia contiene una cartella di riferimento Web. Ad esempio, se:  
  
- FolderC è una cartella di riferimento Web, lo spazio dei nomi è **CL9. FolderC**.  
  
- FolderB è una cartella di riferimento Web, lo spazio dei nomi è **CL9. FolderB. FolderC**.  
  
  Ovvero lo spazio dei nomi usa il formato seguente:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di generatori di file singoli](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrazione di generatori di file singoli](../extensibility/internals/registering-single-file-generators.md)   
 [Esposizione di tipi nelle finestre di progettazione visiva](../extensibility/internals/exposing-types-to-visual-designers.md)