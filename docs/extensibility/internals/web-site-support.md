---
title: Supporto per siti Web Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703440"
---
# <a name="web-site-support"></a>Supporto per siti Web
Un sistema di progetto di sito Web è un sistema di progetto che crea progetti Web. I progetti Web a loro volta creano applicazioni Web. Un progetto di sito Web genera un file eseguibile per ogni pagina Web a cui è associato codice. Ulteriori file eseguibili vengono generati dai file di codice sorgente nella cartella /App_Code.

 I sistemi di progetto di sito Web vengono creati aggiungendo modelli e attributi di registrazione a un sistema di progetto esistente. Uno di questi attributi seleziona il provider IntelliSense per il linguaggio. L'implementazione del provider IntelliSense gestisce i riferimenti e chiama il compilatore di linguaggio quando viene richiesta una pagina Web intelligente che non viene memorizzata nella cache.

 Il compilatore di linguaggio utilizzato [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]per compilare le pagine Web deve essere registrato con . È possibile utilizzare il [ \<compilatore> Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in un file Web.config per registrare il compilatore, come nell'esempio seguente:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Contenuto della sezione
- [Modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md)

 Vengono elencati i modelli che è possibile utilizzare per creare nuovi progetti di sito Web ed elementi associati.

- [Attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md)

 Presenta gli attributi di registrazione che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]collegano un progetto di sito Web a e .

## <a name="related-sections"></a>Sezioni correlate
- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene presentata una panoramica dei due tipi di progetti Web, progetti di sito Web e progetti di applicazione Web.
