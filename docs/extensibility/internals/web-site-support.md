---
title: Supporto per siti Web | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff59be63ef1d6e7120842c936dd64dbb77d7ed70
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618029"
---
# <a name="web-site-support"></a>Supporto per siti Web
Un sistema di progetto sito Web è un sistema di progetto che consente di creare progetti Web. I progetti Web consentono di creare applicazioni Web. Un progetto sito Web genera un file eseguibile per ogni pagina Web che contiene il codice associato. File eseguibile aggiuntivi vengono generati da file di codice sorgente nella cartella /App_Code.

 Sistemi di progetto sito Web vengono creati tramite l'aggiunta di modelli e gli attributi di registrazione in un sistema di progetto esistente. Uno di questi attributi consente di selezionare il provider di IntelliSense per la lingua. L'implementazione del provider IntelliSense gestisce riferimenti e il compilatore di linguaggio viene chiamato quando viene richiesta una pagina Web intelligente non memorizzato nella cache.

 Il compilatore di linguaggio usato per compilare le pagine Web deve essere registrato con [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. È possibile usare la [ \<compilatore > elemento](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in un file Web. config per registrare il compilatore, come nell'esempio seguente:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>In questa sezione
- [Modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md)

 Vengono elencati i modelli che è possibile usare per creare nuovi progetti di siti Web e degli elementi associati.

- [Attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md)

 Presenta gli attributi di registrazione che si connettono un progetto sito Web per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>Sezioni correlate
- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene presentata una panoramica dei due tipi di progetti Web, progetti di siti Web e progetti di applicazione Web.