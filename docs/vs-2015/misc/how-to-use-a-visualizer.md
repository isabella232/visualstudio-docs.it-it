---
title: 'Procedura: Usare un visualizzatore | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
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
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ec7527e51175b82d06a35ad7a6bc26856acf5dd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965968"
---
# <a name="how-to-use-a-visualizer"></a>Procedura: Usare un visualizzatore
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
  
     -oppure-  
  
     `My Documents\Visual Studio 2010\Visualizers` *Visual Studio Version* `\Visualizers`  
  
## <a name="see-also"></a>Vedere anche  
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: Installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Procedura: Scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Visualizzare i valori di dati nei suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)