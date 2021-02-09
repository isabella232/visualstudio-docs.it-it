---
title: Attributi di supporto per siti Web | Microsoft Docs
description: Informazioni sugli attributi di supporto per i siti Web necessari per estendere le funzionalità di Visual Studio mediante i progetti di siti Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 452760974207c4ad30e18dd0c4917bcf7b7aa55d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886834"
---
# <a name="web-site-support-attributes"></a>Attributi di supporto per siti Web
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Il progetto di sito Web può essere esteso per fornire supporto per i linguaggi di programmazione Web. È necessario che il linguaggio si registri [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in modo che i modelli di progetto possano essere visualizzati nella finestra di dialogo **nuovo sito Web** quando la lingua è selezionata.

L'esempio IronPython Studio include il supporto per siti Web. Nell'esempio sono contenute le classi Attribute seguenti per registrare IronPython come linguaggio codebehind per i nuovi progetti Web.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Questo attributo viene inserito nel progetto di linguaggio. Consente di aggiungere la lingua all'elenco dei linguaggi di programmazione Web nell'elenco **lingua** della finestra di dialogo **nuovo sito Web** . Ad esempio, il codice seguente aggiunge IronPython all'elenco:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Questo attributo imposta anche il percorso dei modelli in modo che punti alla cartella Templates. Per ulteriori informazioni sul percorso della cartella dei modelli, vedere [modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Questo attributo viene inserito nel progetto di linguaggio. Consente al progetto di sito Web di annidare un tipo di file (correlato) in un altro tipo di file (primario) nell' **Esplora soluzioni**.

 Il codice seguente, ad esempio, specifica che un file codebehind IronPython è correlato a un file aspx. Quando viene creata una nuova pagina Web aspx in una soluzione di sito Web IronPython, viene generato un nuovo file di origine con estensione py e viene visualizzato come nodo figlio della pagina aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Questo attributo viene inserito nel pacchetto del progetto di linguaggio. Consente di selezionare il provider IntelliSense per la lingua.

 Il codice seguente, ad esempio, specifica che un'istanza di PythonIntellisenseProvider, che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , deve essere creata su richiesta per fornire i servizi di linguaggio.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 L'implementazione di IVsIntellisenseProject gestisce i riferimenti e chiama il compilatore del linguaggio quando viene richiesta una pagina Web con codice ma non memorizzata nella cache.

## <a name="see-also"></a>Vedi anche
- [Supporto per siti Web](../../extensibility/internals/web-site-support.md)
