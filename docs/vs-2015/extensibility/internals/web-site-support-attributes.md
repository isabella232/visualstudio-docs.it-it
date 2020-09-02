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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144306"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Il progetto di sito Web può essere esteso per fornire supporto per i linguaggi di programmazione Web. È necessario che il linguaggio si registri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] in modo che i modelli di progetto possano essere visualizzati nella finestra di dialogo **nuovo sito Web** quando la lingua è selezionata.  
  
 L'esempio IronPython Studio include il supporto per siti Web. È possibile trovarlo con gli [esempi di VSSDK](../../misc/vssdk-samples.md). Sono incluse le classi Attribute seguenti per registrare IronPython come linguaggio codebehind per i nuovi progetti Web.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Questo attributo viene inserito nel progetto di linguaggio. Consente di aggiungere la lingua all'elenco dei linguaggi di programmazione Web nell'elenco **lingua** della finestra di dialogo **nuovo sito Web** . Il codice seguente, ad esempio, aggiunge IronPython all'elenco:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Questo attributo imposta anche il percorso dei modelli in modo che punti alla cartella Templates. Per ulteriori informazioni sul percorso della cartella dei modelli, vedere [modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Questo attributo viene inserito nel progetto di linguaggio. Consente al progetto di sito Web di annidare un tipo di file (correlato) in un altro tipo di file (primario) nell' **Esplora soluzioni**.  
  
 Ad esempio:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Specifica che un file codebehind IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web aspx in una soluzione di sito Web IronPython, viene generato un nuovo file di origine con estensione py e viene visualizzato come nodo figlio della pagina aspx.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Consente di selezionare il provider IntelliSense per la lingua.  
  
 Ad esempio:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , deve essere creata su richiesta per fornire i servizi di linguaggio.  
  
 L'implementazione di IVsIntellisenseProject gestisce i riferimenti e chiama il compilatore del linguaggio quando viene richiesta una pagina Web con codice ma non memorizzata nella cache.  
  
## <a name="see-also"></a>Vedere anche  
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
