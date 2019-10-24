---
title: Implementazione di generatori di file singoli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727171"
---
# <a name="implementing-single-file-generators"></a>Implementazione di generatori di file singoli
Uno strumento personalizzato, noto anche come singolo generatore di file, può essere usato per estendere il [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i sistemi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Uno strumento personalizzato è un componente COM che implementa l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Utilizzando questa interfaccia, uno strumento personalizzato trasforma un singolo file di input in un unico file di output. Il risultato della trasformazione può essere codice sorgente o qualsiasi altro output utile. Due esempi di file di codice generati da strumenti personalizzati sono rappresentati dal codice generato in risposta alle modifiche in una finestra di progettazione visiva e ai file generati utilizzando Web Services Description Language (WSDL).

 Quando viene caricato uno strumento personalizzato o il file di input viene salvato, il sistema del progetto chiama il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> e passa un riferimento a un'interfaccia di callback di <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>, in base alla quale lo strumento può segnalare lo stato di avanzamento all'utente.

 Il file di output generato dallo strumento personalizzato viene aggiunto al progetto con una dipendenza dal file di input. Il sistema del progetto determina automaticamente il nome del file di output, in base alla stringa restituita dall'implementazione dello strumento personalizzato di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Uno strumento personalizzato deve implementare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Facoltativamente, gli strumenti personalizzati supportano l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> per recuperare le informazioni da origini diverse da quelle del file di input. In ogni caso, prima di poter usare uno strumento personalizzato, è necessario registrarlo nel sistema o nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registro di sistema locale. Per ulteriori informazioni sulla registrazione di strumenti personalizzati, vedere la pagina relativa alla [registrazione di generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Vedere anche
- [Esposizione di tipi nelle finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)