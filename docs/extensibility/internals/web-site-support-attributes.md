---
title: Attributi di supporto del sito Web | Microsoft Docs
description: Informazioni sugli attributi di supporto del sito Web necessari per estendere la funzionalità di Visual Studio i progetti di sito Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e5eb1af28c7a8dd7dccf2c161474f821f004c07e06f11b554f898190971837a0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414188"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Il progetto di sito Web può essere esteso per fornire supporto per i linguaggi di programmazione Web. Il linguaggio deve registrarsi con in modo che i modelli di progetto possano essere visualizzati nella finestra di dialogo Nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **sito Web** quando la lingua è selezionata.

L'esempio IronPython Studio include il supporto del sito Web. L'esempio contiene le classi di attributi seguenti per registrare IronPython come linguaggio codebehind per i nuovi progetti Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Questo attributo viene inserito nel progetto di linguaggio. Aggiunge il linguaggio all'elenco dei linguaggi di programmazione Web **nell'elenco Linguaggio** della **finestra di dialogo** Nuovo sito Web . Ad esempio, il codice seguente aggiunge IronPython all'elenco:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Questo attributo imposta anche il percorso dei modelli in modo che punti alla cartella templates. Per altre informazioni sul percorso della cartella templates, vedere [Modelli di supporto per siti Web.](../../extensibility/internals/web-site-support-templates.md)

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Questo attributo viene inserito nel progetto di linguaggio. Consente al progetto sito Web di annidare un tipo di file (correlato) in un altro tipo di file (primario) nel **Esplora soluzioni**.

 Ad esempio, il codice seguente specifica che un file codebehind IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web aspx in una soluzione di sito Web IronPython, viene generato un nuovo file di origine con estensione py che viene visualizzato come nodo figlio della pagina aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Seleziona il provider IntelliSense per il linguaggio.

 Ad esempio, il codice seguente specifica che un'istanza di PythonIntellisenseProvider, che implementa , deve essere creata su richiesta per fornire <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> servizi di linguaggio.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L'implementazione di IVsIntellisenseProject gestisce i riferimenti e chiama il compilatore del linguaggio quando viene richiesta una pagina Web con codice ma non viene memorizzata nella cache.

## <a name="see-also"></a>Vedi anche
- [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
