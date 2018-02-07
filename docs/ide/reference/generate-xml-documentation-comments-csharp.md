---
title: Generare commenti in formato documentazione XML - Generazione del codice (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2025bd2-5984-4486-a61c-0a0933a735ea
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: b0a0ec1db54f57e14ddd412248f7a396336fe009
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="generate-xml-documentation-comments-in-c"></a>Generare commenti in formato documentazione XML in C# #
**Cosa:** consente di generare immediatamente il codice XML di base richiesto per documentare l'elemento selezionato. 

**Quando:** si vogliono creare commenti in formato documentazione XML per l'elaborazione successiva con uno strumento di documentazione come Sandcastle.

**Perché:** è possibile creare manualmente l'intero blocco di commento, tuttavia questa funzionalità consentirà di risparmiare tempo e ottenere una maggiore accuratezza generando il modello di base e altri elementi. 

**Come:**

1. Posizionare il cursore del testo sopra l'elemento da documentare, ad esempio, un metodo.

   ![Metodo da documentare](media/doc-highlight-cs.png)

1. Digitare quindi **///** (3 barre). Verranno creati automaticamente il modello di base e gli eventuali elementi aggiuntivi necessari.  Ad esempio, quando si aggiungono commenti per un metodo, verranno generati i tag **\<summary\>**, oltre a un tag **\<param\>** per ogni parametro passato al metodo e a un tag **\<returns\>** per documentare i valori restituiti dal metodo.

   ![Modello](media/doc-preview-cs.png)

1. Completare i commenti e aggiungere eventuali informazioni aggiuntive che si ritiene necessarie.

   ![Commento completato](media/doc-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)  
[Commenti in formato documentazione XML (Guida per programmatori C#)](/dotnet/csharp/programming-guide/xmldoc/xml-documentation-comments)
