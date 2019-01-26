---
title: Attributi di supporto per siti Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac58ec0d7175d2d7989ce9c4d6086b5a741e77c9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927242"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Progetto di sito Web può essere esteso per fornire il supporto per il Web, linguaggi di programmazione. Il linguaggio deve eseguire la registrazione con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che i modelli di progetto possono essere visualizzati nei **nuovo sito Web** finestra di dialogo quando viene selezionata la lingua.

L'esempio di IronPython Studio include supporto per siti web. L'esempio contiene le classi di attributo seguente per registrare IronPython come linguaggio di codebehind per nuovi progetti Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Questo attributo viene inserito nel progetto Java. La lingua viene aggiunto all'elenco dei linguaggi di programmazione Web di **Language** nell'elenco il **nuovo sito Web** nella finestra di dialogo. Ad esempio, il codice seguente aggiunge IronPython all'elenco:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Questo attributo imposta inoltre il percorso di modelli in modo che punti alla cartella modelli. Per altre informazioni sulla posizione della cartella modelli, vedere [modelli di supporto di siti Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Questo attributo viene inserito nel progetto Java. Consente al progetto sito Web di annidare un tipo di file (correlato) sotto un altro tipo di file (primario) nei **Esplora soluzioni**.

 Ad esempio, il codice seguente specifica che un file codebehind di IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web. aspx in una soluzione di sito IronPython Web, un nuovo file di origine con estensione py viene generato e visualizzato come nodo figlio della pagina aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Seleziona il provider di IntelliSense per la lingua.

 Ad esempio, il codice seguente specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, deve essere creata su richiesta per fornire servizi di linguaggio.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L'implementazione IVsIntellisenseProject gestisce riferimenti e chiama il compilatore di linguaggio quando una pagina Web con il codice è richiesto ma non viene memorizzato nella cache.

## <a name="see-also"></a>Vedere anche
 [Supporto per siti Web](../../extensibility/internals/web-site-support.md)