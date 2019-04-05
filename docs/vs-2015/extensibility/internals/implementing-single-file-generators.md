---
title: Implementazione di generatori di File singoli | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964992"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uno strumento personalizzato, talvolta detta un generatore di file singolo, possono essere utilizzate per estendere il [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../../includes/csprcs-md.md)] in sistemi di progetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Uno strumento personalizzato è un componente COM che implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Utilizzo di questa interfaccia, uno strumento personalizzato Trasforma un singolo file di input in un singolo file di output. Il risultato della trasformazione può essere il codice sorgente, o qualsiasi altro output che è utile. Codice generato in risposta alle modifiche in una finestra di progettazione e i file generati con Web Services Description Language (WSDL) sono due esempi di file di codice generati dallo strumento personalizzato.  
  
 Quando viene caricato uno strumento personalizzato o viene salvato il file di input, il sistema di progetto chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metodo e passa un riferimento a un <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interfaccia di callback, in base al quale lo strumento può segnalare lo stato di avanzamento all'utente.  
  
 Il file di output generato dallo strumento personalizzato viene aggiunto al progetto con una dipendenza nel file di input. Il sistema di progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione dello strumento personalizzato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Uno strumento personalizzato deve implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interfaccia. Facoltativamente, gli strumenti personalizzati supportano il <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interfaccia per recuperare informazioni da origini diverse dal file di input. In ogni caso, prima è possibile usare uno strumento personalizzato, è necessario registrarlo con il sistema o nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registro di sistema locale. Per altre informazioni sulla registrazione di strumenti personalizzati, vedere [la registrazione di generatori di File singoli](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Stabilire il Namespace predefinito di un progetto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)
