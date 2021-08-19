---
title: Risoluzione dei problemi relativi ai frammenti di codice
description: Informazioni su come risolvere i problemi relativi ai frammenti di codice IntelliSense causati in genere da contenuto non valido nel file del frammento di codice o da un file di frammento danneggiato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 37170a41f348a2892055aa39877c8ba74837d34d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055913"
---
# <a name="troubleshoot-snippets"></a>Risoluzione dei problemi relativi ai frammenti di codice

In genere, i problemi con i frammenti di codice IntelliSense possono avere due cause: un file di frammento di codice danneggiato o un contenuto non valido in un file.

## <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Non è possibile trascinare il frammento di codice da Esplora file a un file di origine di Visual Studio

- Il codice XML nel file di frammento di codice potrebbe essere danneggiato. L'**Editor XML** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può individuare i problemi nella struttura XML.

- Il file di frammento di codice potrebbe non essere conforme allo schema del frammento di codice. L'**Editor XML** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può individuare i problemi nella struttura XML.

## <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>Il codice presenta errori del compilatore che non sono evidenziati

- Potrebbe essere stato omesso un riferimento al progetto. Esaminare la documentazione relativa al frammento di codice. Se il riferimento non viene trovato nel computer, è necessario installarlo. L'inserimento di un frammento di codice dovrebbe aggiungere al progetto tutti i riferimenti necessari. Se il frammento di codice non ha le informazioni di riferimento necessarie, è possibile segnalare l'errore a chi lo ha generato.

- Una variabile potrebbe essere non definita. Le variabili non definite in un frammento di codice dovrebbero essere evidenziate. In caso contrario, è possibile segnalare l'errore a chi ha generato il frammento di codice.

## <a name="see-also"></a>Vedi anche

- [Frammenti di codice](../ide/code-snippets.md)
