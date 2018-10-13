---
title: 'Procedura: usare un visualizzatore | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: susanno
manager: douge
ms.openlocfilehash: cdf4c9b3a2ea8dc1322a10799f7f7051b71e035c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306514"
---
# <a name="how-to-use-a-visualizer"></a>Procedura: utilizzare un visualizzatore
È possibile usare un visualizzatore per visualizzare il contenuto di una variabile o di un oggetto in modo significativo per il tipo di dati. È possibile utilizzare i visualizzatori da **suggerimenti dati**, un **Watch** finestra, il **Auto** finestra o il **variabili locali** finestra.  
  
 I visualizzatori non sono supportati in Compact Framework.  
  
> [!NOTE]
>  Nelle **Store** le app, solo il testo standard, i visualizzatori HTML, XML e JSON sono supportati. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
### <a name="to-open-a-visualizer"></a>Per aprire un visualizzatore  
  
1.  Scegliere l'icona della lente di ingrandimento visualizzata accanto al nome di una variabile in **suggerimenti dati**, un **Watch** finestra o nella **Auto**, **variabili locali**, o **Controllo immediato** finestra.  
  
     Verrà visualizzato un elenco di visualizzatori.  
  
2.  Fare clic sul visualizzatore da usare.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Per usare un visualizzatore per il codice gestito durante il debug remoto  
  
-   Copiare la DLL del visualizzatore nel computer remoto prima di avviare la sessione di debug.  
  
     Il percorso della DLL deve essere lo stesso sia nel computer remoto che in quello locale. Il percorso può essere uno dei seguenti:  
  
     *Percorso di installazione di Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     oppure  
  
     `My Documents\Visual Studio 2010\Visualizers` *Versione di Visual Studio* `\Visualizers`  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Visualizzare i valori di dati nei suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)