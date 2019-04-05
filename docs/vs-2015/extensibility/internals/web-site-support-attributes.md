---
title: Attributi di supporto per siti Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966841"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Progetto di sito Web può essere esteso per fornire il supporto per il Web, linguaggi di programmazione. Il linguaggio deve eseguire la registrazione con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in modo che i modelli di progetto possono essere visualizzati nei **nuovo sito Web** finestra di dialogo quando viene selezionata la lingua.  
  
 L'esempio di IronPython Studio include supporto per siti web. È possibile trovarlo con le [esempi di VSSDK](../../misc/vssdk-samples.md). Include le seguenti classi di attributi per la registrazione di IronPython come linguaggio di codebehind per nuovi progetti Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Questo attributo viene inserito nel progetto Java. La lingua viene aggiunto all'elenco dei linguaggi di programmazione Web di **Language** nell'elenco il **nuovo sito Web** nella finestra di dialogo. Ad esempio, di seguito aggiunge IronPython all'elenco:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Questo attributo imposta inoltre il percorso di modelli in modo che punti alla cartella modelli. Per altre informazioni sulla posizione della cartella modelli, vedere [modelli di supporto di siti Web](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Questo attributo viene inserito nel progetto Java. Consente al progetto sito Web di annidare un tipo di file (correlato) sotto un altro tipo di file (primario) nei **Esplora soluzioni**.  
  
 Ad esempio:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Specifica che un file codebehind di IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web. aspx in una soluzione di sito IronPython Web, un nuovo file di origine con estensione py viene generato e visualizzato come nodo figlio della pagina aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Seleziona il provider di Intellisense per la lingua.  
  
 Ad esempio:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, deve essere creata su richiesta per fornire servizi di linguaggio.  
  
 L'implementazione IVsIntellisenseProject gestisce riferimenti e chiama il compilatore di linguaggio quando una pagina Web con il codice è richiesto ma non viene memorizzato nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
