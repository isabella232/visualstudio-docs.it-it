---
title: Genera commenti relativi alla documentazione XML, generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: f1c1dfb69c12eb183ecf3435346a543488ebe0e1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-xml-documentation-comments-in-c"></a>Genera commenti relativi alla documentazione XML in c# #
**Novità:** consente di generare immediatamente la base XML obbligatorio per documentare l'elemento selezionato. 

**Quando:** si desidera creare commenti al documento XML per l'elaborazione successiva da uno strumento di documentazione come Sandcastle.

**Motivo:** è possibile creare manualmente il blocco di commento intera manualmente, tuttavia verrà risparmiare tempo e migliorare l'accuratezza generando il modello di base e altri elementi. 

**Procedura:**

1. Posizionare il cursore di testo sopra l'elemento a cui che si desidera documentare, ad esempio, un metodo.

   ![Metodo al documento](media/doc_highlight.png)

1. Digitare quindi  **///**  (3 in poi barre) che crea automaticamente il modello di base e gli eventuali elementi aggiuntivi in base alle esigenze.  Ad esempio, quando si aggiungono commenti a un metodo, verrà generato il  **\<riepilogo\>**  tag, nonché un  **\<param\>**  tag per ogni parametro è passato al metodo e un  **\<restituisce\>**  tag per documentare il metodo restituisce.

   ![Modello](media/doc_preview.png)

1. Completare i commenti e aggiungere eventuali informazioni aggiuntive che si ritiene sono necessarie.

   ![Commento completato](media/doc_result.png)

## <a name="see-also"></a>Vedere anche
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
