---
title: 'Procedura: Trovare argomenti nel sommario | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer 2.0, table of contents filtering
- Help Viewer 2.0, Contents tab
- Contents tab [Help Viewer 2.0]
- table of contents filtering [Help Viewer 2.0]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8ab015fdfd459dbb13e81deed0fe0cc89f71cd1f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63416681"
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Procedura: Trovare argomenti nel sommario
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nella scheda **Contenuto** è possibile usare il sommario per trovare le informazioni. Il sommario è un elenco espandibile che contiene tutti argomenti dei libri installati. Per informazioni sull'accessibilità relative a come spostarsi nel sommario, vedere [Tasti di scelta rapida (Help Viewer)](../ide/shortcut-keys-help-viewer.md).  
  
> [!IMPORTANT]
> L'ambito degli argomenti disponibili nel sommario dipende dal filtro selezionato.  
  
## <a name="filter-the-toc"></a>Filtrare il sommario  
 È possibile filtrare il sommario per limitare l'ambito degli argomenti visualizzati nella scheda **Contenuto**. I titoli vengono visualizzati nell'elenco solo se contengono la radice del termine specificato. Ad esempio, se si specifica la parola "risoluzione" come filtro, verranno visualizzati solo i titoli contenenti la parola "risolvere" o "risoluzione". I nodi i cui titoli non contengono il termine verranno compressi in un unico nodo con i puntini di sospensione (...).  
  
#### <a name="to-filter-the-toc"></a>Per filtrare il sommario  
  
1. Scegliere la scheda **Contenuto**.  
  
2. Nella casella di testo **Filtra contenuti** immettere un termine.  
  
> [!NOTE]
> Se l'esecuzione del filtro richiede molto tempo, è possibile visualizzare i risultati più rapidamente usando l'operatore di ricerca avanzata `title:`.  
  
## <a name="synchronize-a-topic-with-the-toc"></a>Sincronizzare un argomento con il sommario  
 Se un argomento è stato aperto tramite l'indice o le funzionalità di ricerca full-text, è possibile determinarne la posizione all'interno del sommario sincronizzando quest'ultimo con la finestra dell'argomento.  
  
#### <a name="to-synchronize-the-toc-with-the-topic-window"></a>Per sincronizzare il sommario con la finestra dell'argomento  
  
1. Visualizzare un argomento.  
  
2. Fare clic sul pulsante **Mostra argomento nel contenuto** nella barra degli strumenti oppure premere CTRL+S.  
  
     Viene aperta la scheda **Contenuto** in cui viene visualizzata la posizione dell'argomento nel sommario.  
  
## <a name="see-also"></a>Vedere anche  
 [Locate Information](../ide/locate-information.md)  (Individuare informazioni)  
 [Microsoft Help Viewer](../ide/microsoft-help-viewer.md)
