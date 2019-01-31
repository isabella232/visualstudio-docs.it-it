---
title: 'Introduzione a PTVS: Avviare la codifica (progetti) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 14b85e70-b9a8-415c-a307-8c8c316a0495
caps.latest.revision: 7
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 28622f290d82f86bf3d18cc4f40cfcfc8e953dad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781069"
---
# <a name="getting-started-with-ptvs-start-coding-projects"></a>Introduzione a PTVS: Avviare la codifica (progetti)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Python Tools for Visual Studio (PTVS) consente di gestire il codice. 
 
 È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
 Se si è già usato Python in precedenza, si saprà che il progetto viene definito in base al modo in cui i file vengono disposti su disco. Tale approccio è particolarmente efficace per i progetti Python normali, ma quando si hanno più file (pagine Web con JavaScript, unit test e script di compilazione), i file system possono iniziare a essere un po' limitativi. Visual Studio usa i progetti per raggiungere tre scopi. 
 
- Identificare i file critici. I file importanti sono quelli che vengono archiviati in un sistema di controllo della versione (file di origine, risorse e così via), ma non i file che vengono generati come output di compilazione. I file importanti sono anche quelli che vengono copiati in un altro computer in modo tale che altri utenti possano usare l'app. 
 
- Specificare il modo in cui devono essere usati i file. Si potrebbero avere file che uno strumento deve elaborare ogni volta che vengono modificati i file. I progetti di Visual Studio possono acquisire tali informazioni. 
 
- Definire i limiti dei componenti. Se si hanno più componenti nell'app, è possibile inserire ognuno in un progetto separato. Questi componenti possono essere infine distribuiti in server diversi, compilati con impostazioni di debug o di compilazione diverse oppure possono essere scritti perfino usando un altro linguaggio supportato da Visual Studio, ad esempio C++ o Node.js. 
 
  Esistono diversi modelli di progetto per iniziare. Se si dispone già del codice Python da usare, la Creazione guidata nuovo progetto da file di codice esistenti consente di creare un progetto che include tutti i file. Per alcuni dei framework più diffusi esistono più progetti Web. Negli esempi di PTVS sono disponibili più modelli. Ci sono opzioni che consentono di poter usare i modelli Web forniti con altri framework. Il modello di un'applicazione Python è un progetto pulito e vuoto. Esiste un solo modulo per iniziare. 
 
  Visual Studio mostra i progetti aperti nella finestra Esplora soluzioni, inclusi tutti i file, i percorsi di ricerca e gli ambienti Python. Per aggiungere nuovi elementi, selezionare la cartella del progetto e nel menu di scelta rapida (premere il pulsante destro del puntatore) scegliere Aggiungi e quindi Nuovo elemento. È possibile selezionare qualsiasi elemento nella finestra di dialogo, personalizzare il nome dell'elemento e aggiungere l'elemento al progetto. 
 
  È possibile trascinare la selezione in Esplora soluzioni. Se si sono già copiati i file nella struttura di directory del progetto, è possibile scegliere Mostra tutti i file nella parte superiore di Esplora soluzioni. È possibile quindi selezionare gli elementi che si vuole aggiungere e scegliere Includi nel progetto dal menu di scelta rapida. 
 
  È possibile seguire queste istruzioni in un brevissimo [video di youtube](https://www.youtube.com/watch?v=KHPoVpL7zHg&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=2). 
 
## <a name="see-also"></a>Vedere anche 
 [Documentazione Wiki](https://github.com/Microsoft/PTVS/wiki/Projects) [Introduzione a PTVS video e approfondimento di](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
