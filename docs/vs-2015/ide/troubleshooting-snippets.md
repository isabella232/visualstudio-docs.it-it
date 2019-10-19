---
title: Risoluzione dei problemi relativi ai frammenti di codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f73cb7ba59daf2f8ee957d95dee36bba59f87614
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654785"
---
# <a name="troubleshooting-snippets"></a>Risoluzione dei problemi relativi ai frammenti di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In genere, i problemi con i frammenti di codice IntelliSense possono avere due cause: un file di frammento di codice danneggiato o un contenuto non valido in un file.

## <a name="common-problems"></a>Problemi comuni

### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Non è possibile trascinare il frammento di codice da Esplora file in un file di origine di Visual Studio

- Il codice XML nel file di frammento di codice potrebbe essere danneggiato. L'**Editor XML** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può individuare i problemi nella struttura XML.

- Il file di frammento di codice potrebbe non essere conforme allo schema del frammento di codice. L'**Editor XML** in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] può individuare i problemi nella struttura XML.

### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Il codice presenta errori del compilatore che non sono evidenziati

- Potrebbe essere stato omesso un riferimento al progetto. Esaminare la documentazione relativa al frammento di codice. Se il riferimento non viene trovato nel computer, è necessario installarlo. L'inserimento di un frammento di codice dovrebbe aggiungere al progetto tutti i riferimenti necessari. Se il frammento di codice non ha le informazioni di riferimento necessarie, è possibile segnalare l'errore a chi lo ha generato.

- Una variabile potrebbe essere non definita. Le variabili non definite in un frammento di codice dovrebbero essere evidenziate. In caso contrario, è possibile segnalare l'errore a chi ha generato il frammento di codice.

## <a name="see-also"></a>Vedere anche
 [Frammenti di codice](../ide/code-snippets.md)
