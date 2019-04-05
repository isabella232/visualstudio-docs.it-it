---
title: Supporto per siti Web | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91deb6d2e3ec58533ac9339c8c94634db23ec996
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970287"
---
# <a name="web-site-support"></a>Supporto per siti Web
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sistema di progetto sito Web è un sistema di progetto che consente di creare progetti Web. I progetti Web consentono di creare applicazioni Web. Un progetto sito Web genera un file eseguibile per ogni pagina Web che contiene il codice associato. File eseguibile aggiuntivi vengono generati da file di codice sorgente nella cartella /App_Code.  
  
 Sistemi di progetto sito Web vengono creati tramite l'aggiunta di modelli e gli attributi di registrazione in un sistema di progetto esistente. Uno di questi attributi consente di selezionare il provider di IntelliSense per la lingua. L'implementazione del provider IntelliSense gestisce riferimenti e il compilatore di linguaggio viene chiamato quando viene richiesta una pagina Web intelligente non memorizzato nella cache.  
  
 Il compilatore di linguaggio usato per compilare le pagine Web deve essere registrato con [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)]. È possibile usare la [ \<compilatore > elemento](http://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) in un file Web. config per registrare il compilatore, come nell'esempio seguente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modelli di supporto per siti Web](../../extensibility/internals/web-site-support-templates.md)  
 Vengono elencati i modelli che è possibile usare per creare nuovi progetti di siti Web e degli elementi associati.  
  
 [Attributi di supporto per siti Web](../../extensibility/internals/web-site-support-attributes.md)  
 Presenta gli attributi di registrazione che si connettono un progetto sito Web per [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)].  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Progetti Web](../../extensibility/internals/web-projects.md)  
 Viene presentata una panoramica dei due tipi di progetti Web, progetti di siti Web e progetti di applicazione Web.
