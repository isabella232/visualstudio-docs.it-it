---
title: Supporto per siti Web | Microsoft Docs
description: Informazioni sui sistemi di progetto del sito Web, creati aggiungendo modelli e attributi di registrazione a un sistema di progetto esistente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0cd561e9c1585380a4321801cf8bd21ff40e4d41
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711747"
---
# <a name="web-site-support"></a>Supporto per siti Web
Un sistema di progetto di sito Web è un sistema di progetto che crea progetti Web. I progetti Web creano a loro volta applicazioni Web. Un progetto di sito Web genera un file eseguibile per ogni pagina Web a cui è associato codice. I file eseguibili aggiuntivi vengono generati dai file di codice sorgente nella cartella /App_Code .

 I sistemi di progetto del sito Web vengono creati aggiungendo modelli e attributi di registrazione a un sistema di progetto esistente. Uno di questi attributi seleziona il provider IntelliSense per il linguaggio. L'implementazione del provider IntelliSense gestisce i riferimenti e chiama il compilatore del linguaggio quando viene richiesta una pagina Web intelligente non memorizzata nella cache.

 Il compilatore del linguaggio usato per compilare le pagine Web deve essere registrato con [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . È possibile usare [ \<compiler> l'elemento](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) in un file Web.config per registrare il compilatore, come nell'esempio seguente:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>Contenuto della sezione
- [Modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md)

 Elenca i modelli che è possibile utilizzare per creare nuovi progetti di sito Web ed elementi associati.

- [Attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md)

 Presenta gli attributi di registrazione che connettono un progetto di sito Web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a e [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Sezioni correlate
- [Progetti Web](../../extensibility/internals/web-projects.md)

 Viene presentata una panoramica dei due tipi di progetti Web, progetti di sito Web e progetti di applicazione Web.
