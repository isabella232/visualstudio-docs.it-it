---
title: Risoluzione dei problemi relativi ai frammenti di codice | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 80e5ba76a54b584e5eed74f507f1fb3b81e7f89e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-snippets"></a>Risoluzione dei problemi relativi ai frammenti di codice
In genere, i problemi con i frammenti di codice IntelliSense possono avere due cause: un file di frammento di codice danneggiato o un contenuto non valido in un file.  
  
## <a name="common-problems"></a>Problemi comuni  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Non è possibile trascinare il frammento di codice da Esplora file in un file di origine di Visual Studio  
  
-   Il codice XML nel file di frammento di codice potrebbe essere danneggiato. L'**Editor XML** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può individuare i problemi nella struttura XML.  
  
-   Il file di frammento di codice potrebbe non essere conforme allo schema del frammento di codice. L'**Editor XML** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può individuare i problemi nella struttura XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Il codice presenta errori del compilatore che non sono evidenziati  
  
-   Potrebbe essere stato omesso un riferimento al progetto. Esaminare la documentazione relativa al frammento di codice. Se il riferimento non viene trovato nel computer, è necessario installarlo. L'inserimento di un frammento di codice dovrebbe aggiungere al progetto tutti i riferimenti necessari. Se il frammento di codice non ha le informazioni di riferimento necessarie, è possibile segnalare l'errore a chi lo ha generato.  
  
-   Una variabile potrebbe essere non definita. Le variabili non definite in un frammento di codice dovrebbero essere evidenziate. In caso contrario, è possibile segnalare l'errore a chi ha generato il frammento di codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Frammenti di codice](../ide/code-snippets.md)