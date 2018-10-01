---
title: Risoluzione dei problemi relativi ai frammenti di codice | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6cc8cde833d9580e3fae03df2df11e87eed8cf2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531035"
---
# <a name="troubleshooting-snippets"></a>Risoluzione dei problemi relativi ai frammenti di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [risoluzione dei problemi di frammenti di codice](https://docs.microsoft.com/visualstudio/ide/troubleshooting-snippets).  
  
In genere, i problemi con i frammenti di codice IntelliSense possono avere due cause: un file di frammento di codice danneggiato o un contenuto non valido in un file.  
  
## <a name="common-problems"></a>Problemi comuni  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Non è possibile trascinare il frammento di codice da Esplora file in un file di origine di Visual Studio  
  
-   Il codice XML nel file di frammento di codice potrebbe essere danneggiato. L'**Editor XML** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può individuare i problemi nella struttura XML.  
  
-   Il file di frammento di codice potrebbe non essere conforme allo schema del frammento di codice. L'**Editor XML** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può individuare i problemi nella struttura XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Il codice presenta errori del compilatore che non sono evidenziati  
  
-   Potrebbe essere stato omesso un riferimento al progetto. Esaminare la documentazione relativa al frammento di codice. Se il riferimento non viene trovato nel computer, è necessario installarlo. L'inserimento di un frammento di codice dovrebbe aggiungere al progetto tutti i riferimenti necessari. Se il frammento di codice non ha le informazioni di riferimento necessarie, è possibile segnalare l'errore a chi lo ha generato.  
  
-   Una variabile potrebbe essere non definita. Le variabili non definite in un frammento di codice dovrebbero essere evidenziate. In caso contrario, è possibile segnalare l'errore a chi ha generato il frammento di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice](../ide/code-snippets.md)



