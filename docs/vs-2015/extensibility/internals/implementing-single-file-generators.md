---
title: Implementazione di generatori di file singoli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192697"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uno strumento personalizzato, talvolta denominato generatore di file singolo, può essere utilizzato per estendere i sistemi di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetto e in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Uno strumento personalizzato è un componente COM che implementa l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Utilizzando questa interfaccia, uno strumento personalizzato trasforma un singolo file di input in un unico file di output. Il risultato della trasformazione può essere codice sorgente o qualsiasi altro output utile. Due esempi di file di codice generati da strumenti personalizzati sono rappresentati dal codice generato in risposta alle modifiche in una finestra di progettazione visiva e ai file generati utilizzando Web Services Description Language (WSDL).  
  
 Quando viene caricato uno strumento personalizzato o il file di input viene salvato, il sistema del progetto chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodo e passa un riferimento a un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaccia di callback, in modo che lo strumento possa segnalare lo stato di avanzamento all'utente.  
  
 Il file di output generato dallo strumento personalizzato viene aggiunto al progetto con una dipendenza dal file di input. Il sistema del progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione dello strumento personalizzato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Uno strumento personalizzato deve implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Facoltativamente, gli strumenti personalizzati supportano l' <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaccia per recuperare le informazioni da origini diverse da quelle del file di input. In ogni caso, prima di poter usare uno strumento personalizzato, è necessario registrarlo nel sistema o nel registro di sistema [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] locale. Per ulteriori informazioni sulla registrazione di strumenti personalizzati, vedere la pagina relativa alla [registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Determinazione dello spazio dei nomi predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
