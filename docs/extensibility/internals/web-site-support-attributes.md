---
title: Attributi di supporto del sito Web Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703489"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Il progetto di sito Web può essere esteso per fornire supporto ai linguaggi di programmazione Web. Il linguaggio deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrarsi in modo che i modelli di progetto possano essere visualizzati nella finestra di dialogo **Nuovo sito Web** quando viene selezionata la lingua.

L'esempio IronPython Studio include il supporto per siti Web.The IronPython Studio sample includes web site support. L'esempio contiene le classi di attributi seguenti per registrare IronPython come linguaggio codebehind per i nuovi progetti Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute (AttributiWebProjectAttribute)
 Questo attributo viene inserito nel progetto di linguaggio. Aggiunge il linguaggio all'elenco dei linguaggi di programmazione Web nell'elenco **Linguaggio** della finestra di dialogo **Nuovo sito Web.** Ad esempio, il codice seguente aggiunge IronPython all'elenco:For example, the following code adds IronPython to the list:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Questo attributo imposta anche il percorso dei modelli in modo che punti alla cartella dei modelli. Per ulteriori informazioni sul percorso della cartella dei modelli, vedere Modelli di [supporto sito Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Questo attributo viene inserito nel progetto di linguaggio. Consente al progetto di sito Web di nidificare un tipo di file (correlato) in un altro tipo di file (primario) in **Esplora soluzioni**.

 Ad esempio, il codice seguente specifica che un file codebehind IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web aspx in una soluzione di sito Web IronPython, viene generato un nuovo file di origine con estensione py che viene visualizzato come nodo figlio della pagina aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Seleziona il provider IntelliSense per il linguaggio.

 Ad esempio, il codice seguente specifica che un'istanza <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>di PythonIntellisenseProvider, che implementa , deve essere creata su richiesta per fornire servizi di linguaggio.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Il IVsIntellisenseProject implementazione gestisce i riferimenti e chiama il compilatore di linguaggio quando viene richiesta una pagina Web con codice, ma non è memorizzato nella cache.

## <a name="see-also"></a>Vedere anche
- [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
