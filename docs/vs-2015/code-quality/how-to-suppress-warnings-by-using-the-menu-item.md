---
title: 'Procedura: non visualizzare avvisi tramite la voce di menu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72610020"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Procedura: Eliminare gli avvisi tramite una voce di menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> L'eliminazione dell'origine non è supportata per i progetti di siti Web.

 È possibile utilizzare la finestra analisi codice per disattivare gli avvisi di analisi del codice. L'eliminazione di un avviso non è uguale a quella di disabilitarla. Quando si elimina un avviso, si applica solo a una particolare istanza della violazione. Altre violazioni dello stesso avviso verranno comunque segnalate nella finestra Elenco errori.

 Dopo aver eseguito l'analisi del codice, è possibile determinare che uno o più avvisi di analisi del codice visualizzati nella finestra analisi codice non sono applicabili all'applicazione. Ad esempio, è possibile determinare che il codice è corretto così come è. In alternativa, è possibile che alcune violazioni abbiano priorità bassa e non verranno corrette nel ciclo di sviluppo corrente. Indipendentemente dal motivo, è spesso utile indicare che l'avviso non è applicabile per informare i membri del team che il codice è stato rivisto e che è stato determinato che l'avviso potrebbe essere eliminato. L'eliminazione dell'origine è utile perché consente di inserire un'eliminazione vicino alla posizione in cui viene generato l'avviso.

 È possibile scegliere se l'eliminazione verrà visualizzata nel codice sorgente o nel file di eliminazione globale. Alcune eliminazioni devono essere inserite nel file di eliminazione globale. In tal caso, l'opzione **in source** verrà disabilitata.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>Per non visualizzare un avviso utilizzando la voce di menu

1. Scegliere **finestre** dal menu **analizza** , quindi scegliere **analisi codice**.

2. Nella finestra **analisi codice** selezionare l'avviso non visualizzato.

3. Scegliere azioni, quindi **Elimina messaggi**, quindi scegliere **in origine** o **nel file di eliminazione del progetto**.

     L'avviso specifico viene eliminato e l'avviso viene visualizzato nella finestra analisi codice con una barrata.

> [!NOTE]
> Le eliminazioni che non hanno una destinazione vengono visualizzate nel file di eliminazione globale.
