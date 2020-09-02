---
title: 'Procedura: usare un visualizzatore | Microsoft Docs'
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
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778370"
---
# <a name="how-to-use-a-visualizer"></a>Procedura: utilizzare un visualizzatore
È possibile usare un visualizzatore per visualizzare il contenuto di una variabile o di un oggetto in modo significativo per il tipo di dati. È possibile usare i visualizzatori da **suggerimenti**dati, una finestra **espressioni di controllo** , la finestra **auto** o la finestra **variabili locali** .  
  
 I visualizzatori non sono supportati in Compact Framework.  
  
> [!NOTE]
> Nelle app dello **Store** sono supportati solo i visualizzatori di testo, HTML, XML e JSON standard. Non sono supportati i visualizzatori personalizzati (creati dall'utente).  
  
### <a name="to-open-a-visualizer"></a>Per aprire un visualizzatore  
  
1. Fare clic sull'icona della lente di ingrandimento visualizzata accanto a un nome di variabile in **suggerimenti**dati, in una finestra **espressioni di controllo** o nella finestra **auto**, **variabili locali**o **controllo immediato** .  
  
     Verrà visualizzato un elenco di visualizzatori.  
  
2. Fare clic sul visualizzatore da usare.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>Per usare un visualizzatore per il codice gestito durante il debug remoto  
  
- Copiare la DLL del visualizzatore nel computer remoto prima di avviare la sessione di debug.  
  
     Il percorso della DLL deve essere lo stesso sia nel computer remoto che in quello locale. Il percorso può essere uno dei seguenti:  
  
     *Percorso di installazione di Visual Studio* `\Common7\Packages\Debugger\Visualizers`  
  
     -oppure-  
  
     `My Documents\Visual Studio 2010\Visualizers`*Versione di Visual Studio*`\Visualizers`  
  
## <a name="see-also"></a>Vedere anche  
 [Creare visualizzatori personalizzati](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md)   
 [Visualizzare i valori dei dati nei suggerimenti dati](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)